<script setup>
import {computed} from 'vue';
const thrownDices = defineModel();
console.log('ScoreTable thrownDices:', thrownDices.value);

function diceName(num) {
    const names = ['Aces', 'Twos', 'Threes', 'Fours', 'Fives', 'Sixes'];
    return names[num - 1];
}

// for (let i = 0; i < thrownDices.value.amount.length; i++) {

// }

const totalScore = computed(() => {
    return thrownDices.value.reduce((sum, item) => {
        return sum + item.number * item.amount;
    }, 0);
});

const bonus = computed(() => {
    if (totalScore.value > 63) {
        return 35;
    } else {
        return 0;
    }
});
</script>

<template>
    <div id="scoreBoard">
        <table id="upperSection">
            <tr>
                <th>Upper Section</th>
                <th>How to score</th>
                <th>Game 1</th>
                <th>Game 2</th>
                <th>Game 3</th>
                <th>Game 4</th>
                <th>Game 5</th>
                <th>Game 6</th>
            </tr>
            <tr v-for="item in thrownDices" :key="item.number">
                <td>{{ diceName(item.number) }} = {{ item.number }}</td>
                <td>Count and Add Only {{ diceName(item.number) }}</td>
                <td class="count">{{ item.amount }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Total score</td>
                <td>-></td>
                <td id="totalScore">{{ totalScore }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>
                    bonus
                    <span class="smallerTexts">If total score is 63 or over</span>
                </td>
                <td>Score 35</td>
                <td id="bonus">{{ bonus }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Total Of Upper Section</td>
                <td>-></td>
                <td id="totalOfUpperSection"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
        </table>

        <p id="lowerSectionTitle">Lower Section</p>

        <table id="lowerSection">
            <tr>
                <td>3 of a kind</td>
                <td>Add Total Of All Dice</td>
                <td id="threeOfAKind"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>4 of a kind</td>
                <td>Add Total Of All Dice</td>
                <td id="fourOfAKind"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Full House</td>
                <td>Score 25</td>
                <td id="fullHouse"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Sm. Straight Sequence of 4</td>
                <td>Score 30</td>
                <td id="smallStraight"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Lg. Straight Sequence of 5</td>
                <td>Score 40</td>
                <td id="longStraight"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Yahtzee 5 of a kind</td>
                <td>Score 50</td>
                <td id="yahtzee"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Chance</td>
                <td>Score Total Of All Dice</td>
                <td id="chance"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Total Of Lower Section</td>
                <td>-></td>
                <td id="totalOfLowerSection"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Grand Total</td>
                <td>-></td>
                <td id="grandTotal"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
        </table>
    </div>
</template>
