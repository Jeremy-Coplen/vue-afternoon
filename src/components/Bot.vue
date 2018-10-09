<template>
    <div class="bot">
        <h3>{{bot.name}}</h3>
        <h3>Attack: {{bot.attack}}</h3>
        <h3>Health: {{bot.health}}</h3>
        <div class="buttons">
            <button @click="selectBot(id)">Select</button>
            <button @click="retireBot(id)">Retire</button>
        </div>
    </div>
</template>

<script>
export default {
    props: ["bot", "id", "selectBot", "retireBot"]
}
</script>

<style scoped>
    @import "../reset.css";

    .bot {
        display: flex;
        flex-direction: column;
        align-items: center;
        background: #ffffff;
        width: 350px;
        margin-top: 50px;
        margin-right: 50px;
        box-shadow: 1px 1px 9px -2px black;
    }

    .bot h3 {
        margin-top: 20px;
        margin-bottom: 10px;
        font-size: 20px;
    }

    .buttons {
        margin-bottom: 20px;
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

    .buttons button + button {
        color: #BB6AC9;
    }
</style>