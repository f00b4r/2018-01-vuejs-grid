<template>
    <div class="colors">
        <template v-for="(picked, color, index) in colors">
            <color class="color"
                   :key="index"
                   :picked="picked"
                   :color="color"
                   @pick="pickColor"
                   @unpick="unpickColor"
            ></color>
        </template>
    </div>
</template>

<script>
    import Color from "./Color.vue";
    import {DEFAULT_COLORS} from "./data/colors";

    export default {
        components: {Color},
        data: () => ({
            colors: DEFAULT_COLORS,
        }),
        methods: {
            pickColor(color) {
                this.$emit('pickColor', color);
            },
            unpickColor(color) {
                this.$emit('unpickColor', color);
            }
        }
    }
</script>
<style>
    .colors {
        display: flex;
        flex-direction: row;
    }

    .colors .color {
        margin: 0 2px;
        width: 30px;
        height: 30px;
        cursor: pointer;
    }
</style>