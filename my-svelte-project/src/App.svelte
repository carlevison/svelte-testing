<script lang="ts">
	export let name: string;
 	import {Cloudinary} from '@cloudinary/base';
	import {AdvancedImage} from '@cloudinary/svelte';

	// Import any actions required for transformations.
	import {fill} from "@cloudinary/base/actions/resize";

	// Create a Cloudinary instance and set your cloud name.
	const cld = new Cloudinary({
		cloud: {
			cloudName: 'demo'
		}
	});

	// Instantiate a CloudinaryImage object for the image with the public ID, 'sample'.
	const myImage = cld.image('sample');
	

	// Resize to 250 x 250 pixels using the 'fill' crop mode.
	myImage.resize(fill().width(250).height(250));

	const myUrl = myImage.toURL(); 
</script>

<main>
	<h1>Hello my {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<AdvancedImage cldImg={myImage}/>
	<img src={myUrl} alt="my flowers"> 
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>