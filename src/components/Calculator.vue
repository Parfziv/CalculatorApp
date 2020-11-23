<template>
<div>
    <div class="flex rounded shadow-lg border justify-center w-64 m-auto mt-32 bg-purple-300 p-4">
        <div class="grid grid-cols-4 gap-x-8 gap-y-4">
                <div class="col-span-4 text-center pb-12 rounded border border-gray-800 bg-gray-900 text-white">{{number || 0}}</div>
                <button class="border p-2 bg-gray-900 text-white p-2" @click="clearData">C</button>
                <button class="border p-2 bg-gray-900 text-white">X</button>
                <button class="border p-2 bg-gray-900 text-white" @click="percent">%</button>
                <button class="border p-2 bg-gray-900 text-white"  @click="divide">/</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('7')">7</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('8')">8</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('9')">9</button>
                <button class="border p-2 bg-gray-900 text-white" @click="times">*</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('4')">4</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('5')">5</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('6')">6</button>
                <button class="border p-2 bg-gray-900 text-white" @click="minus">-</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('1')">1</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('2')">2</button>
                <button class="border p-2 bg-gray-900 text-white" @click="input('3')">3</button>
                <button class="border p-2 bg-gray-900 text-white" @click="plus">+</button>
                <button class="border p-2 bg-gray-900 text-white col-span-2 text-center" @click="input('0')">0</button>
                <button class="border p-2 bg-gray-900 text-white" @click="dot">.</button>
                <button class="border p-2 bg-gray-900 text-white" @click="equal">=</button>
        </div>


    </div>
</div>
  
</template>

<script>
export default {
    data(){
        return{
        previous: null,
        operator: null,
        number: '',
        operatorClicked: false,
        };
    },
    methods: {
        clearData(){
            this.number= '';
        },
        input(digit){
            if(this.operatorClicked){
                this.number='';
                this.operatorClicked =false;
            }
            this.number = `${this.number}${digit}` ;
        },
        dot(){
            if(this.number.indexOf('.') === -1){
                this.input('.') ;
            }
        },
        setPrevious(){
                this.previous = this.number;
                this.operatorClicked = true;
        },
        percent(){
            this.number = parseFloat(this.number) / 100;
        },
        divide(){
            this.operator = (a,b) => a / b ;
            this.setPrevious();
        },
        minus(){
            this.operator = (a,b) => a - b ;
            this.setPrevious();

        },
        plus(){
            this.operator = (a,b) => a + b ;
            this.setPrevious();


        },
        times(){
            this.operator = (a,b) => a * b ;
            this.setPrevious();
        },
        equal(){
            this.number = this.operator(parseFloat(this.number), parseFloat(this.previous));

        },
    }

}
</script>

<style>

</style>