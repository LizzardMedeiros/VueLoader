<template>
	<div v-if="is_loading" id="loader">
		<div 
			id="spinner"
			:style="'border-top-color:'+color"
		></div>
	</div>
</template>

<script>
export default {
  name: 'VueLoader',
	props:{
		color:{
			default:'#e53935'
		}
	},
	methods:{
		start(){
			document.getElementsByTagName("BODY")[0].style.overflow = "hidden";
			//$("body").css("overflow", "hidden");
			this.is_loading = true;
			this.$emit('is-loading', this.loading);
		},
		stop(){
			document.getElementsByTagName("BODY")[0].style.overflow = "auto";
			//$("body").css("overflow", "auto");
			this.is_loading = false;
			this.$emit('is-loading', this.loading);
		}
	},
	data() {
		return {
			is_loading : false
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	#spinner {
		position: absolute;
		left: calc(50vw - 30px);
		top: calc(50vh - 30px);
		width: 60px;
		height: 60px;
		z-index: 11;
		border: 8px solid #f3f3f3;
		border-radius: 50%;
		border-top: 8px solid;
		-webkit-animation: spin 2s linear infinite;
		animation: spin 2s linear infinite;
	}

	#loader{
		position: fixed;
		top:0;
		left:0;
		z-index: 10;
		background-color: rgba(.51,.51,.51,.8);
		width: 100vw;
		height: 100vh;
	}

	@-webkit-keyframes spin {
		0% { -webkit-transform: rotate(0deg); }
		100% { -webkit-transform: rotate(360deg); }
	}

	@keyframes spin {
		0% { transform: rotate(0deg); }
		100% { transform: rotate(360deg); }
	}

	.animate-bottom {
		position: relative;
		-webkit-animation-name: animatebottom;
		-webkit-animation-duration: 1s;
		animation-name: animatebottom;
		animation-duration: 1s
	}

	@-webkit-keyframes animatebottom {
		from { bottom:-100px; opacity:0 } 
		to { bottom:0px; opacity:1 }
	}

	@keyframes animatebottom { 
		from{ bottom:-100px; opacity:0 } 
		to{ bottom:0; opacity:1 }
	}
</style>
