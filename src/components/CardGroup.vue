<template>
    <div class="card-group">
        <h2>{{name}}</h2>
        <draggable v-model="cards" :options="{group:'hand', draggable:'.dragArea'}" @start="drag=true" @end="drag=false"
                   element="css-grid" :component-data="getComponentData()">
            <css-grid-item
                class="dragArea" v-bind:style="element.style" v-for="element in cards" :key="element.id">
                    {{element.name}}
            </css-grid-item>
        </draggable>
    </div>
</template>
<script>
    import Draggable from 'vuedraggable'
    import { CssGrid, CssGridItem } from 'vue-css-grid'
    import Vue from 'vue'

    Vue.component('css-grid', CssGrid);

    export default {
        name: 'card-group',
        components: { Draggable, CssGrid, CssGridItem },
        props: ['name', 'cards', 'isHand'],
        methods: {
            getComponentData() {
                if (this.isHand) {
                    return {
                        props: {
                            columns: ['12.5%','12.5%','12.5%','12.5%','12.5%','12.5%','12.5%','12.5%'],
                            rows: ['25%', '25%', '25%', '25%']
                        }
                    }
                }
                return {
                    props: {
                        columns: ['25%', '25%', '25%', '25%'],
                        rows: ['25%', '25%', '25%', '25%']
                    }
                }
            }
        }
    }
</script>

<style>
    .dragArea {
        /*margin: 20px;*/
        background-color: aqua;
        border-width: thin;
        border-style: dashed;
        border-color: black;
        /*height: 50px*/
    }
</style>
