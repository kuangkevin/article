##使用纯css代码实现魔方##
>html代码就是六个ul代表六个面，每个面的每个小方块代表每个格子
>
    <div class="content">
      <ul class="top">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <ul class="bottom">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <ul class="front">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <ul class="behind">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <ul class="left">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <ul class="right">
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
    </div>
>css代码实现魔方的样式以及旋转
>    
    *{
        margin: 0px;
        padding: 0px;
    }
    ul{
        list-style: none;
    }
    html,body{
        height: 100%;
    }
    /**设置内容区域的大小，并居中*/
    .content{
        width: 300px;
        height: 300px;
        border: 0px solid black;
        position: absolute;
        top: 0px;
        left: 0px;
        right: 0px;
        bottom: 0px;
        margin: auto;
        /**需要将立方体设置为在3d空间显示，并兼容*/
        transform-style: preserve-3d;
        -webkit-transform-style: preserve-3d;
        -moz-transform-style: preserve-3d;
        -o-transform-style: preserve-3d;
        -ms-transform-style: preserve-3d;
        /*播放旋转动画*/
        animation: square 5s ease-in-out infinite alternate;
     }
     .content:hover{
        -webkit-animation-play-state:paused;
     }
     /*设置立方体的六个面的公共属性*/
    .content ul{
        width: 267px;
        height: 267px;
        border: 0px solid red;
        position: absolute;
        left: 0px;
        right: 0px;
        top: 0px;
        bottom: 0px;
        margin: auto;
    }
    /*设置每个面中的9个方块的公共属性*/
    .content ul li{
        width: 87px;
        height: 87px;
        border: 1px solid #ddd;
        border-radius: 10px;
        float: left;
    }
    /*折叠立方体的六个面*/
    .content .top{
        -webkit-transform: translateY(-135px)  rotateX(90deg);
    }
    .content .bottom{
        -webkit-transform: translateY(135px)  rotateX(-90deg);
    }
    .content .front{
        -webkit-transform:  translateZ(135px);
    }
    .content .behind{
        -webkit-transform:  translateZ(-135px);
    }
    .content .left{
        -webkit-transform: translateX(135px)  rotateY(-90deg);
    }
    .content .right{
        -webkit-transform: translateX(-135px)  rotateY(90deg);
    }
    /*定义每个面的颜色*/
    .content .top li{
        background-color: red;
    }
    .content .bottom li{
        background-color: blue;
    }
    .content .front li{
        background-color: pink;
    }
    .content .behind li{
        background-color: green;
    }
    .content .left li{
        background-color:yellow;
    }
    .content .right li{
        background-color:rgb(0, 249, 80); ;
    }
    /*设定旋转动画的关键帧*/
    @-webkit-keyframes square {
       20%{  -webkit-transform: rotate3d(1,1,1,150deg);}
       40%{  -webkit-transform: rotate3d(0,0,1,120deg);}
       60%{  -webkit-transform: rotate3d(1,1,1,180deg);}
       80%{  -webkit-transform: rotate3d(1,0,0,360deg);}
       to{  -webkit-transform: rotate3d(1,1,0,240deg);}
    }