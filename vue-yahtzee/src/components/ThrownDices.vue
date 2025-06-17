<script setup>
import {ref} from 'vue';
import DiceIcon from './DiceIcon.vue';

const count = ref([
    {number: 1, amount: 0},
    {number: 2, amount: 0},
    {number: 3, amount: 0},
    {number: 4, amount: 0},
    {number: 5, amount: 0},
    {number: 6, amount: 0},
]);

const thrownDices = ref([]);

function increment() {
    count.value.forEach(d => (d.amount = 0));

    const results = [];
    for (let i = 0; i < 6; i++) {
        const roll = Math.floor(Math.random() * 6) + 1;
        results.push(roll);
        count.value[roll - 1].amount++;
    }

    thrownDices.value = results;
    console.log('New roll:', results);
}
</script>

<template>
    <div class="dice-container">
        <DiceIcon v-for="(dice, index) in thrownDices" :key="index" :diceNumber="dice" />
    </div>

    <button id="dice" @click="increment"><strong>Throw!</strong></button>
</template>
