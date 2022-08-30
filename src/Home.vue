<template><div class="sm:grid sm:grid-cols-12 gap-2">
	<Books class='col-span-12 sm:col-span-9' :books='books' @bookAdded='addBook' @bookRemoved='removeBook' />
	<div class='hidden sm:block sm:col-span-3'><Cart class='sticky top-8' :products='products' /></div>	
	<button class='fixed sm:hidden top-36 bg-gray-200 p-2 border-b-2 border-gray-400' @click='cartShow=true'>cart</button>
	<div v-if='cartShow' class='p-4 ring-2 ring-gray-500 fixed sm:hidden centerIt bg-gray-200 flex flex-col gap-2 items-center'><Cart :products='products' /><button class="text-2xl hover:scale-110 transition-all duration-200" @click='cartShow=false'>&#9874;</button></div>	
</div></template>

<script setup>
	import { ref } from 'vue'
	import Books from '/src/components/Books.vue'
	import Cart from '/src/components/Cart.vue'

	const products = ref([])
	const cartShow = ref(false)

	const books = [
		{
			title: "Official Practical Tests",
			author: "Mike Chapple",
			price: 3100,
			image: "/assets/1.png"
		},
		{
			title: "Python",
			author: "Gabbor Szabo",
			price: 4188,
			image: "/assets/2.png"
		},
		{
			title: "Advanced R",
			author: "Haddley Wickham",
			price: 2599,
			image: "/assets/3.png"
		},
		{
			title: "Android Programming",
			author: "Bill Phillips",
			price: 2696,
			image: "/assets/4.png"
		},
		{
			title: "Angular: From Theory To Practice",
			author: "Asim Hussain",
			price: 3580,
			image: "/assets/5.png"
		},
		{
			title: "Artificial Intelligence",
			author: "George F. Luger",
			price: 950,
			image: "/assets/6.png"
		},
		{
			title: "Atomic Kotlin",
			author: "Bruce Eckel",
			price: 2132,
			image: "/assets/7.png"
		},
		{
			title: "Beginning C# and .NET",
			author: "Benjamin Perkins",
			price: 3648,
			image: "/assets/8.png"
		},
		{
			title: "C How to Program",
			author: "Paul Deitel, Harvey Deitel",
			price: 1250,
			image: "/assets/9.png"
		},
		{
			title: "Data Mining",
			author: "Mehmed Kantardzic",
			price: 2840,
			image: "/assets/10.png"
		}
	]

	const addBook = (x) => { products.value.push(x)	}
	const removeBook = (x,y) => { 
		// products.value.splice(products.value.indexOf(x), 1)	
		products.value = products.value.filter(x => x.title != y)
	}
</script>

<style scoped>
.centerIt{
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
}
</style>