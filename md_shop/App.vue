<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
@font-face {
  font-family: "iconfont"; /* Project id  */
  src: url('~@/static/fonts/iconfont.ttf?t=1625930222070') format('truetype');
}

.iconfont {
  font-family: "iconfont" !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.icon-lianxi:before {
  content: "\e649";
}

.icon-chaoshi:before {
  content: "\e68a";
}

.icon-tupian1:before {
  content: "\e626";
}

.icon-shipin:before {
  content: "\e6a8";
}

.gomeImgLoad{
				width: 750rpx;
				height: 100%;
				vertical-align: bottom;
				
			}
</style>
