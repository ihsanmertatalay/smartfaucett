<template>

    <div class="container">
        
Desired Flow
<div class="form-control">
          <label for="name">Temparature</label>
                    <br>
          <input style="margin: auto;"  type="number" id="name" name="name" v-model="temp" required=true/>
        </div>
         <div class="form-control">
          <label for="name">Flow Rate</label>
          <br>
          <input type="number" id="distance" distance="name" v-model="rate" required=true/>
        </div>
<p style="text-transform: capitalize;">random values of the present water degree
</p>
<p style="color: red;">     Hot side degree =    {{hotm}} C        
</p>
<p style="color:blue;"> Cold side degree =  {{coldm}} C</p>
<br>

  <button @click="hesapla" style="background:purple; color:yellow; padding:10px;">Open The Faucet</button>
  <div v-if="temp > hotm">
      <h1>    Too hot to ensure
    </h1>
  </div>
  <div v-else-if="temp < coldm ">
      <h1>    Too cold to ensure
    </h1>
  </div>
 
  <div v-else>
    <p style="color: red;">
        hot side opened amount of {{hot.toFixed(2)}}
    </p>
    <p style="color: blue;">
        cold side opened amount of {{cold.toFixed(2)}}
    </p>  </div>
    </div>

</template>

<script>

export default {

    data() {
        return {
            temp: 0,
            rate : 0,
            hot:0,
            cold: 0,
            hotm: Math.random().toFixed(2)*30+40,
            coldm: Math.random().toFixed(2)*15+5,
        }
    },
    methods: {
        hesapla(){
            this.hot = (this.temp-this.coldm)/(this.hotm-this.coldm)*this.rate;
            this.cold = (this.hotm-this.temp)/(this.hotm-this.coldm)*this.rate;

        }
    },
}
</script> 
<style>

    .container{
        margin: auto;
        width: 40%;
        text-align: center;
    }
    button:hover{
        filter: brightness(125%);

    }
</style>