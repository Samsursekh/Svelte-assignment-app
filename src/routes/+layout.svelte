<script>
	import Header from './Component/Header.svelte';
	import "../app.css";
	import HeroSection from './Component/HeroSectionPage1.svelte';
</script>

<div class="app">
	<Header />
  <div>
	<main class=""> 
		<slot />
	</main>


   </div>

</div>


