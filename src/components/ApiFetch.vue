<script setup>
import { ref, watchEffect, defineProps } from 'vue';

const props = defineProps(['clicked']);
const apiData = ref(null);

const fetchData = async () => {
    try {
        const response = await fetch('https://api.adviceslip.com/advice');
        if (!response.ok) {
            throw new Error('Error fetching data');
        }
        const jsonData = await response.json();
        apiData.value = jsonData;
    } catch (error) {
        console.log(error);
    }
};

watchEffect(() => {
    fetchData();
    if (props.clicked) {
        fetchData();
    }
});
</script>

<template>
    <template v-if="apiData">
        <h1>Advice #{{ apiData.slip.id }}</h1>
        <p>"{{ apiData.slip.advice }}"</p>
    </template>
</template>
<style scoped>
h1 {
    color: hsl(150, 100%, 66%);
    font-size: 0.8rem;
    text-transform: uppercase;
}
p {
    color: hsl(193, 38%, 86%);
    font-size: 28px;
    text-align: center;
}
</style>
