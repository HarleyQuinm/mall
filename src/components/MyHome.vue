<template>
    <div class="homemain">
      <div class="count">
        <div class="count-content">
          <div class="iconfont user">&#xe60a;</div>
          <div class="howmany">
            <!-- 请求得到 -->
            <h1>111</h1>
            <p>用户总数</p>
          </div>
        </div>
        <div class="count-content">
          <div class="iconfont product">&#xe60c;</div>
          <div class="howmany">
            <!-- 请求得到 -->
            <h1>211</h1>
            <p>商品总数</p>
          </div>
        </div>
        <div class="count-content">
          <div class="iconfont order">&#xe626;</div>
          <div class="howmany">
            <!-- 请求得到 -->
            <h1>111</h1>
            <p>订单总数</p>
          </div>
        </div>
        <div class="count-content">
          <div class="iconfont looked">&#xe636;</div>
          <div class="howmany">
            <!-- 请求得到 -->
            <h1>111</h1>
            <p>浏览量</p>
          </div>
        </div>
      </div>
      <div class="announce-comment">
        <ul class="announce-comment-title" id="title">
          <li class="annouce active point" >公告</li>
          <li class="comment point">评论</li>
        </ul>
        <div class="announce-comment-content">
            <div class="announce-content active">
                <p class="welcome">管理员，<span id="hello"></span> 现在的时间是：<time></time></p>
                <p>XMALL管理系统和商城前台都是用vue搭建，前后端开发分离。点击此处可前往XMALl的前台商城演示：<a href="">点我前往</a> </p>
                <p>后台几乎完成所有功能开发，你所看到的几乎皆为真实后台数据，为避免数据遭恶意修改，测试体验账号只具备查看权限。 后台主要使用技术有</p>
                <p>1111111111111111111</p>
            </div>
            <div class="comment-content"></div>
        </div>
      </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'MyHome',
  data () {
    return {
      Hello:'',
      loginCity:''
    }
  },
  mounted(){
    // 
    $.getScript('http://int.dpool.sina.com.cn/iplookup/iplookup.php?format=js',function(){
      this.loginCity=remote_ip_info.city
      // $.getScript('http://php.weather.sina.com.cn/iframe/index/w_cl.php?code=js&city=南京&day=0&dfc=3&charset=utf-8',function(res){
      //   console.log(window.SWther.w)
      // })

    })
    var data=new Date()
    var hour=data.getHours()
    if(hour < 6){$("#hello").html("凌晨好！");}
    else if (hour < 9){$("#hello").html("早上好！");}
    else if (hour < 12){$("#hello").html("上午好！");}
    else if (hour < 14){$("#hello").html("中午好！");}
    else if (hour < 17){$("#hello").html("下午好！");}
    else if (hour < 19){$("#hello").html("傍晚好！");}
    else if (hour < 22){$("#hello").html("晚上好！");}
    else {$("#hello").html("深夜好！");}
    setInterval(function(){
        $("time").text(new Date().toLocaleString());
    },1000)
  }
}
</script>
<style>
.homemain{
  height: 100%;
  padding: 110px 0 0 201px;
  background-color: #F1F2F7;
}
.count{
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.count-content{
  width: 22%;
  background-color: white;
  border-radius: 5px;
  overflow: hidden;
}
.count-content>div{
  float: left;
  text-align: center;
  /* line-height: 3rem; */
}
.count-content div.iconfont{
  width: 40%;
  font-size: 50px;
  padding: 20px 0;
  color: white;
}
.count-content div.user{
   background: #6CCAC9;
}
.count-content div.product{
   background: #FF6C60;
}
.count-content div.order{
   background: #F8D347;
}
.count-content div.looked{
   background:#57C8F2;
}
.count-content div.howmany{
  width: 60%;
  height: 94.44px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: #c6cad6;
  
}
.count-content div.howmany h1{
  font-weight: 500;
}
.count-content div.howmany p{
  font-size: 13px;
}
.announce-comment{
  width: 45%;
  background-color: white;
  margin: 25px;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 0 9px rgba(0, 0, 0, .2)
}
.announce-comment-title li{
  float: left;
  width: 50%;
  background: #7087A3 ;
  height: 35px;
  text-align: center;
  line-height: 35px;
}
.announce-comment-title li:hover{
  background-color: white;
}
.announce-comment-title li.active{
  background: white;
}
.announce-comment-content{
  padding: 0 25px 25px 25px;
  font-size: 13px;
  color: #797979;
}
.announce-comment-content .welcome{
  color: #f77b6f
}
.announce-comment-content p{
  margin: 20px 0;
}
</style>



