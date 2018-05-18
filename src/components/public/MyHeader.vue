<template>
    <div class="main">
        <header class="header-container">
            <p class="system-name point">
                XMall后台管理系统 v1.0
            </p>
            <ul class="nav-list">
                <li class="point add " :class="navWhich==1?'active':''" @mouseenter="isAdd=true;navWhich=1" @mouseleave="isAdd=false;navWhich=0">
                    <i class="fa fa-plus "></i>&nbsp;
                    <p>新增</p>&nbsp;
                    <i class="el-icon-arrow-down"></i>
                    <ul class="add-menu" v-show="isAdd">
                        <li :class="addWhich==1?'active':''" @mouseenter="addWhich=1" @mouseleave="addWhich=0">
                            <i class="el-icon-goods"></i>
                            <p>商品</p>
                        </li>
                        <li :class="addWhich==2?'active':''" @mouseenter="addWhich=2" @mouseleave="addWhich=0">
                            <i class="fa fa-user-o"></i>
                            <p>用户</p>
                        </li>
                    </ul>
                </li>
                <li class="point active">
                    <p>平台</p>
                </li>
                <li class="point"  :class="navWhich==2?'active':''"  @mouseenter="navWhich=2" @mouseleave="navWhich=0">
                    <p>商城前往</p>
                </li>
            </ul>
            <ul class="drop-list">
                <li>
                    <p></p>
                </li>
                <li class="point" :class="navWhich==3?'active':''" @mouseenter="isuser=true;navWhich=3" @mouseleave="isuser=false;navWhich=0">
                    <span>
                        test
                    </span>
                    <i class="el-icon-arrow-down"></i>
                    <ul class="user-menu"  v-show="isuser">
                        <li class="point" :class="addWhich==1?'active':''" @mouseenter="addWhich=1" @mouseleave="addWhich=0">个人信息</li>
                        <li class="point" :class="addWhich==2?'active':''" @mouseenter="addWhich=2" @mouseleave="addWhich=0">切换账户</li>
                        <li class="point" :class="addWhich==3?'active':''" @mouseenter="addWhich=3" @mouseleave="addWhich=0">退出</li>
                    </ul>
                </li>
                <li class="point" :class="navWhich==4?'active':''" @mouseenter="navWhich=4" @mouseleave="navWhich=0">
                     <i class="icon iconfont">&#xe82b;</i>
                </li>
                <li class="point" :class="navWhich==5?'active':''" @mouseenter="navWhich=5" @mouseleave="navWhich=0">
                    <i class="fa fa-envelope-o"></i>
                </li>
                <li class="point" :class="navWhich==6?'active':''" @mouseenter="navWhich=6" @mouseleave="navWhich=0">
                    <i class="icon iconfont">&#xe91e;</i>
                </li>
            </ul>
        </header>
        <aside class="side-list">
            <ul class="side-menu">
                <li v-for="item in sideList" class="point" :key="item.id" @click="sideMenuClick(item.id,item.child.length)">
                    <p class="list-title">
                        <i class="iconfont" v-html="item.icon" style=" color:#a0a7b1;"></i>
                        <span>{{item.name}}</span>
                        <i class="el-icon-arrow-down"></i>
                    </p>
                    <ul class="menu-list">
                        <li v-for="childitem in item.child" :key="childitem" class="point">
                            <p> {{childitem}} </p>
                        </li>
                    </ul>
                </li>
                <span class="stretch point" @click="stretchHandle()">
                <i class="iconfont" style="color: #a0a7b1;">&#xe717;</i>
                </span>
            </ul>
            
        </aside>
        <div class="innerHeader">
            <ul  class="innerHeader-list">
                <li class="little-title point" :class="item.isActive?'active':''" v-for="item in pagetitle" :key="item.id">
                    <span>{{item.title}}</span>
                    <i class="iconfont" v-if="item.title!='我的首页'">&#xe6e9;</i>
                </li>
            </ul>
        </div>
    </div>
    
</template>

<script>
export default {
  name:'MyHeader',
  data(){
      return {
          isAdd:false,
          isuser:false,
          addWhich:0,
          navWhich:0,
          sideList:[
              {id:0,name:'商城管理',child:['首页板块管理','首页轮播图管理','首页板块内容管理','其他版块内容管理'],icon:'&#xe6ef;'},
              {id:1,name:'商品管理',child:['分类管理','商品管理'],icon:'&#xe764;'},
              {id:2,name:'订单管理',child:['订单列表'],icon:'&#xe6de;'},
              {id:3,name:'管理员管理',child:['角色管理','权限管理','管理员列表'],icon:'&#xe716;'},
              {id:4,name:'会员管理',child:['会员列表','删除的会员'],icon:'&#xe715;'},
              {id:5,name:'统计报表',child:[],icon:'&#xe60e;'},
              {id:6,name:'系统管理',child:['权限配置','基本配置','系统日志'],icon:'&#xe728;'}
              
          ],
          pagetitle:[
              {id:0, title:'我的首页',isActive:true},
          ],
          stretchCount:0
      }
  },
  methods:{
    sideMenuClick(index,num){
        var list=$('.side-menu>li:eq('+index+') .menu-list')
        console.log(list.height())
        if(list.height()!=0){
            list.css('height','0')
            $('.side-menu>li:eq('+index+') .el-icon-arrow-down').css('transform',' rotate(0)')
        }else {
            list.css('height',(30*num+3)+'px')
             $('.side-menu>li:eq('+index+') .el-icon-arrow-down').css('transform',' rotate(180deg)')
        }    
    },
    stretchHandle(){
        console.log('11111')
        this.stretchCount++;
        if(this.stretchCount%2!=0){
            $('.side-menu').css('left','-201px');
            $('.stretch .iconfont ').css('transform','rotate(0)')
            $('.innerHeader').css('left','0')

        }else {
            $('.side-menu').css('left','0');
            $('.stretch .iconfont ').css('transform','rotate(180deg)');
            $('.innerHeader').css('left','201px')
            }
        
    }
  }
}
</script>
<style scoped>
 .header-container{
     background-color: #2D6DCC;
     width: 100%;
     color: white;
     font-size: 14px;
     height: 44px;
     position: fixed;
     left: 0;
     top: 0
 }
 .system-name{
     font-size: 16px;
     margin: 0 20px;
     line-height: 44px;
 }
 .nav-list{
     margin: 0;
     line-height: 44px;
     padding: 0 5px;
  }
  .nav-list li{
      padding: 0 20px;
      text-align: center;
      position: relative;
      transition: all .2s
  }
  .nav-list li.active,.drop-list li.active{
      background: rgba(255, 255, 255, .2)
      
  }
 .nav-list,.nav-list>li,.system-name,.drop-list>li{
     float: left;
 }
 .nav-list li p{
     display: inline-block;
 }
 .add-menu{
     color: black;
     position: absolute;
     width: 100%;
     top: 44px;
     left: 0;
     box-shadow: 0 0 4px rgba(0, 0, 0, .2);
     background-color: white;
     z-index: 99;
 }
 .add-menu li{
     text-align: center;
     padding: 0;
     margin: 0;
 }
  .add-menu li:nth-of-type(1){
      border-bottom: 1px solid #f2f2f2;
  }
  .add-menu li.active,.user-menu li.active{
      color: blue;
      background-color: #fafafa;
  }
  .drop-list{
      float:right;
  }
  .drop-list>li{
      padding:0 15px;
      line-height:44px;
      vertical-align: middle;
      position: relative;
  }
  .drop-list>li:nth-of-type(n+3) i{
      font-size:17px;
  }
  .drop-list>li i{   
      display: inline-block;
      line-height: 44px;
  }
  .user-menu{
      color: black;
      box-shadow: 0 0 4px rgba(0, 0, 0, .2);
      width: 100px;
      position: absolute;
      left: 0;
      text-align: center;
      z-index: 99;
      background: white;
  }
  .user-menu li:nth-of-type(-n+2){
      border-bottom: 1px solid #f2f2f2;
  }
  .side-list {
      width: 200px;
      /* height: 2000px; */
      transition: all .3s
  }
  .side-menu{
      position: fixed;
      top: 44px;
      left: 0;
      bottom: 0;
      width: 200px;
      color: #333;
      border-right:1px solid #e5e5e5; 
      transition: all .3s;
      font-size: 14px;
      height: 100%;
      padding-top: 10px;
      background: rgba(238,238,238,0.98)
  }
  .side-menu>li .list-title{
      height: 35px;
      line-height: 35px;
      border-bottom: 1px solid #e5e5e5;
      padding: 0 10px;
  }
   .side-menu>li .list-title:hover{
       color: #5A98DE;
   }

  .side-menu i.el-icon-arrow-down{
      float: right;
      line-height: 35px;   
      transition: all .3s
  }
  .menu-list{
      overflow: hidden;
      height: 0;
      transition: all .3s linear;
  }
  .menu-list li:hover{
      background-color: white;
      color: #5A98DE;
  }
  .menu-list p{
   padding-left: 35px;
   line-height: 30px;
  }
  .stretch{
    position: absolute;
    left: 201px;
    top: 45%;
    height:50px;  
    width:0;  
    border-left:20px solid rgba(238,238,238,0.98); 
    border-top:20px solid transparent;  
    border-bottom:20px solid transparent;
    z-index: 999999;
  }
  .stretch:hover{
      border-left:20px solid #2D6DCC;
  }
 .stretch i{
     position: absolute;
    left: -20px;
 }
  .stretch:hover i{
      
      color: white !important;
  }
  .stretch .iconfont{
      display: inline-block;
      transform: rotate(180deg);
      margin-top: 15px;
  }
.innerHeader{
    position: fixed;
    left:201px;
    top: 44px;
    background-color: #efeef0;
    width: 100%;
    height: 35px;
    border-bottom: 1px solid #e5e5e5;
    overflow: hidden;
    transition: all .3s
}
.innerHeader .little-title p{
    text-align: center;
    width: 138px;
}
.innerHeader-list li{
    margin-top: 10px;
    line-height: 26px;
    display: inline-block;
    background-color: #CBCACC;
    border-top: 1px solid rgba(180, 177, 177, 0.904);
    position: relative;
    margin-left: 19px;
    padding: 0 20px;
}
.innerHeader-list li.active,.innerHeader-list li.active::before,.innerHeader-list li.active::after{
    background-color:#EDEDEE 
}
.innerHeader .innerHeader-list li.active::before,.innerHeader-list li.active::after{
    z-index:-9;
}
.innerHeader-list li:before{
    position: absolute;
    left: -14px;
    top:7px;
    content: '';
    height: 36.7px;
    width:36.7px;
    background-color: #CBCACC;
    transform: rotate(35deg);
    border-left: 1px solid rgba(180, 177, 177, 0.904);
    z-index: -99;
}
.innerHeader-list li:after{
    position: absolute;
    right: -14px;
    top:7px;
    content: '';
    height: 36.7px;
    width:36.7px;
    background-color: #CBCACC;
    transform: rotate(-35deg);
    border-right: 1px solid rgba(180, 177, 177, 0.904);
    z-index: -99;
}
.innerHeader .innerHeader-list li.active{
    background-color:#EDEDEE;
}
.innerHeader-list li span{
    display: inline-block;
    line-height: 27px;
}
.innerHeader-list li i.iconfont{
    position: absolute;
    right:-1px;
    top: 1px;
}
</style>


