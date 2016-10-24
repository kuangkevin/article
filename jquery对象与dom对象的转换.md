##js代码中DOM对象与jQuery对象不能混合使用,及其转换##
>在jqeury选择器中得到的jquery对象和js中document.getElementById()得到的dom对象是两种不同的对象，jquery对象不能使用dom方法,dom也不能使用jquery方法，但是可以通过转换将dom对象强制转换城jquery对象。<br>
>dom对象
>
    var p1=document.getElementById("p1");
    var btn1=document.getElementById("btn1");
    btn1.onclick=function ()
    {
        p1.innerHTML="Hello World!";
    }
>jquery对象
>      
    $("#btn1").click(function()
    {
        $("#p1").html("Hello World!")
    });
>以上两种方法所实现的效果都是一样的，但是要注意在js代码中要注意以上两种方法不能混合使用。<br>
>举一个例子，就是this，有些初学者经常会在jquery中这么写：this.css({color:"red"});但是这么写是会出错的因为这里的this代表的是一个dom对象，而.css({color:"red"})是jquery方法，所以要解决这个问题就要进行转换，将dom对象转换成jquery对象。
>>1.jquery对象转换成dom对象：
>>   
    $("#btn1").get(0).onclick=function()
    {   };
>>2.dom对象转换成jquery对象：
>>    
    var btn1=document.getElementById("btn1");
    $(btn1).click(function()
    {   });
>
>通过上面方法将dom对象与jquery对象互相转换之后，dom对象才能使用jquery方法。