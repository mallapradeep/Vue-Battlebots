<template>
  <div>

    <div class='navbar'>
    <div class='container'>

     <button @click='switchView(true)'>CREATE</button>
     <p>BATTLE BOT</p>
     <button @click='switchView(false)'>COLLECTION</button>
    </div>
    </div>

  <!-- creating bots -->
    <section v-if='showForm'>
      <div className='box'>
      <input v-model='botName' type="text" placeholder='Bot Name'><br>
      <input v-model='attackValue' type="text" placeholder='Attack Value'><br>
      <input v-model='healthValue' type="text" placeholder='Health Value'><br>
      <button @click='addBot'>SUBMIT</button>
      <button @click='clearPost'>CLEAR</button>
      </div>
    </section>

<!-- collection of bots -->
  <section v-else>
      <h3>Bot #1: Select a bot below</h3>
      <h3>Bot #2: Select a bot below</h3>
          <Bot v-for='(Bot, i) in allBots'
              :key='i' 
              :postObject='Bot'
          />
      <button>BATTLE</button>
      <button>CLEAR</button><hr>



  </section>
  </div>
</template>



<script>
import Bot from './components/Bot';

export default {
  data() {
    return {
   showForm: true,
        botName: '',
        attackValue: '',
        healthValue: '',
        bot1: '',
        bot2: '' ,
        allBots: []
    };
  },
  methods: {
    switchView(val) {
      this.showForm = val
    },

    addBot() {
      this.allBots.push({
        botName: this.botName,
        attackValue: this.attackValue,
        healthValue: this.healthValue,
      })
      this.botName = '';
      this.attackValue = '';
      this.healthValue = '';
      this.switchView(false);
    },

    clearPost() {
        this.botName = '';
        this.attackValue = '';
        this.healthValue = '';
            }  
    },
  components: {
    Bot: Bot
  }
}
</script>


<style lang='css'>
    p {
      background-color: blue;
      font-size: 40px;
    
    }

    .navbar {
      width: 100%;
      height: 20vh;
     
    }

   .container {
     width: 100vw;
     height: 40px;
     display: flex;
     justify-content: space-between;
   }

   .box {
     margin-left: 150px;
   }


</style>
