<script setup>
import ThrownDices from './components/ThrownDices.vue';
import ScoreTable from './components/ScoreTable.vue';

const dice = [];
</script>

<template>
    <div id="title">
        <div id="yahtzeeTitle">
            <h1>Yahtzee</h1>
            <p>&#174;</p>
        </div>
        <div id="name">
            <h3>NAME</h3>
        </div>
        <hr />
    </div>

    <ThrownDices v-model="dice" />

    <ScoreTable />
</template>
