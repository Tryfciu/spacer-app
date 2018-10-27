<template>
  <div :class="[{ flexStart: step === 1}, 'wrapper']">
    <transition name="slide">
      <img src="./assets/logo.svg" class="logo" v-if="step === 1">
    </transition>
    <transition name="fade">
      <HeroImage v-if="step === 0"/>
    </transition>
    <Claim  v-if="step === 0"/>
    <search-input
      v-model="searchValue"
      @input="handleInput"
      :dark="step === 1"
    />
    <div class="results" v-if="results && !loading && step === 1">
      <Item v-for="item in results" :key="item.data[0].nasa_id" :item="item" :title="item.title"/>
    </div>
    <Modal />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import HeroImage from '@/components/HeroImage.vue';
import Item from '@/components/Item.vue';
import Modal from '@/components/Modal.vue';

const API = 'https://images-api.nasa.gov/search';

export default {
  name: 'App',
  components: {
    Claim,
    SearchInput,
    HeroImage,
    Item,
    Modal,
  },
  data() {
    return {
      searchValue: '',
      results: [],
      loading: false,
      step: 0,
    };
  },
  methods: {
    handleInput: debounce(function () {
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          this.step = 1;
          this.loading = false;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800');

* {
  box-sizing: border-box;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .6s ease;
}

.fade-anter, .fade-leave-to {
  opacity: 0;
}

.slide-enter-active, .slide-leave-active {
  transition: margin-top .6s ease;
}

.slide-enter, .slide-leave-to {
  margin-top: -50px;
}

.wrapper {
  margin: 0;
  position: relative;
  width: 100%;
  height: 100vh;
  min-height: 100vh;
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &.flexStart {
    justify-content: flex-start;
  }
}

.logo {
  position: absolute;
  top: 30px;
}

.results {
  margin-top: 50px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 20px;

  @media (min-width: 768px) {
    grid-template-columns: 1fr 1fr 1fr;
  }

}

</style>
