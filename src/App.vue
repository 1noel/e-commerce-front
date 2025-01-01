<template>


<main class="flex">

  <side class="w-[17%] fixed custom h-screen">
    <div>
      <h1>Buy and Sell</h1>
    </div>


    <!-- navigation -->
  <div class="mt-10 px-7">
    <ul class="space-y-4 text-gray-600 text-sm">
      <li>
        <a href="#"> Home</a>
      </li>
      
      <li class="relative">
        <button 
          @click="isOpen = !isOpen" class="flex justify-between items-center gap-2 hover:text-gray-800">

          <span>Discover</span>
          <svg 
            class="w-4 h-4 transition-transform"
            :class="{ 'rotate-180': isOpen }"
            xmlns="http://www.w3.org/2000/svg" 
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor">

            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
          </svg>
        </button>
        
        <!-- Dropdown Menu -->
        <ul 
          v-show="isOpen"
          class="pl-4 mt-2 space-y-2 text-gray-500">
          <li><a href="#" class="hover:text-gray-800">New Arrivals</a></li>
          <li><a href="#" class="hover:text-gray-800">Featured</a></li>
          <li><a href="#" class="hover:text-gray-800">Categories</a></li>
          <li><a href="#" class="hover:text-gray-800">Collections</a></li>
        </ul>
      </li>

        <li>
          <a href="#">Popular Products</a>
        </li>
        <li>
        <a href="#">Top Authors</a>
        </li>
      <li>
        <a href="#">Feed</a>
      </li>
      <li>
            <a href="#">Contact</a>
      </li>

    </ul>
  </div>


  </side>

  
 <!-- contents -->
 <section class="w-[83%] ml-[17%]">
    
  
 <section class="mx-5">
<!-- headers -->
<header class="flex p-3  justify-between items-center">
<div>

  <!-- search -->
  <div class="relative">
    <span class="absolute left-3 top-2.5 text-gray-500">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
        <path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" />
      </svg>
    </span>
    <input 
      type="text" 
      v-model="searchQuery"
      @input="handleSearch"
      class="bg-gray-100 rounded-full px-12 py-2 w-80 focus:outline-none text-gray-800" 
      placeholder="Search products..."
    >
    <span class="absolute right-3 top-2.5 text-gray-500">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M7 4a3 3 0 016 0v4a3 3 0 11-6 0V4zm4 10.93A7.001 7.001 0 0017 8a1 1 0 10-2 0A5 5 0 015 8a1 1 0 00-2 0 7.001 7.001 0 006 6.93V17H6a1 1 0 100 2h8a1 1 0 100-2h-3v-2.07z" clip-rule="evenodd" />
          </svg>
        </span>
    
  </div>
  
  </div>

<div class="flex space-x-3 items-center">
  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-500" viewBox="0 0 20 20" fill="currentColor">
    <path d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z" />
  </svg> 
    <span class="relative">
       <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-500" viewBox="0 0 20 20" fill="currentColor">
         <path d="M10 2a6 6 0 00-6 6v3.586l-.707.707A1 1 0 004 14h12a1 1 0 00.707-1.707L16 11.586V8a6 6 0 00-6-6zM10 18a3 3 0 01-3-3h6a3 3 0 01-3 3z" />
       </svg>
       <span class="absolute -top-1 -right-1 h-2 w-2 bg-yellow-500 rounded-full flex items-center justify-center text-xs text-white"></span>
    </span>
    
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 text-gray-500" viewBox="0 0 20 20" fill="currentColor">
        <path d="M3 1a1 1 0 000 2h1.22l.305 1.222a.997.997 0 00.01.042l1.358 5.43-.893.892C3.74 11.846 4.632 14 6.414 14H15a1 1 0 000-2H6.414l1-1H14a1 1 0 00.894-.553l3-6A1 1 0 0017 3H6.28l-.31-1.243A1 1 0 005 
        1H3zM16 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM6.5 18a1.5 1.5 0 100-3 1.5 1.5 0 000 3z" />
      </svg> 
      
      <button class="bg-yellow-500 px-5 py-2 text-sm rounded-full">Become a seller</button>
  <span class="">
      <img src="./assets/images/iconpro.png" alt="" class="border border-dashed border-yellow-500 p-1 rounded-full">
  </span>
</div>

</header>
  
  <div class="my-5">
      <h1 class="text-md  text-gray-600">Discover / Electronics</h1>
      <h1 class="text-lg font-semibold text-gray-800">Best Selling Electronics Products - Weekly Update.</h1>
  </div>

  <!-- buttons -->

  <div class="overflow-x-auto pb-4">
    <ul class="flex flex-nowrap gap-2 min-w-max px-4">
      <li v-for="category in categories" :key="category">
        <a 
          href="#" :class="[
            'whitespace-nowrap inline-block px-4 py-2 rounded-full text-sm transition-colors',
            category === 'All' 
              ? 'bg-gray-800 text-white' 
              : 'bg-gray-100 text-gray-500 hover:bg-gray-800 hover:text-white'
          ]"
        >
          {{ category }}
        </a>
      </li>
    </ul>
  </div>


<!-- products -->
<div class="grid md:grid-cols-3 gap-8 my-5">
    <div v-for="product in filteredProducts" 
         :key="product.id" 
         class="border rounded-xl shadow-sm">
      <div class="flex justify-center items-center">
        <img :src="product.image" :alt="product.name" class="w-72">
      </div>
      <div class="p-2">
        <div class="flex space-x-2 items-center">
          <img src="./assets/images/iconpro.png" alt="Seller Icon" class="w-8 h-8">
          <div>
            <p class="font-semibold text-gray-800">{{ product.name }}</p>
            <span class="text-sm text-gray-600">{{ product.store }}</span>
          </div>
        </div>
        <div class="px-10">
          <p class="space-x-2 text-sm my-0.5">
            <span class="text-yellow-500 font-semibold">${{ product.price }}</span>
            <span class="text-gray-500 line-through">${{ product.originalPrice }}</span>
          </p>
          <div class="flex justify-between items-center">
            <p class="text-gray-600 space-x-2 text-sm">
              <span>{{ product.sales }} sales</span>
              <span class="text-yellow-500 text-lg">★</span>
              <span>{{ product.rating }}({{ product.reviews }})</span>
            </p>
            <button class="text-2xl font-semibold text-gray-500">
              <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
        <path d="M3 1a1 1 0 000 2h1.22l.305 1.222a.997.997 0 00.01.042l1.358 5.43-.893.892C3.74 11.846 4.632 14 6.414 14H15a1 1 0 000-2H6.414l1-1H14a1 1 0 00.894-.553l3-6A1 1 0 0017 3H6.28l-.31-1.243A1 1 0 005 
        1H3zM16 16.5a1.5 1.5 0 11-3 0 1.5 1.5 0 013 0zM6.5 18a1.5 1.5 0 100-3 1.5 1.5 0 000 3z" />
      </svg> 
            </button>   
                 </div>
        </div>
      </div>
    </div>
  </div>



</section>



</section>
</main>
</template>


<script setup>
import { ref, computed } from 'vue'
import cameraImage from './assets/images/camera.png'
import shoeImage from './assets/images/shoe1.png'
import macImage from './assets/images/mac.png'

const isOpen = ref(false)

const categories = [
  'All',
  'Bags',
  'Food',
  'Books',
  'Clothes',
  'Grocery',
  'Furniture',
  'Baby care',
  'Stationery',
  'Beauty & Makeup',
  'icon'
]


// seaarch
const searchQuery = ref('')
const products = ref([
  {
    id: 1,
    name: 'Nikon D7500 DSLR Camera',
    store: 'Nikon Official Store',
    image: cameraImage,
    category: 'Electronics',
    price: 1199.00,
    originalPrice: 1499.00,
    sales: 243,
    rating: 4.8,
    reviews: 156
  },
  {
    id: 2,
    name: 'Nike Air Max 270',
    store: 'Nike Sports',
    category: 'Shoes',
    image: shoeImage,
    price: 149.99,
    originalPrice: 199.99,
    sales: 876,
    rating: 4.9,
    reviews: 342
  },
  {
    id: 3,
    name: 'MacBook Pro M2 14-inch',
    store: 'Apple Store',
    category: 'Electronics',
    image: macImage,
    price: 1899.00,
    originalPrice: 1999.00,
    sales: 534,
    rating: 4.9,
    reviews: 267
  }
])

const filteredProducts = computed(() => {
  const query = searchQuery.value.toLowerCase()
  return products.value.filter(product => {
    return (
      product.name.toLowerCase().includes(query) ||
      product.store.toLowerCase().includes(query) ||
      product.category.toLowerCase().includes(query)
    )
  })
})

const handleSearch = () => {
  // You can add debounce here if needed
  console.log('Filtered products:', filteredProducts.value)
}
</script>

<style>
.custom{
  background-color: #F9FAFB ;
}
</style>

