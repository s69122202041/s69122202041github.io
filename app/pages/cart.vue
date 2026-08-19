<template>
    <h1>cart page</h1>
    <div v-for="item in myCart">
        <div>
         Name: {{ item.name }}
         </div>
        <button @click="handleClickDelete(item.id)">ลบ</button>
        <hr />
    </div>
</template>


<script setup>
import dataMock from "~/data/mock-products.json"

const myCart = ref([])
const getProducts = () => {
const ls = localStorage.getItem("products")
    
    return ls
}

const handleClickDelete = (productId) => {
    console.log('id', productId)
    const ls = getProducts()
    const lsArray = JSON.parse(ls)
    const result = lsArray.filter((item) => {
        //  logic
        return item !== productId
    })
    const resultStr = JSON.stringify(result)
    localStorage.setItem("products", resultStr)
    updateMyCart()
}

const updateMyCart = () => {
    const productsLS = getProducts()
    const productsArray = JSON.parse(productsLS)
    
    const result = dataMock.Products.filter((item) => {

        return productsArray.includes(item.id)
    })

    myCart.value = result
}

onMounted(() => {
    // initial data
    updateMyCart() 
})
</script>