<template>
<div class="bg-gray-100 w-1/3 mx-auto pb-5">
    <h1 class="pt-4 text-2xl font-google">外幣換算小工具</h1>
    <div class="p-2 m-2 font-mono">
        <button @click="calUSD" class="btnDesign"><img src="../assets/united-states.png" class="w-5 inline-block">USD</button>
        <button @click="calEUR" class="btnDesign"><img src="../assets/european-union.png" class="w-5 inline-block">EUR</button>
        <button @click="calAUD" class="btnDesign"><img src="../assets/australia.png" class="w-5 inline-block">AUD</button>
        <button @click="calJPY" class="btnDesign"><img src="../assets/japan.png" class="w-5 inline-block">JPY</button>
        <button @click="calKRW" class="btnDesign"><img src="../assets/south-korea.png" class="w-5 inline-block">KRW</button>
    </div>
    <input type="text" v-model="inputDollar" class="border-2 border-black mx-auto text-center">
    <div class="p-3">
        <div v-if="dollarType">
            <h3> {{ inputDollar }} NTD = {{ result }} {{ dollarType }}</h3>
        </div>
        <div v-else>
            <h3>輸入你想轉換的新台幣數量</h3>
        </div>
    </div>
    <table class="mx-auto shadow-lg bg-white">
        <tr>
            <th class="tableDesign bg-blue-100">幣別</th><th class="tableDesign bg-blue-100">1新台幣=多少目標幣別</th>
        </tr>
        <tr>
            <td class="tableDesign"><img src="../assets/united-states.png" class="p-1 w-9 inline-block">USD</td><td class="tableDesign">{{ currData['USD'] }}</td>
        </tr>
        <tr>
            <td class="tableDesign"><img src="../assets/european-union.png" class="p-1 w-9 inline-block">EUR</td><td class="tableDesign">{{ currData['EUR'] }}</td>
        </tr>
        <tr>
            <td class="tableDesign"><img src="../assets/australia.png" class="p-1 w-9 inline-block">AUD</td><td class="tableDesign">{{ currData['AUD'] }}</td>
        </tr>
        <tr>
            <td class="tableDesign"><img src="../assets/japan.png" class="p-1 w-9 inline-block">JPY</td><td class="tableDesign">{{ currData['JPY'] }}</td>
        </tr>
        <tr>
            <td class="tableDesign"><img src="../assets/south-korea.png" class="p-1 w-9 inline-block">KRW</td><td class="tableDesign">{{ currData['KRW'] }}</td>
        </tr>
    </table>
    </div>
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
</style>