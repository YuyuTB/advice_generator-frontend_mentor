<script setup>
import { ref, onMounted, onBeforeMount } from 'vue';
import DiceButton from '../components/DiceButton.vue';

const dividerSrc = ref('');

const updateScreenSize = () => {
    const screenWidth = window.innerWidth;
    dividerSrc.value =
        screenWidth <= 1440
            ? '/images/pattern-divider-mobile.svg'
            : '/images/pattern-divider-desktop.svg';
};
onMounted(() => {
    window.addEventListener('resize', updateScreenSize);
    updateScreenSize();
});
onBeforeMount(() => {
    window.removeEventListener('resize', updateScreenSize);
});
</script>

<template>
    <div class="invisible-div">
        <section class="advice-container">
            <h1>h1</h1>
            <p>
                Lorem ipsum dolor, sit amet consectetur adipisicing elit.
                Laudantium perferendis quia
            </p>
            <img
                :src="dividerSrc"
                alt="divider" />
            <DiceButton />
        </section>
    </div>
</template>

<style scoped>
.invisible-div {
    padding-bottom: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
}
.advice-container {
    background-color: hsl(217, 19%, 24%);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    padding: 20px 10px 10px 10px;
    margin: 10px;
}
h1 {
    color: hsl(150, 100%, 66%);
    font-size: 1rem;
}
p {
    color: hsl(193, 38%, 86%);
    font-size: 28px;
    text-align: center;
}
@media screen and (min-width: 1440px) {
    .advice-container {
        max-width: 45%;
        padding: 30px 25px 10px 25px;
    }
}
</style>
