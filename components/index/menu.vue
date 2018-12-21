<template>
  <div class="m-menu">
    <dl 
      class="nav" 
      @mouseleave="mouseleave">
      <dt>全部分类</dt>
      <dd 
        v-for="(item,index) in menu"
        :key="index"
        @mouseenter="mouseenter">
        <i :class="item.type"/>{{ item.name }}<span class="arrow"/>
      </dd>
    </dl>
    <div 
      v-if="kind"
      class="detail" 
      @mouseenter="sover"
      @mouseleave="sout">
      <template v-for="(item,index) in curdetail.child">
        <h4 :key="index">{{ item.title }}</h4>
        <span 
          v-for="(item1,index) in item.child"
          :key="index">{{ item1 }}</span>
      </template>
    </div>
  </div>
</template>
<script>
  export default{
    data(){
      return{
        kind:'',
        menu:[{
          type:'food',
          name:'美食',
          child:[{
            title:'美食',
            child:['代金券','火锅','自助餐','甜点饮品']
          },{
            title:'美食',
            child:['代金券','火锅','自助餐','甜点饮品']
          }]
        },{
          type:'takeout',
          name:'外卖',
          child:[{
          	title:'外卖',
          	child:['美团外卖']
          }]
        },{
          type:'hotel',
          name:'酒店',
          child:[{
          	title:'酒店星级',
          	child:['经济型','舒适三星','高档','豪华']
          }]
        }]
      }
    },
    computed:{
      curdetail:function(){
        return this.menu.filter((item)=>item.type===this.kind)[0];
      }
    },
    methods:{
      mouseleave:function(){
        let that=this;
        that._timer=setTimeout(function(){
          that.kind="";
        },150)
      },
      mouseenter:function(e){
        this.kind=e.target.querySelector('i').className
      },
      sover:function(){
        clearTimeout(this._timer)
      },
      sout:function(){
        this.kind="";
      }
    }
  }
</script>
<style></style>