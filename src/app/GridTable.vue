<template>
    <div class="grid">
        <template v-for="gridY in y">
            <div class="grid__row">
                <template v-for="gridX in x">
                    <section class="grid__node">
                        <grid-node ref="node"></grid-node>
                    </section>
                </template>
            </div>
        </template>
    </div>
</template>

<script>
    import GridNode from "./GridNode.vue";

    export default {
        components: {
            'grid-node': GridNode
        },
        data: () => ({
            x: 11,
            y: 13
        }),
        mounted() {
            (this.$refs['node'] || [])
                .forEach((node) => node.changeBg(this.randomColor()));
        },
        methods: {
            refresh() {
                (this.$refs['node'] || [])
                    .forEach((node) => node.changeBg(this.randomColor()));
            },
            randomColor() {
                const colors = [
                    'green',
                    'red',
                    'orange',
                ];

                return colors[Math.floor(Math.random() * colors.length)];
            }
        }
    }
</script>

<style>
    .grid {
        display: flex;
        flex-direction: column;
    }

    .grid .grid__row {
        display: flex;
        flex-direction: row;
    }

    .grid .grid__row .grid__node {
        margin: 1px;
        height: 50px;
        flex: 1 0 auto;
        text-align: center;
    }

    .grid .grid__node {
    }
</style>