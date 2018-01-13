<template>
    <div class="node"
         :style="{'background-color': bg}"
    >
    </div>
</template>

<script>
    export default {
        data: () => ({
            bg: null
        }),
        methods: {
            changeBg(bg) {
                this.bg = bg;
            }
        }
    }
</script>

<style>
    .node {
        width: 100%;
        height: 100%;
    }
</style>