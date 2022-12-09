<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<div class="text-column">
	<h1>About this app</h1>

	<p>
		This is a <a href="https://kit.svelte.dev">SvelteKit</a> app. You can make your own by typing the
		following into your command line and following the prompts:
	</p>

	<pre>npm create svelte@latest</pre>

	<p>
		The page you're looking at is purely static HTML, with no client-side interactivity needed.
		Because of that, we don't need to load any JavaScript. Try viewing the page's source, or opening
		the devtools network panel and reloading.
	</p>

	<p>
		The <a href="/sverdle">Sverdle</a> page illustrates SvelteKit's data loading and form handling. Try
		using it with JavaScript disabled!
	</p>
</div>
<script>
	 import MyFirstComponent from "../MyFirstComponent.svelte";
	let cats = [
		{ id: 'J---aiyznGQ', name: 'Keyboard Cat' },
		{ id: 'z_AbfPXTKms', name: 'Maru' },
		{ id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
	];
	let m = { x: 0, y: 0 };

// @ts-ignore
function handleMousemove( event) {
	m.x = event.clientX;
	m.y = event.clientY;
}

import { onMount } from 'svelte';

/**
     * @type {any[]}
     */
let photos = [];

onMount(async () => {
	const res = await fetch(`https://jsonplaceholder.typicode.com/photos/`);
	console.log(res);
	photos = await res.json();
});
</script>

<h1>The Famous Cats of YouTube</h1>

<ul>
	{#each cats as { id, name }, i}
		<li><a target="_blank" href="https://www.youtube.com/watch?v={id}" rel="noreferrer">
			{i + 1}: {name}
		</a></li>
	{/each}
</ul>
<div class="test" on:mousemove={handleMousemove}>
	The mouse position is {m.x} x {m.y}
</div>
<style>

.test {
		display: flex;
		flex-direction: column;
		height: 100px;
		align-self: center;
	}
	
</style>

<MyFirstComponent />


<!--
<div class="photos">
	{#each photos as photo}
		<figure>
			<img src={photo.thumbnailUrl} alt={photo.title}>
			<figcaption>{photo.title}</figcaption>
		</figure>
	{:else}
		
		<p>loading...</p>
	{/each}
</div> -->

