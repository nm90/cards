<template>
    <div id="app">
        <div id="main">
            <h1>Cards!</h1>

            <css-grid :rows="['25%', '50%', '25%']" :columns="['12.5%','12.5%','12.5%','12.5%','12.5%','12.5%','12.5%','12.5%']" class="deck">
                <css-grid-item x="0" y="0" width="8" height="1">
                    <card-group :name="player1.name" :cards="player1.cards" isHand="true"/>
                </css-grid-item>

                <css-grid-item x="1" y="0" width="2" height="14" class="spades suit-group">
                    <card-group name="Spades" :cards="spades" />
                </css-grid-item>

                <css-grid-item x="3" y="0" width="2" height="14" class="clubs suit-group">
                    <card-group name="Clubs" :cards="clubs" />
                </css-grid-item>

                <css-grid-item x="5" y="0" width="2" height="14" class="hearts suit-group">
                    <card-group name="Hearts" :cards="hearts" />
                </css-grid-item>

                <css-grid-item x="7" y="0" width="2" height="14" class="diamonds suit-group">
                    <card-group name="Diamonds" :cards="diamonds" />
                </css-grid-item>

                <css-grid-item x="0" y="0" width="8" height="1">
                    <card-group :name="player2.name" :cards="player2.cards" isHand="true"/>
                </css-grid-item>
            </css-grid>
        </div>
    </div>
</template>

<script>
    import draggable from 'vuedraggable'
    import { CssGrid, CssGridItem } from 'vue-css-grid'
    import CardGroup from "./components/CardGroup"
    import Vue from 'vue'

    Vue.component('css-grid', CssGrid);

    export default {
        name: 'app',
        components: {
            CardGroup,
            draggable,
            CssGrid,
            CssGridItem
        },
        data: function () {
            return {
                spades: [
                    {name: "1S", id: 1, style: 'background-color: blue; color: red'},
                    {name: "2S", id: 2, style: 'background-color: blue; color: red'},
                    {name: "3S", id: 3, style: 'background-color: blue; color: red'},
                    {name: "4S", id: 4, style: 'background-color: blue; color: red'},
                    {name: "5S", id: 5, style: 'background-color: blue; color: red'},
                    {name: "6S", id: 6, style: 'background-color: blue; color: red'},
                    {name: "7S", id: 7, style: 'background-color: blue; color: red'},
                    {name: "8S", id: 8, style: 'background-color: blue; color: red'},
                    {name: "9S", id: 9, style: 'background-color: blue; color: red'},
                    {name: "TS", id: 10, style: 'background-color: blue; color: red'},
                    {name: "JS", id: 11, style: 'background-color: blue; color: red'},
                    {name: "QS", id: 12, style: 'background-color: blue; color: red'},
                    {name: "KS", id: 13, style: 'background-color: blue; color: red'}
                    ],
                clubs: [
                    {name: "1C", id: 14, style: 'background-color: green; color: black'},
                    {name: "2C", id: 15, style: 'background-color: green; color: black'},
                    {name: "3C", id: 16, style: 'background-color: green; color: black'},
                    {name: "4C", id: 17, style: 'background-color: green; color: black'},
                    {name: "5C", id: 18, style: 'background-color: green; color: black'},
                    {name: "6C", id: 19, style: 'background-color: green; color: black'},
                    {name: "7C", id: 20, style: 'background-color: green; color: black'},
                    {name: "8C", id: 21, style: 'background-color: green; color: black'},
                    {name: "9C", id: 22, style: 'background-color: green; color: black'},
                    {name: "TC", id: 23, style: 'background-color: green; color: black'},
                    {name: "JC", id: 24, style: 'background-color: green; color: black'},
                    {name: "QC", id: 25, style: 'background-color: green; color: black'},
                    {name: "KC", id: 26, style: 'background-color: green; color: black'}
                ],
                hearts: [
                    {name: "1H", id: 27, style: 'background-color: yellow; color: purple'},
                    {name: "2H", id: 28, style: 'background-color: yellow; color: purple'},
                    {name: "3H", id: 29, style: 'background-color: yellow; color: purple'},
                    {name: "4H", id: 30, style: 'background-color: yellow; color: purple'},
                    {name: "5H", id: 31, style: 'background-color: yellow; color: purple'},
                    {name: "6H", id: 32, style: 'background-color: yellow; color: purple'},
                    {name: "7H", id: 33, style: 'background-color: yellow; color: purple'},
                    {name: "8H", id: 34, style: 'background-color: yellow; color: purple'},
                    {name: "9H", id: 35, style: 'background-color: yellow; color: purple'},
                    {name: "TH", id: 36, style: 'background-color: yellow; color: purple'},
                    {name: "JH", id: 37, style: 'background-color: yellow; color: purple'},
                    {name: "QH", id: 38, style: 'background-color: yellow; color: purple'},
                    {name: "KH", id: 39, style: 'background-color: yellow; color: purple'}
                ],
                diamonds: [
                    {name: "1D", id: 40},
                    {name: "2D", id: 41},
                    {name: "3D", id: 42},
                    {name: "4D", id: 43},
                    {name: "5D", id: 44},
                    {name: "6D", id: 45},
                    {name: "7D", id: 46},
                    {name: "8D", id: 47},
                    {name: "9D", id: 48},
                    {name: "TD", id: 49},
                    {name: "JD", id: 50},
                    {name: "QD", id: 51},
                    {name: "KD", id: 52}
                ],
                player1: {
                    name: "Player1",
                    cards: [
                        {name: "", id: 0}
                    ]
                },
                player2: {
                    name: "Player2",
                    cards: [
                        {name: "", id: 999}
                    ]
                }
            }
        },
        methods: {
            add: function () {
                this.list.push({name: 'Juan'});
            },
            replace: function () {
                this.list = [{name: 'Edgard'}]
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .deck .suit-group {
        /*float: left;*/
        /*width: 25%;*/
    }
</style>
