<template>
	<div class="wrapper">
		<!-- 头部-->
		<section class="header">
			<div class="header">
				<!--头部搜索框 图片 输入框-->
				<div class="scanner">
					<img src="../assets/images/二维码.png" alt="">
				</div>
				<!--搜索框  路由跳转router-link to="/search" -->
				<router-link to="/search" class="search">
					<input type="search" placeholder="请输入关键字" />
				</router-link>
				<div class="morekind" @click="category">
					<img src="../assets/images/分类.png" alt="">
				</div>
      </div>
		</section>
		<!--分割线-->
		<div class="block"></div>
		<!--轮播图-->
    <IndexBanner></IndexBanner>
    <!--产品搜索入口-->
    <IndexGoods :goodslist="goodslist"></IndexGoods>
    <!--间隔-->
    <div class="interval"></div>
    <!--分类列表-->
    <IndexRecom :typelist = "typelist"></IndexRecom>
    <!-- 滚动轮播广告-->
    <!--间隔-->
    <div class="interval"></div>
    <IndexAd :ad="ad"></IndexAd>

		</div>
</template>
<script>
	import NavBottom from '../components/NavBottom'
	import IndexBanner from '../components/IndexBanner.vue'
	import IndexGoods from '../components/IndexGoods.vue'
	import IndexRecom from '../components/IndexRecom.vue'
	import IndexAd from '../components/IndexAd.vue'
	import IndexNav from '../components/IndexNav.vue'
	import { mapActions } from 'vuex'
	export default {
		components: {
		  IndexBanner,
			IndexGoods,
			IndexRecom,
			IndexAd,
			IndexNav,
			NavBottom
		},
		data() {
			return {
				goodslist: [],
				typelist: [],
				ad: []
			}
		},
		mounted() {
			this.$store.dispatch('setCurindex', 0)
			this.axios.get('https://easy-mock.com/mock/5955a3849adc231f356de97e/index/goodslist/list')
				.then((response) => {
					this.goodslist = response.data.goodslist
				})
				.catch(function(error) {
					console.log(error)
				})
			this.axios.get('https://easy-mock.com/mock/5955a3849adc231f356de97e/index/goodslist/typelist')
				.then((response) => {
					this.typelist = response.data.typelist
				})
				.catch(function(error) {

				})
			this.axios.get('https://easy-mock.com/mock/5955a3849adc231f356de97e/index/goodslist/ad')
				.then((response) => {
					this.ad = response.data.ad

				})
				.catch(function(error) {

				})
		},
		methods: {
			category() {
				this.$router.push({
					path: '/category'
				})
			}
		}
	}
</script>
<style lang="scss" scoped>
	.wrapper {
		width: 100%;
		min-height: 70rem;
		position: relative;
		.block {
			height: 4.5rem;
		}
		.header {
			width: 100%;
			height: 4.5rem;
			background-color: #ffda44;
			z-index: 10;
			position: fixed;
			top: 0;
			display: -webkit-flex;
			display: flex;
			align-items: center;
			.scanner {
				width: 2rem;
				height: 2rem;
				margin-left: 1rem;
				margin-right: 1rem;
				img {
					width: 2rem;
					height: 2rem;
				}
				input {
					display: none;
				}
			}
			.search {
				flex: 1;
				height: 3rem;
				display: flex;
				align-items: center;
				outline: none;
				border-radius: .4rem;
				border: none;
				padding-left: 2.8rem;
				background-color: #fff;
				background-image: url('../assets/images/search.png');
				background-repeat: no-repeat;
				background-size: 1.8rem 1.8rem;
				background-position: .8rem 50%;
				input {
					border: none;
          width: 100%;
          height: 100%;
				}
			}
			.morekind {
				width: 2rem;
				height: 2rem;
				margin-left: 1rem;
				margin-right: 1rem;
				img {
					width: 2rem;
					height: 2rem;
				}
			}
		}
	}
  .interval {
    height: 0.7rem;
    width: 100%;
    background-color: #dedede;
  }
</style>
