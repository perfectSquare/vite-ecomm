<template><div class='p-2'>


	<div class="p-2 border-b-2 border-cyan-200 mb-2">Available Books <span class="text-xs p-2">let we are on products > Books</span></div>

	<div class="p-2 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-2">
	<template v-for='(book,i) in books' :key='i'>
		<div class="relative bg-gray-100 p-2 border-t-2 border-zinc-200 hover:border-zinc-400 flex flex-col items-center">			
			<div class="flex flex-col items-center mb-8">
			<img :src="book.image" alt="">
			<div class="titleFont">{{book.title}}</div>
			<div>by: {{book.author}}</div>
			<div>price: {{book.price}}</div>			
			</div>
			<div class="absolute bottom-0">
				<button @click='[$emit("bookAdded", book), addStatus($event)]' class="p-1 rounded-md bg-slate-700 text-white hover:bg-slate-800 transition-all duration-200">add to cart</button>
				<button @click='[$emit("bookRemoved", book, book.title), removeStatus($event)]' class="hidden p-1 rounded-md bg-red-800 text-white hover:bg-red-900 transition-all duration-200">remove from cart</button>
			</div>			
		</div>
	</template>
	</div>


</div></template>

<script setup>
	
	import { ref } from 'vue'

	const props = defineProps({		books: Array	})
	const emits = defineEmits(['bookAdded', 'bookRemoved'])

	const addStatus = (e) => {
		e.target.classList.add('hidden')
		e.target.nextElementSibling.classList.remove('hidden')
	}
	const removeStatus = (e) => {
		e.target.classList.add('hidden')
		e.target.previousElementSibling.classList.remove('hidden')
	}

</script>

<style scoped>
.titleFont{ font-family:'cd' }
</style>