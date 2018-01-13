<template>
    <div id="main" class="container">
        <div class="card text-white bg-dark">
            <div class="card-header">
                <h1>Grid Generator v1.0</h1>
            </div>
            <div class="card-body">
                <button @click.prevent="onRefresh" class="btn btn-success">Refresh grid</button>
            </div>
        </div>
        <grid-table ref="grid"></grid-table>
    </div>
</template>

<script>
    import GridTable from "./GridTable.vue";

    export default {
        components: {
            'grid-table': GridTable
        },
        methods: {
            onRefresh() {
                this.$refs.grid.refresh();
            }
        }
    }
</script>

<style>
    #main {
        margin-top: 20px;
    }
</style>