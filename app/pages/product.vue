<template>
    <h1>product page</h1>
     <div v-for="item in data.Products">
        <div>ID: {{ item.id }}</div>
        <div>Name: {{ item.name }}</div>
        <div>
            <button @click="handleClickAdd(item.id)">Add</button>
        </div>
        <hr />
    </div>
</template>

<script setup>
import mockProduct from "~/data/mock-products.json"

const data = ref([])

const handleClickAdd = (productid) => {
    const ls = localStorage.getItem('products')
    const lsArray = JSON.parse(ls)
    const products = lsArray || []
    products.push(productid)
    const productsStr = JSON.stringify(products)
    localStorage.setItem('products', productsStr)
}

onMounted(() => {
    data.value = mockProduct
    console.log('assign done !')
})
</script>