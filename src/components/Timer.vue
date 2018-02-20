<template>
  <div>
    <div class="block">
        <p class="digit">{{days}}</p>
        <p class="text">Days</p>
    </div>
    
    <div class="block">
        <p class="digit">{{hours}}</p>
        <p class="text">Hours</p>
    </div>

    <div class="block">
        <p class="digit">{{minutes}}</p>
        <p class="text">Minutes</p>
    </div>

     <div class="block">
        <p class="digit">{{seconds}}</p>
        <p class="text">Seconds</p>
    </div>

  </div>
</template>

<script>
export default {
  props: ['date'],
  name: 'hello',
  data () {
    return {
      msg: `Welcome to Your Vue.js PWA ${this.date}`,
      now: Math.trunc((new Date().getTime() / 1000)),
      dateto: Math.trunc(Date.parse(this.date) / 1000)
    }
  },
  computed: {
    seconds () {
      return (this.dateto - this.now) % 60
    },
    minutes () {
      return Math.trunc((this.dateto - this.now) / 60) % 60
    },
    hours () {
      return Math.trunc((this.dateto - this.now) / 60 / 60) % 24
    },
    days () {
      return Math.trunc((this.dateto - this.now) / 60 / 60 / 24)
    }
  },
  mounted () {
    window.setInterval(() => {
      this.now = Math.trunc((new Date().getTime() / 1000))
    }, 1000)
  },
  filters: {
    'doubleit': function (value) {
      if (value.toString().length <= 1) {
        return '0' + value.toString()
      }
      return value.toString()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
@import url(https://fonts.googleapis.com/css?family=Roboto+Condensed:400|Roboto:100);
.block {
    display: flex;
    flex-direction: column;
    margin: 20px;
}

.text {
    color: #bd1616;
    font-size: 40px;
    font-family: 'Roboto Condensed', serif;
    font-weight: 40;
    margin-top:10px;
    margin-bottom: 10px;
    text-align: center;
}

.digit {
    color: #ecf0f1;
    font-size: 150px;
    font-weight: 100;
    font-family: 'Roboto', serif;
    margin: 10px;
    text-align: center;
}
</style>
