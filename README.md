<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<style>
			.wrapper {
				width: 370px;
				height: 200px;
				border: 15px solid black;
				border-image: radial-gradient(black,white,black, white,black,black) 1;
				position: relative;
			}
		
			/* 5张图片叠加到一块 */
			.wrapper img {
				width: 100%;
				height: 100%;
				position: absolute;
				left: 0;
				top: 0;
				display: none;
			}
		
			.wrapper img:nth-of-type(1) {
				display: block;
			}
		
			/* 小圆点 */
			.btn {
				width: 80px;
				display: flex;
				justify-content: space-around;
				position: absolute;
				left: 285px;
				bottom: -14px;
				z-index: 100
			}
		
			.btn span {
				display: block;
				width: 5px;
				height: 5px;
				border: 3px solid white;
				border-radius: 50%;
			}
		
			/* 左右箭头 */
			.wrapper a {
				text-decoration: none;
				font-size: 50px;
				color: red;
				position: absolute;
				top: 35%;
			}	
			.active {
				background-color: blue;
			}
		</style>
        <script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-1.9.0.min.js"></script>
	</head>
	<body>
		<div class="wrapper">
			<div class="contain">
				<img class="img666" src="./images1/W020110417320153842809.jpg" alt="">
				<img class="img666" src="./images1/W020110417372214444705.jpg" alt="">
				<img class="img666" src="./images1/W020110417358924996040.jpg" alt="">
				<img class="img666" src="./images1/W020110417309440968483.jpg" alt="">
				<img class="img666" src="./images1/W020110417312673166063.jpg" alt="">
			</div>
			<div class="btn">
				<span class="active span666"></span>
				<span class="span666"></span>
				<span class="span666"></span>
				<span class="span666"></span>
				<span class="span666"></span>
			</div>
		</div>
		<script>
			var trindex=0;
		
			// 悬浮停止
			$(".wrapper").mouseover(function(){
				clearInterval(id);
			});
			$(".wrapper").mouseout(function(){
					autoplay();
			})
			
			
			// 下一张
			function next_pic(){
				trindex++;
				if(trindex>4){
					trindex=0;
				}
				addStyle();
			}
			
			// 上一张
			function prev_pic(){
				trindex--;
				if(trindex<0){
					trindex=4;
				}
				addStyle();
			}
			
			// 控制图片显示隐藏,小圆点背景色
			function addStyle(){
				$(".img666").eq(trindex).fadeIn();
				$(".img666").eq(trindex).siblings().fadeOut();
				$(".span666").eq(trindex).addClass("active");
				$(".span666").eq(trindex).siblings().removeClass("active");
			}
			
			// 自动轮播
			var id;
			autoplay();
			function autoplay(){
				id=setInterval(function(){
					next_pic();
				},2000)
			}
			
		</script>
	</body>
</html>
