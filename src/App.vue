<template>
  <div id="app">
    <label>행군 병력</label>
    <input type="number" v-model="all">
    <br>
    <label>보병</label>
    <input type="number" v-model="Inf" disabled>
    <br>
    <label>라이더</label>
    <input type="number" v-model="Rid" disabled>
    <br>
    <label>헌터</label>
    <input type="number" v-model="Hun" disabled>
    <br>
    <div>493여러분 사랑해요🖤 -SIR 우진-</div>
    <br>
    <div>백투백 랠리 계산용 1번째 랠리기준</div>
    <div>1번째랠리 행군시간</div>
    <input type="number" v-model="M1" style="width:80px">
    <label style="width:40px">분</label>
    <input type="number" v-model="S1" style="width:80px">
    <label style="width:40px">초</label>
    <input type="text" placeholder="랠리장 이름 메모" style="width:200px">
    <div>2번째랠리 행군시간</div>
    <input type="number" v-model="M2" style="width:80px">
    <label style="width:40px">분</label>
    <input type="number" v-model="S2" style="width:80px">
    <label style="width:40px">초</label>
    <input type="text" placeholder="랠리장 이름 메모" style="width:200px">
    <br>
    <label>출발시간 : </label>
    <input type="text" v-model="T2" disabled>
    <div>3번째랠리 행군시간</div>
    <input type="number" v-model="M3" style="width:80px">
    <label style="width:40px">분</label>
    <input type="number" v-model="S3" style="width:80px">
    <label style="width:40px">초</label>
    <input type="text" placeholder="랠리장 이름 메모" style="width:200px">
    <br>
    <label>출발시간 : </label>
    <input type="text" v-model="T3" disabled>
    <div>4번째랠리 행군시간</div>
    <input type="number" v-model="M4" style="width:80px">
    <label style="width:40px">분</label>
    <input type="number" v-model="S4" style="width:80px">
    <label style="width:40px">초</label>
    <input type="text" placeholder="랠리장 이름 메모" style="width:200px">
    <br>
    <label>출발시간 : </label>
    <input type="text" v-model="T4" disabled>
    <br>
    <br>
    <div>고스트랠리 출발시간 계산</div>
    <div>공격자 행군시간</div>
    <input type="number" v-model="BM1" style="width:80px">
    <label style="width:40px">분</label>
    <input type="number" v-model="BS1" style="width:80px">
    <label style="width:40px">초</label>
    <div>고스트 행군시간</div>
    <input type="number" v-model="BM2" style="width:80px">
    <label style="width:40px">분</label>
    <input type="number" v-model="BS2" style="width:80px">
    <label style="width:40px">초</label>
    <br>
    <div>상대방 기준 출발시간</div>
    <input type="text" v-model="BT2" disabled>

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
        M1 : 0,
        M2 : 0,
        M3 : 0,
        M4 : 0,
        S1 : 0,
        S2 : 0,
        S3 : 0,
        S4 : 0,
        T1 : 0,
        T2 : 0,
        T3 : 0,
        T4 : 0,
        BS1 : 0,
        BS2 : 0,
        BM1 : 0,
        BM2 : 0,
        BT1 : 0,
        BT2 : 0,
    }
  },
  watch:{
    'all': {
        handler: function(val, oldVal) {
            if(val != oldVal){
                this.setUnit();
            }
        }
    },
    'M1': {
        handler: function(val, oldVal) {
            if(val != oldVal){
                this.setTime();
            }
        }
    },
    'M2': {
     handler: function(val, oldVal) {
         if(val != oldVal){
             this.setTime();
         }
     }
    },
    'M3': {
    handler: function(val, oldVal) {
       if(val != oldVal){
           this.setTime();
       }
    }
    },
    'M4': {
     handler: function(val, oldVal) {
         if(val != oldVal){
             this.setTime();
         }
     }
    },
     'S1': {
         handler: function(val, oldVal) {
             if(val != oldVal){
                 this.setTime();
             }
         }
     },
     'S2': {
      handler: function(val, oldVal) {
          if(val != oldVal){
              this.setTime();
          }
      }
     },
     'S3': {
     handler: function(val, oldVal) {
        if(val != oldVal){
            this.setTime();
        }
     }
     },
     'S4': {
      handler: function(val, oldVal) {
          if(val != oldVal){
              this.setTime();
          }
      }
      },
     'BS1': {
      handler: function(val, oldVal) {
          if(val != oldVal){
              this.setBackToBack();
          }
        }
      },
     'BS2': {
      handler: function(val, oldVal) {
          if(val != oldVal){
              this.setBackToBack();
          }
        }
      },
     'BM1': {
      handler: function(val, oldVal) {
          if(val != oldVal){
              this.setBackToBack();
          }
        }
      },
     'BM2': {
      handler: function(val, oldVal) {
          if(val != oldVal){
              this.setBackToBack();
          }
      }
     }
  },
  methods:{
    setUnit: function(){
        this.Inf = Math.floor(this.all/100)*62 + this.all%100;
        this.Rid = Math.floor(this.all/100)*9;
        this.Hun = Math.floor(this.all/100)*29;
    },
    setTime: function(){
        this.T1 = parseInt(this.M1*60)+parseInt(this.S1);
        var t2,t3,t4;
        
        if(this.M2 != '')
            t2 = (300-(parseInt(this.T1) - (parseInt(this.M2*60) + parseInt(this.S2))));
        else
            t2 = (300-(parseInt(this.T1) - (parseInt(this.S2))));
        if(parseInt(t2)%60>10)
            this.T2 = Math.floor(parseInt(t2)/60) + ':' + parseInt(t2)%60;
        else
            this.T2 = Math.floor(parseInt(t2)/60) + ':0' + parseInt(t2)%60;
        if(this.M3 != '')
            t3 = (300-(parseInt(this.T1) - (parseInt(this.M3*60) + parseInt(this.S3))));
        else
            t3 = (300-(parseInt(this.T1) - (parseInt(this.S3))));
        
        if(parseInt(t3%60)>10)
            this.T3 = Math.floor(t3/60) + ':' + t3%60;
        else
            this.T3 = Math.floor(t3/60) + ':0' + t3%60;
        
        if(this.M4 != '')
            t4 = (300-(parseInt(this.T1) - (parseInt(this.M4*60) + parseInt(this.S4))));
        else
            t4 = (300-(parseInt(this.T1) - (parseInt(this.S4))));
            
        if(parseInt(t4%60)>10)
            this.T4 = Math.floor(t4/60)+ ':' + t4%60;
        else
            this.T4 = Math.floor(t4/60)+ ':0' + t4%60;
    },
    setBackToBack: function(){
        this.BT1 = parseInt(this.BM1*60)+parseInt(this.BS1);
        var bt = (300 - (parseInt(this.BT1) - (parseInt(this.BM2)*60 + parseInt(this.BS2))));
        if(parseInt(bt)%60>10)
            this.BT2 = Math.floor(parseInt(bt)/60) + ':' + parseInt(bt)%60;
        else
            this.BT2 = Math.floor(parseInt(bt)/60) + ':0' + parseInt(bt)%60;
    },
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
    font-weight:bold;
}

</style>
