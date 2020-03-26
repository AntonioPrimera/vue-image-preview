<template>
	<div class="border flex justify-center items-center" style="background-repeat: repeat" :style="style">
		<template v-if="url">
			<img :src="url" :alt="alt" class="w-full">
		</template>
		<template v-else>
			<p v-text="alt"></p>
		</template>
	</div>
</template>

<script>
	export default {
		mixins: [],
		
		components: {},
		
		props: {
			fileSelector: String,
			
			//initial preview image
			src: {
				type: String,
				'default': null,
			},
			
			alt: {
				type: String,
				'default': 'Image Preview',
			},
			
			transparent: {
				type: Boolean,
				'default': false,
			}
		},
		
		data() {
			return {
				url: null,
			}
		},
		
		computed: {
			style() {
				return this.transparent && this.url
					? "background-image: url(\"data:image/svg+xml,%3Csvg width='1000' height='1000' xmlns='http://www.w3.org/2000/svg'%3E%3Cdefs%3E%3Cpattern id='tbg' x='0' y='0' width='.02' height='.02'%3E%3Crect x='0' y='0' width='12' height='12' style='fill:%23cecece'/%3E%3Crect x='12' y='0' width='12' height='12' style='fill:%23eaeaea'/%3E%3Crect x='0' y='12' width='12' height='12' style='fill:%23eaeaea'/%3E%3Crect x='12' y='12' width='12' height='12' style='fill:%23cecece'/%3E%3C/pattern%3E%3C/defs%3E%3Crect id='pt' fill='url(%23tbg)' width='1200' height='1200'/%3E%3C/svg%3E\");"
					//"background-image: url(\"data:image/svg+xml,%3Csvg width='1000' height='1000' xmlns='http://www.w3.org/2000/svg'%3E%3Cdefs%3E%3Cpattern id='tbg' x='0' y='0' width='.04' height='.04'%3E%3Crect x='0' y='0' width='20' height='20' style='fill:%23cecece'/%3E%3Crect x='20' y='0' width='20' height='20' style='fill:%23eaeaea'/%3E%3Crect x='0' y='20' width='20' height='20' style='fill:%23eaeaea'/%3E%3Crect x='20' y='20' width='20' height='20' style='fill:%23cecece'/%3E%3C/pattern%3E%3C/defs%3E%3Crect id='pt' fill='url(%23tbg)' width='1000' height='1000'/%3E%3C/svg%3E\");"
					//"background-image: url(\"data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='8' height='8' viewBox='0 0 8 8'%3E%3Cg fill='%23707070' fill-opacity='0.23'%3E%3Cpath fill-rule='evenodd' d='M0 0h4v4H0V0zm4 4h4v4H4V4z'/%3E%3C/g%3E%3C/svg%3E\");"
					: '';
			}
		},
		
		watch: {
			//watch properties
			//e.g. watchedAttributeName: function(value) { this.someOtherAttribute = value * 2; }
		},
		
		methods: {
			readURL(event) {
				let input = event.target;
				
				if (input.files && input.files[0]) {
					let reader = new FileReader();

					reader.onload = e => this.url = e.target.result;

					reader.readAsDataURL(input.files[0]);
				}
			}
		},
	
		created() {
			if (typeof this.src === 'string' && this.src.length) this.url = this.src;
		},
		
		mounted() {
			//$("#imgInp").change(function() {
			//	readURL(this);
			//});
			//	},
			
			let fileElement = document.querySelector(this.fileSelector);
			if (fileElement) fileElement.addEventListener('change', this.readURL);
		},
	}
</script>

<style lang="scss" scoped>
	/* scss style to be added */
</style>
