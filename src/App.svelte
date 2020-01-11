<script>
	import Product from './Product.svelte';
	import Button from './Button.svelte';
	import Cart from './Cart.svelte';

	let title = '';
	let price = 0;
	let description = '';

	let products = [];
	let cartItems = [];

	function setTitle(event) {
		title = event.target.value;
	}

	function createProduct() {
		const newProduct = {
			title: title,
			price: price,
			description: description
		};

		// products = products.concat(newProduct);
		products = [...products, newProduct];
	}

	function addToCart(event) {
		const selectedTitle = event.detail;

		cartItems = cartItems.concat({
			...products.find(prod => prod.title === selectedTitle)
		});
		console.log(cartItems);
	}
</script>

<!-- MARK UP ||||||||||||||||||||||||||||||||| -->
<section>
	<Cart items={cartItems} />
</section>

<hr>

<section>
	<div>
		<label for="title">Title</label>
		<input type="text" id="title" value={title} on:input={setTitle} />
		<!-- binding through function with "on:"  -->
	</div>
	<div>
		<label for="price">Price</label>
		<input type="number" id="price" bind:value={price} />
		<!-- shorthand binding syntax without the need to write a function -->
	</div>
	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value={description}></textarea>
	</div>

	<Button on:click={createProduct}>Create Product</Button>
</section>

<hr>

<section>
	{#if products.length === 0}
		<p>No Products added, yet!</p>
		{:else}
		{#each products as product}
			<Product 
				productTitle={product.title}
				productPrice={product.price}
				productDescription={product.description}
				on:addcart={addToCart} />
		{/each}
	{/if}

	<!-- <Product productTitle={title}
			productPrice={price}
			productDescription={description} /> -->
</section>



<style>

	section {
		width: 30rem;
		margin: auto;
	}

	input,
	label,
	textarea {
		width: 100%;
	}
</style>