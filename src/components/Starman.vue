<template>
  <div id="starman">
    <div>
      <p>导演</p>
      <ul>
          <li v-if="passData.casts!=null" v-for="item in passData.directors">
            <img :src="item.avatars.medium">
            <p>{{item.name}}</p>
          </li>
      </ul>
      <p>演员</p>
      <ul>
          <li v-if="passData.casts!=null" v-for="item in passData.casts">
            <img :src="item.avatars.medium">
            <p>{{item.name}}</p>
          </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  props:["passData"],
  name: 'Starman',
  mounted(){
    setTimeout(()=>{
      var mySwiper = new Swiper('.swiper-container',{
        slidesPerView : 2.8,
        spaceBetween : 20
     })
    },100)
    
  }
}
</script>

<style>
#starman{
  border-top: 1px solid #dcdcdc;
  margin: 0.2rem;
  padding-top: .1rem;
  padding-bottom: .1rem;
}
#starman>div:nth-child(1)>p{
  font-size: 0.3rem;
  color: #666;
  padding: 0.1rem 0;
}
#starman ul{
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
}
#starman ul li{
  width: 22%;
}
#starman ul li img{
  border: 1px solid #dcdcdc;
  width: 100%;
  /*width: 1.8rem;*/
  /*height: 2.5rem;*/
}
#starman ul li{
  display: flex;
  flex-flow: column;
}
#starman ul li p{
  padding-top: 0.1rem;
  font-size: 0.2rem;
  color: #999;
  text-align: center;
}
</style>
