<template>
    <div id="main" class="container">
        <div class="card text-white bg-dark">
            <div class="card-header">
                <h1 class="float-left">Grid Generator v1.0</h1>
                <button @click.prevent="onRefresh" class="btn btn-success float-right">Refresh grid</button>
            </div>
            <div class="card-body">
                <colors @pickColor="pickColor" @unpickColor="unpickColor"></colors>
            </div>
        </div>
        <grid-table ref="grid" :colors="generateColors()"></grid-table>
    </div>
</template>

<script>
    import GridTable from "./GridTable.vue";
    import Colors from "./Colors.vue";
    import {DEFAULT_COLORS} from "./data/colors";

    export default {
        components: {
            Colors,
            GridTable
        },
        data: () => ({
            colors: [],
        }),
        created() {
            this.colors = Object.keys(DEFAULT_COLORS);
        },
        methods: {
            onRefresh() {
                this.$refs.grid.refresh();
            },
            pickColor(color) {
                this.colors.push(color);
            },
            unpickColor(color) {
                const index = this.colors.indexOf(color);
                if (index !== -1) {
                    this.$delete(this.colors, index);
                }
            },
            generateColors() {
                return [...this.colors];
            }
        }
    }
</script>

<style>
    #main {
        margin-top: 20px;
    }
</style>