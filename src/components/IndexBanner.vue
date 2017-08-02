<template>
	<div class="banner">
		<!--轮播图 自动轮播 时间为2毫秒-->
		<mt-swipe :auto="2000">
			<!--轮播内容  遍历数据-->
      <mt-swipe-item v-for="data in banner" key="data.id">
        <img :src="data.src" alt="">
		    </mt-swipe-item>
		</mt-swipe>
	</div>

</template>
<script>
	export default {
    data() {
      return {
        banner: []
      }
    },
    // 挂载的时候进行数据请求https://easy-mock.com/mock/593ebbfe8ac26d795feb44f8/index/indexbanner
    mounted() {
    // get方法 请求
        this.axios.get('https://easy-mock.com/mock/593ebbfe8ac26d795feb44f8/index/indexbanner')
          .then((response)=> {
            this.banner = response.data.banner;
          })
          .catch(function (error) {
          })
      }
  }
</script>
<style lang="css" scoped>
.banner {
  width:100%;
  height: 15rem;
}
.banner img {
  width:100%;
  height: 100%;
  float: left;
}
</style>
