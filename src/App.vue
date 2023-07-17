<script setup>
import { reactive } from 'vue';


const state = reactive({
    firstNumber: 0,
    secondNumber: 0,
    result: 0,
    operation: 'Select the operation',
});

const addition = () => {
    state.result = parseFloat(state.firstNumber) + parseFloat(state.secondNumber);
}
const subtraction = () => {
    state.result = parseFloat(state.firstNumber) - parseFloat(state.secondNumber);
}
const multiplication = () => {
    state.result = parseFloat(state.firstNumber) * parseFloat(state.secondNumber);
}
const division = () => {
    state.result = parseFloat(state.firstNumber) / parseFloat(state.secondNumber);
}

const getOperation = () => {
    const { operation } = state;

    switch (operation) {
        case 'addition':
            return addition();
        case 'subtraction':
            return subtraction();
        case 'multiplication':
            return multiplication();
        case 'division':
            return division();
    }
}

</script>

<template>
    <div class="container md">
        <header class="p-5 mb-4 mt-4 bg-light rounded-3 text-center">
            <h1>Arithmetic Calculator</h1>
        </header>
        <form class="d-flex flex-column text-center gap-2" id="numbers">
            <label class="fw-bold fs-4" for="firstNumber">First Number</label>
            <input @keyup="event => state.firstNumber = event.target.value" id="firstNumber" type="number"
                placeholder="First Number" required>
            <label class="fw-bold fs-4" for="secondNumber">Second Number</label>
            <input @keyup="event => state.secondNumber = event.target.value" id="secondNumber" type="number"
                placeholder="Second Number" required>
            <label class="fw-bold fs-4" for="operation">Select the operation</label>
            <select class="form-select" id="operation" :on-click="getOperation()"
                @change="event => state.operation = event.target.value">
                <option selected>Select the operation</option>
                <option value="addition">addition</option>
                <option value="subtraction">subtraction</option>
                <option value="multiplication">multiplication</option>
                <option value="division">division</option>
            </select>

            <section id="result">
                <h3>Result:</h3>

                <span class="fs-4" id="result-number">{{ state.result }}</span>
            </section>
        </form>
    </div>
</template>

