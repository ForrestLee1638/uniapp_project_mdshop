<template>
	<view class="contact">
		<image class="img" src=../../static/images/we.jpg></image>
		<view class="info">
			<view @click="phone">联系电话：19985076924（点击拨打）</view>
			<view>地址：广西自治区南宁市西乡塘区大学东路101号</view>
			<map class="map" :longitude="longitude" :latitude="latitude" :markers="markers" :scale="scale"></map>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				longitude:108.244075,
				latitude:22.842128,
				scale:11,
				markers:[
					{
						longitude:108.244075,
						latitude:22.842128,
						iconPath:'../../static/images/biaoji.png',
						width:30,
						height:30
					}
				]
			}
		},
		methods: {
			phone(){
				uni.makePhoneCall({
					phoneNumber:'19985076924'
				})
			}
		}
	}
</script>

<style lang="scss">
	.contact{
		.img{
			width: 750rpx;
			height: 320rpx;
		}
		.info{
			view{
				padding: 10rpx 20rpx;
				font-size: 30rpx;
				line-height: 60rpx;
				border-bottom: 1px solid #eee;
			}
			.map{
				width: 750rpx;
				height: 750rpx;
			}
		}
	}

</style>
