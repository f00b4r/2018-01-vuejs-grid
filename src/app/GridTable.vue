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
        props: {
            colors: {
                type: Array
            },
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
                return this.colors[Math.floor(Math.random() * this.colors.length)];
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
        justify-content: space-around;
    }

    .grid .grid__row .grid__node {
        flex: 1 0 auto;
        height: auto;
        margin: 2px;
        text-align: center;
    }

    .grid .grid__row .grid__node:before {
        content: '';
        float: left;
        padding-top: 100%;
    }

    .grid .grid__node {
    }
</style>