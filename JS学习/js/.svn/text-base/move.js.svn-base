 function getStyleAttr(obj,attr) {
    if(window.getComputedStyle) { //支持IE9+, 谷歌, 火狐..
    	return getComputedStyle(obj,null)[attr];
    }else{
		return obj.currentStyle[attr]; //支持IE8-
    }
}

//obj 对象
//attr 属性
//target 目标值
//s 定时器速度
//fn 回调函数
function move(obj,attr,target,s,fn){
	//1.目标值
	if(attr=="opacity"){
		target = target*100;
	}else{
		target = target;
	}
	clearInterval(obj.timer);
	obj.timer = setInterval(function(){
		//2.获取当前值
		if(attr=="opacity"){
			var start = parseFloat(getStyleAttr(obj,attr))*100;
		}else{
			var start = parseFloat(getStyleAttr(obj,attr));
		}
		//3.速度
		var speed = (target-start)/7;
		speed = speed>0?Math.ceil(speed):Math.floor(speed);
		//4.运动
		if(target==start){
			clearInterval(obj.timer);
			//判断是否存在回调函数
			if(fn){
				fn();
			}
		}else{
			if(attr=="opacity"){
				obj.style[attr] = (start+speed)/100;
				obj.style.filter="alpha(opacity="+start+speed+")";
			}else{
				obj.style[attr] = start+speed+"px";
			}
			
		}
	},s)
}
function bannerlunbo(){
	var banner = document.querySelector(".banner");
	var oimg = banner.querySelectorAll("img");
	var leftbtn = banner.querySelector(".left-btn");
	var rightbtn = banner.querySelector(".right-btn");
	var oli = banner.querySelectorAll("li");
	var i = 0;
	//自动轮播
	var lunbotimer = setInterval(lunbo,3000);
	function lunbo(){
		i++;
		if(i==oimg.length){
			i=0;
		}
		icon2();
	}
	function icon2(){
		for(var j=0;j<oimg.length;j++){
			oimg[j].style.opacity = 0;
		}
		icon();
		oimg[i].style.opacity = 1;
	}
	function icon(){
		for(var j=0;j<oli.length;j++){
			oli[j].style.background = "#999";
		}
		oli[i].style.background = "white";
	}
	
	//鼠标移入停止轮播
	banner.onmouseenter = function(){
		clearInterval(lunbotimer);
	}
	//鼠标移出开启轮播
	banner.onmouseleave = function(){
		lunbotimer = setInterval(lunbo,3000);
	}
	
	//下一张
	rightbtn.onclick = function(){
		lunbo();
	}
	//上一张
	leftbtn.onclick = function(){
		i--;
		if(i<0){
			i=oimg.length-1;
		}
		icon2();
	}
	//小圈圈
	for(var k=0;k<oli.length;k++){
		oli[k].index = k;
		oli[k].onclick = function(){
			i=this.index;
			icon2();
		}
	}
}
