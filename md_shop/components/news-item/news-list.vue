<template>
	<view>
	<view class="news_itme" v-for="item in list" :key="item.id" @click="navigator(item.id)">
		<image src="../../static/images/t2.jpg" mode=""></image>
		<view class="right">
				<view class="tit">
			{{item.title}}
			<view class="info">
				<text>发布时间：{{item.addtime | formatDate}}</text>
				<text>浏览：{{item.click}}</text>
			</view>
		</view>
		</view>
	</view>
	</view>
</template>

<script>
	export default{
		props:['list'],
		filters:{
			formatDate(date){
				return '2021-07-12'
				
			}
		},
		methods:{
			navigator(id){
				this.$emit('itemClick',id)
			}
		}
	}
</script>

<style lang="scss">
	.news_itme{
		display: flex;
		padding: 10rpx 20rpx;
		border-bottom: 1px solid $shop-color;
		image{
			min-width: 200rpx;
			max-width: 200rpx;
			height: 150rpx;
		}
	.right{
		margin-left: 15rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	.tit{
			font-size: 30rpx;
			.info{
				margin-top: 30rpx;
				font-size: 24rpx;
				text:nth-child(2){
					margin-left:30rpx;
				}
			}
		}
	}
	}
</style>
