<template>
    <h1>TWD to foreign currency</h1>
    <button @click="calUSD" class="usd">USD</button>
    <button @click="calEUR" class="eur">EUR</button>
    <button @click="calAUD" class="aud">AUD</button>
    <button @click="calJPY" class="jpy">JPY</button>
    <button @click="calKRW" class="krw">KRW</button>
    <input type="text" v-model="inputDollar">
    <div v-if="dollarType">
        <h3> {{ inputDollar }} TWD = {{ result }} {{ dollarType }}</h3>
    </div>
    <div v-else>
        <h3>Input the amount of TWD to convert</h3>
    </div>
    <ul>
        <li>
            <h4>USD to TWD: {{ currData['USD'] }}</h4>
        </li>
        <li>
            <h4>EUR to TWD: {{ currData['EUR'] }}</h4>
        </li>
        <li>
            <h4>AUD to TWD: {{ currData['AUD'] }}</h4>
        </li>
        <li>
            <h4>JPY to TWD: {{ currData['JPY'] }}</h4>
        </li>
        <li>
            <h4>KRW to TWD: {{ currData['KRW'] }}</h4>
        </li>
    </ul>
</template>

<script>
export default {
    data() {
        return {
            currData: [],
            exchange: 0,
            inputDollar: 0,
            result: 0,
            dollarType: ''
        }
    },
    mounted() {
        fetch('https://v6.exchangerate-api.com/v6/19d4303920de70888a25c89f/latest/TWD')
            .then(res => res.json())
            .then(data => this.currData = data.conversion_rates)
            .catch(err => console.log(err.message));
    },
    methods: {
        calUSD() {
            this.exchange = this.currData['USD'];
            this.dollarType = 'USD';
            this.result = this.exchange * this.inputDollar;
            this.result = this.result.toFixed(2);
        },
        calEUR() {
            this.exchange = this.currData['EUR'];
            this.dollarType = 'EUR';
            this.result = this.exchange * this.inputDollar;
            this.result = this.result.toFixed(2);
        },
        calAUD() {
            this.exchange = this.currData['AUD'];
            this.dollarType = 'AUD';
            this.result = this.exchange * this.inputDollar;
            this.result = this.result.toFixed(2);
        },
        calJPY() {
            this.exchange = this.currData['JPY'];
            this.dollarType = 'JPY';
            this.result = this.exchange * this.inputDollar;
            this.result = this.result.toFixed(2);
        },
        calKRW() {
            this.exchange = this.currData['KRW'];
            this.dollarType = 'KRW';
            this.result = this.exchange * this.inputDollar;
            this.result = this.result.toFixed(2);
        }
    }
}
</script>

<style>
    button {
        margin: 0px 5px 20px 0px;
        border-radius: 6px;
        font-size: 20px;
        color: white;
    }
    button.usd {
        background: crimson;
    }
    button.eur {
        background: blue;
    }
    button.aud {
        background: green;
    }
    button.jpy {
        background: purple;
    }
    button.krw {
        background: black;
    }
    button:hover {
        background: lightgray;
        color: black;
    }
    input {
        display: block;
        margin: 0px 0px 0px 560px;
        width: 290px;
    }
    li {
        list-style-type: none;
        margin: 0px 50px 0px 0px;
    }
</style>