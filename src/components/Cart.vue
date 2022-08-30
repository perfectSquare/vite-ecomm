<template><div class="p-2">
	<div class='p-2 bg-gradient-to-r from-gray-100 to-gray-300 border-b-2 border-gray-400 text-center text-xl'>Cart</div>	

	<div class="p-1 flex flex-col gap-2">	
	<template v-for='(product,i) in products' :key='i'>

		<div class="p-1 flex flex-col gap-2 bg-green-50 border-r-2 border-r-gray-400">
			<div>Book: {{product.title}}</div>
			<div>Price: {{product.price}}</div>
		</div>

	</template>
	</div>

	<div class="p-1 flex flex-col gap-2">
		<div>Books: {{booksCount}}</div>
		<div>Total: Rs. {{total}}</div>
		<div class="bg-blue-50 p-2 border-b-2 border-gray-400">5% Total: Rs. {{totalFive}}</div>
		<button class="p-1 rounded-md bg-slate-700 text-white hover:bg-slate-800 transition-all duration-200">proceed</button>
	</div>
	<Teleport to='#tel'>
		<div v-if='five' class='fixed top-24 left-24 p-4 bg-cyan-200 flex gap-2'><div>you got 5% discount for above Rs 5000</div><button @click='five=false' class='text-2xl self-center hover:scale-110 transition-all duration-100'>&#9874;</button></div>
	</Teleport>

</div></template>

<script setup>
	import { ref, computed } from 'vue'

	const five = ref(false)
	const props = defineProps({		products:Array	})
	const booksCount = computed(() => {		return props.products.length	})

	const total = computed(() => {
		let totalP = 0
		for(let x of props.products){
			totalP += x.price
		}
		return totalP
	})

	const totalFive = computed(() => {
		let totalP = 0
		for(let x of props.products){
			totalP += x.price
		}
		five.value = false
		if(totalP > 5000){
			five.value = true			
			totalP = totalP - totalP*0.05
			return totalP
		}
		return totalP
	})

</script>


<style scoped></style>