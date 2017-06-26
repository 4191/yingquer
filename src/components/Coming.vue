<template>
<div id="coming">
  <div id="title">
    <h3>即将上映</h3>
    <router-link :to="{name:'More',params:{woxiang:'coming_soon'}}"><h4>更多</h4></router-link>
  </div>
  <ul>
    <li v-for="item in arrcoming">
      <router-link :to="{name:'Details', params:{id:item.id}}"><img :src="item.images.large" :alt="item.alt"></router-link> 
      <p>{{ item.title }}</p>
      <!-- 未上映模块，没有评分 -->
      <p class="smallFont">暂无评分</p>
    </li>
  </ul>
</div>
</template>

<script>
import Vue from 'vue';
import jsonp from 'jsonp';
export default {
  name: 'Coming',
  data(){
    return {
      arrcoming:[]
    }
  }, 
  created(){
    // var url  = "../../static/coming_soon.json"
    // Vue.axios.get(url).then((response) => {
    //   return response.data.subjects;
    // }).then((data)=>{
    //   var arr = Array.prototype.slice.call(data);
    //   var newArr = []
    //   for(var i=0, len=arr.length; i<8; i++){
    //     newArr.push(arr[i]);
    //   }
    //   this.arrcoming = newArr;
    // })

    // jsonp跨域
    var url  = "https://api.douban.com/v2/movie/coming_soon"
    jsonp(url,null,(err,data)=>{
      if(err){
        console.error(err.message);
      }else{
       // 取前8条数据
       for(var i=0; i<8; i++){
         this.arrcoming.push(data.subjects[i])
       }
       // this.arrcoming = data.subjects;
       //console.log(this.obj)   
      }
    })
  }
}


</script>

<style>
#coming{
  padding: 0.2rem;
}
#coming>#title{
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  padding-bottom: 0.1rem;
}
#coming>#title>h3{
  font-size: 0.3rem;
  color: #717071;
}
#coming>#title h4{
  width: .7rem;
  height: .32rem;
  background: rgb(195,13,35);
  font-size: 0.14rem;
  color: white;
  text-align: center;
  line-height: .32rem;
  font-weight: normal;
  border-radius: .12rem; /*慧君说这个好看，不准改*/
}
#coming>ul{
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
}
#coming>ul>li{
  list-style: none;
  width: 25%;
  text-align: center;
  padding-bottom: 0.2rem;
}
#coming>ul>li img{
  width: 1.3rem;
  height: 2rem;
}
#coming>ul>li>p{
  width: 100%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: 0.25rem;
}
#coming>ul>li>p.smallFont{
  width: 100%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: 0.1rem;
  color: gray;
}
</style>
