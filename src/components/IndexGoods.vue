<template>
  <div class="goodBox">
    <ul class="goodList">
      <li v-for="data in goodslist" key="data.id">
        <div class="item">
          <img class="typelist-img" :src="data.src">
          <p class="typelist-title">{{data.title}}</p>
          <p class="typelist-desc">{{data.desc}}</p>
        </div>
      </li>
    </ul>
  </div>

</template>
<script>
	export default {
      props: {
          goodslist: {
              type:Array
          }
      }
	}
</script>
<style type="text/css" scoped>
*{
  margin:0;
  padding:0;
}
  ul,li {
    list-style:none;
  }
.goodList {
  width:98%;
  height: auto;
  margin: auto;
  overflow: hidden;
  display: -webkit-flex;
  display: flex;
  text-align: center;
}
.goodList li {
  flex: 1;
  position: relative;
  height: auto;
  margin: 0.4rem 2% 0.4rem 2%;
}
.item {
  flex: 1;
  text-decoration: none;
}
.typelist-img{
  width: 3rem;
  height: 3rem;
}
.typelist-title{
  font-size: 1.4rem;
  padding: 0 0.4rem;
  color: black;
  font-weight: 400;
}
.typelist-desc{
  color: #666;
  font-size: 1rem;
  margin-bottom: .5rem;
}
</style>
