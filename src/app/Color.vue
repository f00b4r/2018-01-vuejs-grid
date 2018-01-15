<template>
    <div :class="{'color--inactive': !enabled}"
         :style="{'background-color': color}"
         @click="pick">
    </div>
</template>

<script>

    export default {
        props: [
            'color',
            'picked',
        ],
        data() {
            return {
                enabled: this.picked
            }
        },
        methods: {
            pick() {
                this.enabled = !this.enabled;

                if (this.enabled) {
                    this.$emit('pick', this.color);
                } else {
                    this.$emit('unpick', this.color);
                }
            }
        }
    }
</script>
<style>
    .color--inactive {
        opacity: 0.1;
    }
</style>