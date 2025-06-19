<script setup>
import {computed} from 'vue';
const thrownDices = defineModel();
console.log('ScoreTable thrownDices:', thrownDices.value);

function diceName(num) {
    const names = ['Aces', 'Twos', 'Threes', 'Fours', 'Fives', 'Sixes'];
    return names[num - 1];
}

// upperSection
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

const totalOfUpperSection = computed(() => {
    return thrownDices.value.reduce((sum, item) => {
        return sum + item.number * item.amount;
    }, 0);
});

// lowerSection
const threeOfAKind = computed(() => {
    const obj = thrownDices.value.find(item => item.number === 3);

    const result = obj ? obj.amount * obj.number : 0;

    return result;
});

const fourOfAKind = computed(() => {
    const obj = thrownDices.value.find(item => item.number === 4);

    const result = obj ? obj.amount * obj.number : 0;

    return result;
});

const fullHouse = computed(() => {
    const hasTwo = thrownDices.value.find(item => item.amount === 2);
    const hasThree = thrownDices.value.find(item => item.amount === 3);

    return hasTwo && hasThree ? 25 : 0;
});

const calculateSortedKeys = computed(() => {
    const sortedEntries = [...thrownDices.value].sort((a, b) => a.number - b.number);

    const sortedKeys = sortedEntries.flatMap(entry => Array(entry.amount).fill(entry.number));

    console.log(sortedKeys);
    return sortedKeys;
});

function hasStraight(sortedKeys, length) {
    for (let i = 0; i <= sortedKeys.length - length; i++) {
        let straight = true;
        for (let j = 0; j < length - 1; j++) {
            if (sortedKeys[i + j] + 1 !== sortedKeys[i + j + 1]) {
                straight = false;
                break;
            }
        }
        if (straight) return true;
    }
    return false;
}

const smallStraight = computed(() => {
    const sortedKeys = calculateSortedKeys.value;
    if (hasStraight(sortedKeys, 4)) {
        console.log('Small Straight!');
        return 30;
    }
    return 0;
});

const longStraight = computed(() => {
    const sortedKeys = calculateSortedKeys.value;
    if (hasStraight(sortedKeys, 5)) {
        console.log('Long Straight!');
        return 40;
    }
    return 0;
});

const yahtzee = computed(() => {
    const sortedKeys = calculateSortedKeys.value;
    if (hasStraight(sortedKeys, 6)) {
        console.log('Long Straight!');
        return 50;
    }
    return 0;
});

const Chance = computed(() => {
    return thrownDices.value.reduce((sum, item) => {
        return sum + item.number * item.amount;
    }, 0);
});

const totalOfLowerSection = computed(() => {
    return (
        threeOfAKind.value +
        fourOfAKind.value +
        fullHouse.value +
        smallStraight.value +
        longStraight.value +
        yahtzee.value +
        Chance.value
    );
});

const grandTotal = computed(() => {
    return totalOfUpperSection.value + totalOfLowerSection.value;
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
                <td id="totalOfUpperSection">{{ totalOfUpperSection }}</td>
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
                <td id="threeOfAKind">{{ threeOfAKind }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>4 of a kind</td>
                <td>Add Total Of All Dice</td>
                <td id="fourOfAKind">{{ fourOfAKind }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Full House</td>
                <td>Score 25</td>
                <td id="fullHouse">{{ fullHouse }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Sm. Straight Sequence of 4</td>
                <td>Score 30</td>
                <td id="smallStraight">{{ smallStraight }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Lg. Straight Sequence of 5</td>
                <td>Score 40</td>
                <td id="longStraight">{{ longStraight }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Yahtzee 5 of a kind</td>
                <td>Score 50</td>
                <td id="yahtzee">{{ yahtzee }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Chance</td>
                <td>Score Total Of All Dice</td>
                <td id="chance">{{ Chance }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Total Of Lower Section</td>
                <td>-></td>
                <td id="totalOfLowerSection">{{ totalOfLowerSection }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Grand Total</td>
                <td>-></td>
                <td id="grandTotal">{{ grandTotal }}</td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
        </table>
    </div>
</template>
