<template>
	<view class="pics">
		<scroll-view class="left" scroll-y>
			<view v-for="(item,index) in cates" :class="active===index?'active':''" :key="item.id" @click="leftClickHandel(index,item.id)">{{item.title}}</view>
		</scroll-view>
		<scroll-view class="right" scroll-y>
			<view class="item" v-for="item in secondData" :key="item.id">
				<image src="../../static/images/t.jpg" @click="previewImg(item.img_url)"></image>
				<text>{{item.title}}</text>
			</view>
			<text v-if="secondData.length===0">暂无数据</text>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				cates:[],
				active:0,
				secondData:[],
				urls:['../../static/images/t.jpg','../../static/images/t.jpg','../../static/images/t.jpg','../../static/images/t.jpg']
			}
		},
		methods: {
		async getPicsCate(){
			const res = await this.$myRequest({
				url:'/api/getimgcategory'
			})
			this.cates=res.data.message
			this.leftClickHandel(0,this.cates[0].id)
		},
		async leftClickHandel(index,id){
			this.active=index
			//获取右侧数据
			const res = await this.$myRequest({
				url:'/api/getimages/'+id
			})
			this.secondData=res.data.message
		},
		previewImg(current){
			const urls = this.secondData.map(item=>{
				return item.img_url
			})
			console.log(urls)
			uni.previewImage({
				current,
			urls:this.urls
			})
		}
		},
		onLoad() {
			this.getPicsCate()
		}
	}
</script>

<style lang="scss">
	page{
		height: 100%;
	}
.pics{	
	height: 100%;
	display: flex;
	.left{
		width: 220rpx;
		height: 100%;
		border-right: 1px solid #eee;
	}

	view{
		height: 60px;
		line-height: 30px;
		width: 220rpx;
		color: #333;
		text-align: center;
		font-size: 30rpx;
		border-top: 1px solid #eee;
	}
	.active{
		background-color: $shop-color;
		color: #fff;
	}
	.right{
		height: 100%;
		width: 500rpx;
		margin: 10rpx auto;
		.item{
			width: 520rpx;
			height: 60%;
			image{
				width: 530rpx;
				height: 530rpx;
				border-radius: 5px;
			}
			text{
				font-size: 30rpx;
				line-height: 60rpx;
			}
		}
	}
}
</style>
