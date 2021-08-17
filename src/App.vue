<template>
  <div id="app">
    <label>총 병력 수</label>
    <input type="number" v-model="all">
    <br>
    <label>보병</label>
    <input type="number" v-model="Inf">
    <br>
    <label>라이더</label>
    <input type="number" v-model="Rid">
    <br>
    <label>헌터</label>
    <input type="number" v-model="Hun">
    <br>
    <div>493여러분 사랑해요🖤 -SIR 우진-</div>
  </div>
</template>

<script>

export default {
  name: 'App2',
  data () {
    return {
        Inf : 0,
        Rid : 0,
        Hun : 0,
        all : 0,
    }
  },
  watch:{
    'all': {
        handler: function(val, oldVal) {
            if(val != oldVal){
                this.setUnit();
            }
        }
    }
  },
  methods:{
    setUnit: function(){
        this.Inf = Math.floor(this.all*62/100) + this.all%100;
        this.Rid = Math.floor(this.all*9/100);
        this.Hun = Math.floor(this.all*29/100);
    }
  },
}
</script>

<style>
label {
    width:100px;
    font-size: 20px;
    font-weigh: border;
}
input{
    width:200px;
    font-size: 20px;
}
div {
    font-size: 20px;
    font-weigh: border;
}
</style>
