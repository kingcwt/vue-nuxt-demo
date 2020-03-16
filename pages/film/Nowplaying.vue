<template>
  <div>
    nowplaying
    <ul>
      <li v-for="data in datalist" :key="data.filmId" @click="handlepush(data.filmId)">
        <!--                {{data}}-->
        <div class="imgbox"><img :src="data.poster | myfilter" alt=""></div>
        <div class="libox">
          <h3>{{data.name}}</h3>
          <p><span class="wish">{{data.category}}</span><span></span></p>
          <p>{{data.synopsis}}</p>
        </div>
      </li>    </ul>
  </div>
</template>

<script>
  import axios from 'axios';
  import Vue from 'vue';
  Vue.filter('myfilter',function (item) {
    return item.replace('w.h','80.100')
  });
    export default {
        name: "Nowplaying",
        data:function () {
          return {
            datalist:[111,222,333]
          }
        },
      asyncData(){
          return axios({
            url:'https://m.maizuo.com/gateway?cityId=440300&pageNum=1&pageSize=10&type=2&k=7239881',
            headers:{
              'X-Client-Info': '{"a":"3000","ch":"1002","v":"5.0.4","e":"1584086486721554505773","bc":"110100"}',
              'X-Host': 'mall.film-ticket.film.list'
            }
          }).then(res=>{
            return{
              datalist:res.data.data.films
            }
          })
      },
      methods:{
        handlepush(id){
          this.$router.push(`/detail/${id}`)
        }
      }
    }
</script>

<style scoped>

</style>
