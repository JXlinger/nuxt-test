<template>
  <div class="container">
		<ul>
			<li v-for="item in bannerlist" :key="item.name">
				<img :src="'https://img.xhmwxy.com/' + item.image" />
			</li>
		</ul>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'
export default {
  components: {
    Logo
  },
	asyncData(){
		return axios.get('https://api.meiweixueyuan.cn/pc/banners',{
			headers:{
				Accept: 'application/prs.meiweixueyuan.v1+json'
			}
		})
		.then( res => {
			return {
				bannerlist: res.data.data
			}
			
		})
		.catch( error => {
			console.warn(error)
		})
	},
	head:{
		title: 'nuxt.js 体验，这是他的title',
		meta: [
				{name: 'viewport',content: 'width=device-width,initial-scale=1'},
				{name: 'discription',content: 'nuxt.js体验，这是描述'}
		]
	}
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}


</style>
