<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col 
        :span="3" 
        class="left">
        <img 
          src="//s0.meituan.net/bs/fe-web-meituan/e5eeaef/img/logo.png" 
          alt="美团">
      </el-col>
      <el-col 
        :span="15"
        class="center">
        <div class="wrapper">
          <el-input 
            v-model="search" 
            placeholder="搜索商家或地点"
            @focus="focus"
            @blur="blur"
            @input="input"/>
          <button class="el-button el-button--primary"><i class="el-icon-search"/></button>
          <dl 
            v-if="isHotPlace"
            class="hotPlace">
            <dt>热门搜索</dt>
            <dd 
              v-for="(item,index) in hotPlace" 
              :key="index">{{ item }}</dd>
          </dl>
          <dl
            v-if="isSearchList"
            class="searchList">
            <dd 
              v-for="(item,index) in searchList"
              :key="index">{{ item }}</dd>
          </dl>
        </div>
        <p class="suggset">
          <a href="#">杭州宋城景区</a>
          <a href="#">大渝火锅</a>
          <a href="#">哥老官重庆美蛙鱼头</a>
          <a href="#">莫泰酒店</a>
          <a href="#">速8酒店</a>
          <a href="#">布丁酒店</a>
          <a href="#">慕尚精品酒店</a>
        </p>
        <ul class="nav">
          <li>
            <nuxt-link 
              to="/" 
              class="takeout">美团外卖</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/" 
              class="movie">猫眼电影</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/" 
              class="hotel">美团酒店</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="apartment">民宿/公寓</nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/"
              class="business">商家入驻</nuxt-link>
          </li>
        </ul>
      </el-col>
      <el-col
        :span="6"
        class="right">
        <ul class="security">
          <li><i class="refund"/><p class="txt">随时退</p></li>
          <li><i class="single"/><p class="txt">不满意免单</p></li>
          <li><i class="overdue"/><p class="txt">过期退</p></li>
        </ul>
      </el-col>
    </el-row>
  </div>
</template>
<script>
  export default{
    data(){
      return{
        isFocus:false,
        search:'',
        hotPlace:['杭州宋城景区','大渝火锅','莫泰酒店','哥老官重庆美蛙鱼头','速8酒店','布丁酒店'],
        searchList:['搜索结果1','搜索结果2','搜索结果3','搜索结果4','搜索结果5','搜索结果6']
      }
    },
    computed:{
      isHotPlace:function(){
        return this.isFocus&&!this.search
      },
      isSearchList:function(){
      	return this.isFocus&&this.search
      }
    },
    methods:{
    	focus:function(){
    		this.isFocus=true
    	},
      blur:function(){
        let that=this
        setTimeout(function(){
          that.isFocus=false
        },200)
      },
      input:function(){
        
      }
    }
  }
</script>
<style></style>