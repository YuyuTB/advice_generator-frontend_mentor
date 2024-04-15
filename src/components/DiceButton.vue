<script setup></script>
<template>
    <div class="dice-container">
        <img
            src="/images/icon-dice.svg"
            alt="Get a random quote" />
    </div>
</template>
<style scoped>
.dice-container {
    background-color: hsl(150, 100%, 66%);
    padding: 20px;
    border-radius: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    top: 45px;
}
img {
    width: 25px;
    height: 25px;
}
.dice-container:hover {
    cursor: pointer;
    box-shadow: 0px 0px 30px hsl(150, 100%, 66%);
}
</style>
