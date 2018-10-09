<template>
  <div>
    <div class="header">
      <div class="link" @click="createToTrue">
        <h1 class="header_item">Create</h1>
      </div>
      <div>
        <h1 class="header_title">Battle Bots</h1>
      </div>
      <div class="link" @click="createToFalse">
        <h1 class="header_item">Collection</h1>
      </div>
    </div>
    <section v-if="createView">
      <create :addBot="addBot"></create>
    </section>
    <section v-else>
      <collection :battleBots="battleBots" :retireBot="retireBot"></collection>
    </section>
  </div>
</template>

<script>
import Create from "./components/Create"
import Collection from "./components/Collection"

export default {
  data() {
    return {
      createView: true,
      battleBots: [
        {name: "George", attack: 50, health: 100},
        {name: "Jeff", attack: 10, health: 60},
        {name: "Megan", attack: 70, health: 50}
      ]
    };
  },
  methods: {
    createToTrue() {
      this.createView = true;
    },
    createToFalse() {
      this.createView = false;
    },
    addBot(bot) {
      this.battleBots.push(bot)
      this.createToFalse()
    },
    retireBot(id) {
      this.battleBots.splice(id, 1)
    }
  },
  components: {
    Create,
    Collection
  }
};
</script>

<style scoped>
  @import "./reset.css";
  .header {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    width: 100vw;
    height: 10vh;
    background: #05386B;
    color: #FFFFFF;
  }

  .header_title {
    font-size: 30px;
    margin-top: 10px;
  }

  .header_item {
    font-size: 25px;
    padding: 10px;
  }

  .header_item:hover {
    cursor: pointer;
    background: #224F7C;
  }
</style>
