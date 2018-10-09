<template>
    <div class="create">
        <div class="form_container">
            <div class="form">
                <div class="input">
                    <input type="text" v-model="name" placeholder="Bot Name*">
                    <input type="number" v-model="attack" placeholder="Attack Value*">
                    <input type="number" v-model="health" placeholder="Health Value*">
                </div>
                <div class="buttons">
                    <button id="button1" @click="addToBot">Submit</button>
                    <button id="button2" @click="clear">Clear</button>
                </div>  
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            attack: "",
            health: "",
        }
    },
    methods: {
        addToBot() {
            if(!this.name || !this.attack || !this.health) {
                alert("Please enter in all values marked with an '*'")
                return
            }
            this.addBot({
                name: this.name,
                attack: this.attack,
                health: this.health
            })
            this.name = "",
            this.attack = "",
            this.health = ""
        },
        clear() {
            this.name = "",
            this.attack = "",
            this.health = ""
        }
    },
    props: ["addBot"]
}
</script>


<style scoped>
    @import "../reset.css";

    .create {
        height: 90vh;
        background: #5CDB95;
    }

    .form_container {
        display: flex;
        justify-content: center
    }

    .form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-content: center;
        background: #FFFFFF;
        width: 50vw;
        margin-top: 50px;
    }

    .input {
        display: flex;
        flex-direction: column;
        margin: 10px;
    }

    .input input {
        margin: 10px;
        border-radius: 10px;
        padding: 5px;
    }

    .buttons {
        display: flex;
        justify-content: space-around;
        margin-bottom: 10px;
    }

    .buttons button {
        background: transparent;
        width: 110px;
        height: 40px;
        border: none;
        box-shadow: 6px 6px 40px -2px  black;
        font-size: 18px;
    }

    .buttons button:hover {
        cursor: pointer;
        background: #DCDCDC;
    }

    #button1 {
        margin-left: 50px;
    }

    #button2 {
        margin-right: 50px;
    }
</style>