<script setup>
    import { ref, reactive } from 'vue';

   let input = [];
   let display = ref('')
   let result = ref('0')

   function takeInput(text){
    input.push(text);
    display.value = input.join('')
   }

   function erase(){
    input.pop()
    display.value = input.join('')
   }

   function clearDisplay() { 
    display.value = ''
   }

   function calculate(){
    let string =  input.join('')
    result.value = eval(string)
   }
</script>
<template>
    <div class="container">
        <section id="Display-area">
            <div class="input">{{ display }}</div>
            <div class="result">{{ result }}</div>
        </section>
        <section class="keypad-btns">
            <button type="button" class="fn-btn" @click="clearDisplay()">C</button>
            <button type="button" class="fn-btn" @click="erase()">&#11013;</button>
            <button type="button" class="fn-btn" @click="takeInput('/')">/</button>
            <button type="button" class="fn-btn" @click="takeInput('%')">%</button>
            <button type="button" class="num-btn" @click="takeInput('7')">7</button>
            <button type="button" class="num-btn" @click="takeInput('8')">8</button>
            <button type="button" class="num-btn" @click="takeInput('9')">9</button>
            <button type="button" class="fn-btn" @click="takeInput('*')">*</button>
            <button type="button" class="num-btn" @click="takeInput('4')">4</button>
            <button type="button" class="num-btn" @click="takeInput('5')">5</button>
            <button type="button" class="num-btn" @click="takeInput('6')">6</button>
            <button type="button" class="fn-btn" @click="takeInput('-')">-</button>
            <button type="button" class="num-btn" @click="takeInput('1')">1</button>
            <button type="button" class="num-btn" @click="takeInput('2')">2</button>
            <button type="button" class="num-btn" @click="takeInput('3')">3</button>
            <button type="button" class="fn-btn" @click="takeInput('+')">+</button>
            <button type="button" class="num-btn" @click="takeInput('00')">00</button>
            <button type="button" class="num-btn" @click="takeInput('0')">0</button>
            <button type="button" class="num-btn" @click="takeInput('.')">.</button>
            <button type="button" class="fn-btn" @click="calculate()">=</button>
        </section>
    </div>
</template>
<style>
    *{
        margin:0;
        padding:0;
    }
    .container {
        background-color: #131313;
        max-width: 300px;
        /* height: 100vh; */
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 0px 35px 25px 35px;
        border-radius: 10px;
        user-select: none;
    }

    #Display-area {
        width: 100%;
        margin: 3vh 0;
        display: grid;
        grid-template-columns: 100%;
        grid-template-rows: repeat(2, minmax(40px, auto));
        word-wrap: break-word;
        padding-bottom: 20px;
        border-bottom: 1px rgba(128, 128, 128, 0.116) solid;
    }

    #Display-area .input {
        /* display: flex; */
        text-align: right;
        height: 8vh;
        color: white;
        font-size: xx-large;
        line-height: 2;
        word-wrap: break-word;
    }

    #Display-area .result {
        text-align: right;
        color: rgba(150, 150, 150, 0.87);
        height: 7px;
        line-height: 3;
        font-size: larger;
    }

    .keypad-btns {
        display: grid;
        grid: repeat(5, 70px) / repeat(4, 70px);
        grid-row-gap: 20px;
        grid-column-gap: 20px;
    }

    .keypad-btns button {
        outline: none;
        border: none;
        border-radius: 10px;
        background-color: #131313;
        color: white;
        font-size: x-large;
    }

    .keypad-btns .fn-btn {
        color: #ff8800;
    }

    .num-btn:hover,.fn-btn:hover {
        background-color: rgba(29, 29, 29, 0.979);
    }

    @media only screen and (max-width: 600px) {
        body {
            background-color: #131313;
            align-items: flex-start;
        }
    }
</style>