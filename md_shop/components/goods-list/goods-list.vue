<template>
	<view class="goods_list">
		<view class="goods_item" v-for="item in goods" :key="item.id" @click="navigator(item.id)">
			<image src="../../static/images/iphone6.jpg"></image>
			<view class="price">
				<text>￥{{item.sell_price}}</text>
				<text>￥{{item.market_price}}</text>
			</view>
			<view class="name">
				{{item.title}}
			</view>
		</view>
			
	</view>
</template>

<script>
	export default {
	props:['goods'],
	methods:{
		navigator(id){
			this.$emit('goodsItemClick',id)
		}
	}
	}
	
</script>

<style lang="scss">
	.goods_list {
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;
			padding:0 15rpx;
			box-sizing: border-box;
			.goods_item {
				background-color: #fff;
				width: 355rpx;
				margin-top: 15rpx;
				image {
					display: block;
					margin:0 auto;
					width: 60%;
					height: 120px;
				}
			}
	
			.price {
				color: $shop-color;
				font-size: 36rpx;
				margin: 20rpx 0 10rpx 0;
				text:nth-child(2){
					color: #ccc;
					font-size: 28rpx;
					margin-left: 17rpx;
					text-decoration: line-through;
				}
			}
			.name{
				font-size: 28rpx;
				line-height: 50rpx;
				padding-bottom: 15rpx;
				padding-top: 10rpx;
			}
		}
</style>
