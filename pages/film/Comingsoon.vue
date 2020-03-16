<template>
  <div>
<!--    {{datalist}}-->

    <ul>
      <li v-for="data in datalist">{{data.nm}}</li>
    </ul>
  </div>
</template>

<script>
    import axios from "axios";

    export default {
        name: "Comingsoon",
      data:function(){

          return{
            datalist:[]
          }
      },
      asyncData(){
        return axios({
          url:process.server?'http://m.maoyan.com/ajax/mostExpected?ci=1&limit=10&offset=0&token=&optimus_uuid=3C0142D0642311EA96885F6C8BEFB3CE8EC54C4D01444061BDDCD16CF292089C&optimus_risk_level=71&optimus_code=10':'/ajax/mostExpected?ci=1&limit=10&offset=0&token=&optimus_uuid=3C0142D0642311EA96885F6C8BEFB3CE8EC54C4D01444061BDDCD16CF292089C&optimus_risk_level=71&optimus_code=10',
        }).then(res=>{
          console.log(res,'222');
          // return{
          // }
          return {datalist:res.data.coming}
        })
      },
    }
</script>

<style scoped>

</style>
