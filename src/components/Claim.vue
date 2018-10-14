<template>
    <div class="claimWrapper">
        <h1 class="claim">SPACER</h1>
        <p class="subclaim">Begin your journey through our amazing galaxy,
            and discover places you never even heard of.
        </p>
        <p class="subclaim">
            Type anything space-related to start.
        </p>
    </div>
</template>

<script>
export default {
  name: 'Claim',
};
</script>

<style lang="scss">
.claimWrapper {
    display: flex;
    text-align: center;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.claim {
    font-size: 50px;
}

.subclaim {
    margin: 25px 0 0 0;
    font-size: 13px;
}
</style>
