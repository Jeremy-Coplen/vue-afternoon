<template>
    <div class="collection">
        <div class="battle_container">
            <p>Bot #1: {{bot1.name}}</p>
            <p>Bot #2: {{bot2.name}}</p>
            <div class="buttons">
                <button @click="battle">Battle</button>
                <button @click="clearBots">Clear</button>
            </div>
        </div>
        <hr>
        <div class="bots_container">
            <bot v-for="(bot, i) in battleBots" :key="i" :bot="bot" :id="i" :selectBot="selectBot" :retireBot="retireBot"></bot>
        </div>
    </div>
</template>

<script>
import Bot from "./Bot"

export default {
    data() {
        return {
            bot1: {name: "Select a bot below"},
            bot2: {name: "Select a bot below"},
            battlingBots: []
        }
    },
    methods: {
        selectBot(id) {
            if(this.bot1.health && this.bot2.health) {
                return
            }
            else if(!this.bot1.health) {
                this.bot1 = this.battleBots[id]
                this.battlingBots.push(this.bot1)
            }
            else if(!this.bot2.health){
                this.bot2 = this.battleBots[id]
                this.battlingBots.push(this.bot2)
            }

        },
        clearBots()  {
            this.bot1 = {name: "Select a bot below"}
            this.bot2 = {name: "Select a bot below"}
            this.battlingBots = []
        },

        battle() {
            let winner = Math.floor(Math.random() * 2)
            alert(`${this.battlingBots[winner].name} Wins!`)
        }
    },
    props: ["battleBots", "retireBot"],
    components: {
        Bot
    }
}
</script>

<style scoped>
    @import "../reset.css";

    .collection {
        background: #5CDB95;
        width: 100vw;
        height: 90vw;
    }

    .battle_container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .bots_container {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-wrap: wrap;
        margin-top: -10px;
    }

    .battle_container p {
        margin-top: 5px;
        margin-bottom: 5px;
        font-size: 25px;
    }

    .buttons {
        margin-top: 25px;
        margin-bottom: 30px;
    }

     .buttons button {
        background: #FFFFFF;
        width: 110px;
        height: 40px;
        border: none;
        box-shadow: 1px 1px 9px -2px black;
        font-size: 18px;
        margin-right: 20px;
        margin-left: 20px;
    }

    .buttons button:hover {
        cursor: pointer;
        background: #DCDCDC;
    }
</style>