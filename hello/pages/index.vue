<template>
  <div class="container">
		<ul>
			<li v-for="item in bannerlist" :key="item.name">
				<img :src="'https://img.xhmwxy.com/' + item.image" />
        {{ item.name }}
			</li>
		</ul>
    <nuxt-link to="/home">home</nuxt-link>
    <div class="donghua_wrap">
      <div class="box">
        <div class="donghua">
        </div>
        <div class="wrap">call</div>
      </div>

    </div>

  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'
export default {
  components: {
    Logo
  },
	async asyncData(){
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
</style>
