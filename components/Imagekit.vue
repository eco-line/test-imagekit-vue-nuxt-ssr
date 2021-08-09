<template>
  <div>
    <h1><center>Blurred images are loaded, scroll to load original images</center></h1>

	<div class="empty-space"></div>

	<div v-for="(item, id) in urlArray" :key="id">
		<ik-image 
			:src="item"
			loading="lazy"
			:lqip="{active:true}"
		/>
	</div>
  </div>
</template>

<style>
body {
  padding: 20px;
}

h1 {
  margin-bottom: 1em;
}

.empty-space{
	height : 5000px;
}
</style>

<script>
import Vue from 'vue';
import ImageKit, { IKImage, IKContext, IKUpload } from "imagekitio-vue"

var ikUrlEndpoint = "https://ik.imagekit.io/0gr1w07bzr6iu";
var ikPublicKey = "public_iVvQuCWJAUgooh9zXj24O2Zo3z4=";

Vue.use(ImageKit, {
	urlEndpoint: ikUrlEndpoint,
	publicKey: ikPublicKey,
})
let path = "/default-image.jpg";
let urlArray = [
	"https://ik.imagekit.io/0gr1w07bzr6iu/default-image.jpg",
	"https://ik.imagekit.io/0gr1w07bzr6iu/blue_balloon.jpg",
	"https://ik.imagekit.io/0gr1w07bzr6iu/files/test11_5TZhYLYt3.jpg"
]
export default {
	name: "app",
	components: {
		IKImage,
		IKContext,
		IKUpload
	},
	data() {
		return {
			urlEndpoint: ikUrlEndpoint,
			publicKey: ikPublicKey,
			path: path,
			src: `${ikUrlEndpoint}/${path}`,
			urlArray,
		};
	},
	methods: {
		onError(err) {
			console.log("Error");
			console.log(err);
		},
		onSuccess(res) {
			console.log("Success");
			console.log(res);
		}
	}
};
</script>
