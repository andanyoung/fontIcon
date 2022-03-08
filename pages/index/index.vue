<template>
	<view class="content">

		<view class="icon-container" id="icon">
			<text class="text">{{title}}</text>
		</view>
		<button @click="handleGImg">生成图片</button>

		<view><a class="down" href="" download="downImg">下载</a></view>
	</view>
</template>

<script>
	import html2canvas from "@/lib/html2canvas.min.js"
	export default {
		data() {
			return {
				title: '考'
			}
		},
		onLoad() {

		},
		methods: {
			handleGImg() {

				html2canvas(document.querySelector("#icon")).then(function(canvas) {

					//document.body.appendChild(canvas);
					//canvas转换成url，然后利用a标签的download属性，直接下载，绕过上传服务器再下载
					document.querySelector(".down").setAttribute('href', canvas.toDataURL());
				});
			}
		}
	}
</script>

<style>
	.content {
		background-color: rgb(0, 0, 0, 0);
	}

	.icon-container {
		width: 512px;
		height: 512px;
		background-image: linear-gradient(#1877e9, #5fcdff);
		/* border-radius: 44px; */
		padding: 36px;
		overflow: hidden;

	}

	.text {
		line-height: 512px;
		display: block;
		/* width: 512px; */
		/* height: 512px; */
		font-size: 400px;
		text-align: center;
		color: white;

	}
</style>
