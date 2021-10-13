<template>
	<view class="home">
		<swiper indicator-dots circular autoplay>
			<swiper-item v-for="item in swipers" :key="item.id" @click="navigator(item.id)">
				<image :src="item.img"></image>
			</swiper-item>
		</swiper>
		<!--导航区域-->
		<view class="nav">
			<view class="nav_item" v-for="(item,index) in navs" :key="index" @click="navItemClick(item.path)">
				<view :class="item.icon"></view>
				<text>{{item.title}}</text>
			</view>
		</view>
		<!--推荐商品区域-->
		<view class="hot_goods">
			<view class="tit">推荐商品</view>
			<goods-list @goodsItemClick="goGoodsDetail" :goods="goods"></goods-list>
		</view>
	</view>
</template>

<script>
	import goodsList from '../../components/goods-list/goods-list.vue'
	export default {
		data() {
			return {
				swipers: [],
				goods: [],
				navs: [{
						icon: 'iconfont icon-chaoshi',
						title: '明东超市',
						path: '/pages/goods/goods',
					},
					{
						icon: 'iconfont icon-lianxi',
						title: '联系我们',
						path: '/pages/contact/contact',
					},
					{
						icon: 'iconfont icon-tupian1',
						title: '社区图片',
						path: '/pages/pics/pics',
					},
					{
						icon: 'iconfont icon-shipin',
						title: '学习视频',
						path: '/pages/videos/videos',
					}


				]
			}
		},
		onLoad() {
			this.getSwipers()
			this.getHotGoods()
		},
		methods: {
			//获取热门商品列表数据
			async getHotGoods() {
				const res = await this.$myRequest({
					url: '/api/getgoods?pageindex=1'
				})
				this.goods = res.data.message
			},
			//获取轮播图数据
			async getSwipers() {
				// uni.request({
				// 	url:'http://localhost:8082/api/getlunbo',
				// 	success:res=> {
				// 		console.log(res)
				// 		if(res.data.status!==0){
				// 			return uni.showToast({
				// 				title:'获取数据失败'
				// 			})
				// 		}
				// 		this.swipers = res.data.message
				// 	}
				// })
				const res = await this.$myRequest({
					url: '/api/getlunbo'
				})
				this.swipers = res.data.message
			},
			//导航点击处理的函数
			navItemClick(url) {
				uni.navigateTo({
					url
				})
			},
			//导航到商品详情页
			goGoodsDetail(id){
				uni.navigateTo({
					url:'/pages/goods-detail/goods-detail?id='+id
				})
			}
		},
		//注册组件
		components: {
			"goods-list": goodsList
		}
	}
</script>

<style lang="scss">
	.home {
		swiper {
			width: 750rpx;
			height: 380rpx;

			image {
				height: 100%;
				width: 100%;
			}
		}

		.nav {
			display: flex;

			.nav_item {
				width: 25%;
				text-align: center;

				text {
					font-size: 30rpx;
				}

				view {
					width: 120rpx;
					height: 120rpx;
					background-color: $shop-color;
					border-radius: 60rpx;
					margin: 10px auto;
					line-height: 120rpx;
					color: white;
					font-size: 70rpx;

				}
			}
		}

		.hot_goods {
			background-color: #eee;
			overflow: hidden;
			margin-top: 10px;

			.tit {
				padding: 0 15rpx;
				font-weight: 700;
				height: 50px;
				line-height: 50px;
				color: $shop-color;
				text-align: center;
				letter-spacing: 20px;
				background-color: #fff;
				margin: 7rpx 0;
			}


		}
	}
</style>
