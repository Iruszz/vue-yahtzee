<script setup></script>

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
            <tr>
                <td>Aces = 1</td>
                <td>Count and Add Only Aces</td>
                <td class="count"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Twos = 2</td>
                <td>Count and Add Only Twos</td>
                <td class="count"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Threes = 3</td>
                <td>Count and Add Only Threes</td>
                <td class="count"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Fours = 4</td>
                <td>Count and Add Only Fours</td>
                <td class="count"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Fives = 5</td>
                <td>Count and Add Only Fives</td>
                <td class="count"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Sixes = 6</td>
                <td>Count and Add Only Sixes</td>
                <td class="count"></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
                <td></td>
            </tr>
            <tr>
                <td>Total score</td>
                <td>-></td>
                <td id="totalScore"></td>
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
                <td id="bonus"></td>
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
