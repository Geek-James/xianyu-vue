<template>
	<div class="adbox">
		<mt-swipe :auto="5000">
			<mt-swipe-item v-for="data in ad" key="data.id">
        <p class="desc">{{data.desc}}</p>
        <img :src="data.src" alt="">
			</mt-swipe-item>
		</mt-swipe>
	</div>
</template>
<script>
export default {
	props: {
       	 ad: {
       	 	type: Array
       	 }
       }
}
</script>
<style lang="css" scoped>
.adbox{
	width: 100%;
	height: 7rem;
}
.adbox img{
	width: 100%;
	height: 100%;
	float: left;
}
.desc {
    text-align: left;
    font-size: 12px;
    color: black;
  }
</style>
