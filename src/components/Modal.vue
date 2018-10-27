<template>
    <div class="outerWrapper">
        <div class="innerWrapper">
            <div class="photo">

            </div>
            <div class="description">
                <h2 class="title">Lorem Ipsum</h2>
                <p class="description">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae, deserunt? Dicta quia, officia rem nisi quis architecto amet, voluptatem ipsa ratione quibusdam deleniti! Eaque impedit placeat aliquam quisquam sunt cum.
                </p>
            </div>
        </div>
        <div class="close" @click="$emit('closeModal')" />
    </div>
</template>

<script>
export default {
    
}
</script>

<style lang="scss" scoped>
.outerWrapper {
    background: #f6f6f6;
    max-width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
}

.close {
    position: absolute;
    width: 30px;
    height: 30px;
    padding:30px;
    right: 0;
    top: 0;
    cursor: pointer;

    &::before,
    &::after {
        position: absolute;
        top: 30px;
        right: 20px;
        content: '';
        width: 20px;
        height: 2px;
        background: black;
        display: block;
    }

    &::before {
        transform: rotate(45deg);
    }

    &::after {
        transform: rotate(-45deg);
    }
}

.innerWrapper {
    display: flex;
    height: 100%;
    padding: 50px;
    justify-content: center;
    align-items: center;
    flex-direction: column;

    .photo {
        width: 100%;
        height: 50%;
        background: black;

        img {
            width: 100%;
        }
    }

    .description {
        color: #333;
    }
}
</style>

