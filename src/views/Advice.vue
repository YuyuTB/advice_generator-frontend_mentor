<script setup>
import { ref, onMounted, onBeforeMount } from 'vue';
import DiceButton from '../components/DiceButton.vue';
import ApiFetch from '../components/ApiFetch.vue';

const dividerSrc = ref('');
const diceClick = ref(false);
const clickStart = () => {
    diceClick.value = true;
};
const clickEnd = () => {
    diceClick.value = false;
};

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
            <ApiFetch :clicked="diceClick" />
            <img
                :src="dividerSrc"
                alt="divider" />
            <DiceButton
                @clickStart="clickStart"
                @clickEnd="clickEnd" />
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
    min-width: 450px;
}

@media screen and (min-width: 1440px) {
    .advice-container {
        max-width: 45%;
        padding: 30px 25px 10px 25px;
    }
}
</style>
