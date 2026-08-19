<template>
    <h1>Index pages</h1>
    <p>
        <span>Name: </span>
        <span>{{ name }}</span>
    </p>
    <p>
        <span>Age: </span>
        <span>{{ age }}</span>
    </p>
    <button @click="handleclick">rename</button>
    <button @click="handleShowlogName">handleShowlogName</button>
    <button @click="handleAddAge">บวกอายุ</button>
    </template>

<script setup>
const name = ref("init")
const age = ref(0)

const handleAddAge = (data) => {
    let newAge = age.value
    newAge = newAge +1

    age.value = newAge
}

const handleShowlogName = () => {
    const Namevalue = name.value
    console.log(nameValue)
}

const handleclick = () => {
    // logic
    console.log('worked from handclick funciton')
    
    name.value = "wachirawit"
}
</script>