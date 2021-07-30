<template>
<div>
     <div class="nav">
       <img src="./assets/library.png" width=45px height=45px ><font style="font-family: 'Catamaran', sans-serif; font-weight: 700;margin-top:13px;" color="#FFFFFF">图书馆</font>  
       <font style="margin-top:13px;margin-left:15%" color="#FFFFFF">首页</font> 
       <font style="margin-top:13px;margin-left:25%" color="#FFFFFF">个人中心</font> 
       <font style="margin-top:13px;margin-left:25%" color="#FFFFFF">搜索</font> 
      </div>
<img src="./assets/background.jpg" width=1800px height=300px style="margin-left:-13px;"> 
<div class="announ">
   <img src="./assets/annou.png" width=45px height=45px style="margin-top:13px;"><font  style="font-family: 'Catamaran', sans-serif; font-size:25px;" color="#000000">通知</font> 
    <div id="app">
       <div v-html="message"></div>
    </div>
   <div><span style="font-size:20px;color:blue;">公告1</span><span style="font-family: 'Catamaran', sans-serif; font-size:15px;color:blue;">根据国家。。</span></div>
   <div><span style="font-size:20px;color:blue;">公告2</span><span style="font-family: 'Catamaran', sans-serif; font-size:15px;color:blue;">根据国家。。</span></div>
   <div><span style="font-size:20px;color:blue;">公告3</span><span style="font-family: 'Catamaran', sans-serif; font-size:15px;color:blue;">根据国家。。</span></div>
   <div><span style="font-size:20px;color:blue;">公告4</span><span style="font-family: 'Catamaran', sans-serif; font-size:15px;color:blue;">根据国家。。</span></div>
</div>

    <div class="wrapper">
         <div class="nav-item" :class='{active: index == nowIndex}' v-for='(tabItem,index) in tabParams' @click='tabToggle(index)'>
             <span :class='{dropdownBtn: index == 0}'  @click='dropdown'>{{tabItem}}</span>
             <ul v-if='index == 0' class="dropdownWrapper" v-show='dropdownActive'>
                <li v-for='(item, index) in dropParams'>{{item}}</li>
            </ul>
         </div>
    </div>
    <div>
		<hr />
		<footer class="footer" style="margin-top:3.5%;width:1700px;height:190px;margin-left:-10px;">
		  <div align="center" class="foot1">
			<img src="./assets/logo.png" class="foot1-img">
		  </div>
		  <div align="center" class="foot3">
			<p class="foot3-text1">© 杭州师范大学精思苑2号楼629寝室 All Rights Reserved</p>
			<p class="foot3-text1">浙ICP备1900592号-1</p>
		  </div>
		</footer>
	  </div>
</div>
	
</template>

<script>

    export default {
        data() {
            return {
                nowIndex: 0,
                dropdownActive: false,
                tabParams: ['政治', '娱乐', '体育', '搞笑'],
                dropParams: ['亚洲', '北美洲', '欧洲', '非洲']
            }
            
        },
        methods: {
            dropdown: function(){
                console.log(event.target.getAttribute('class'))
                if(event.target.getAttribute('class') === 'dropdownBtn') {
                    this.dropdownActive = !this.dropdownActive;
                }
            },
            tabToggle: function(index){
                this.nowIndex = index;
                if(index === 0){
                    return
                }else {
                    this.dropdownActive = false;
                }
            }
        },
    }


</script>

<style scoped>
.chara{
    font-size:25px;
}
.announ{
   
}
.nav {
     background-color:#000000;
     display: flex;
     position: fixed;
     top: 0;
     left: 0;
     right: 0;
     height: 49px;
     text-align: center;
   }

    body {
        min-height: 100%;
    }
    .wrapper {
        margin-top:10px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .wrapper>div {
        flex: 1;
        text-align: center;
        height: 36px;
        line-height: 36px;
    }
    .dropdownWrapper {
        /*margin-top: 36px;*/
        border: 1px solid #2C3E50;
        font-size: 14px;
    }
    .dropdownWrapper li {
        display: block;
    }

    .nav-item.active {
        background: #e3e3d3;
    }
    .dropdownBtn {
        display: inline-block;
        width: 100%;
        height: 100%;
    }
    .nav-item {
        cursor: pointer;
    }
.footer{
    background-color: #343A40;
}
.foot1{
    padding-top: 30px;
}
.foot1-img{
    width: 50px;
    height:50px;
}
.foot2{
    padding-top: 20px;
}
.foot2-text1{
    font-size: 14px;
    color:white;
    font-weight:bold;
}
.foot2-text2{
    font-size:10px;
    color:white;
}
.foot3{
    padding-top: 20px;
    padding-bottom: 20px;
}
.foot3-text1{
    font-size: 8px;
    color:white;
}

</style>