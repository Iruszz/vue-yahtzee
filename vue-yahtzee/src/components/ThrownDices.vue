<script setup>
import {ref, computed} from 'vue';
import DiceIcon from './DiceIcon.vue';

const thrownDices = defineModel();

const count = ref([
    {number: 1, amount: 0},
    {number: 2, amount: 0},
    {number: 3, amount: 0},
    {number: 4, amount: 0},
    {number: 5, amount: 0},
    {number: 6, amount: 0},
]);

const flattenedDice = computed(() => count.value.flatMap(d => Array(d.amount).fill(d.number)));

console.log('flattenedDice:', flattenedDice);

function increment() {
    count.value.forEach(d => (d.amount = 0));

    // const results = [];
    for (let i = 0; i < 5; i++) {
        const roll = Math.floor(Math.random() * 6) + 1;
        // results.push(roll);
        count.value[roll - 1].amount++;
    }

    // thrownDices.value = count.value;
    thrownDices.value = count.value.map(item => ({...item}));

    console.log('count.value inside of increment:', count.value);
    console.log('ThrownDices inside of increment:', thrownDices.value);
}

console.log('count.value 2:', count.value);
</script>

<template>
    <div class="dice-container">
        <DiceIcon v-for="(diceNumber, index) in flattenedDice" :key="index" :diceNumber="diceNumber" />
    </div>

    <button id="dice" @click="increment"><strong>Throw!</strong></button>
</template>
