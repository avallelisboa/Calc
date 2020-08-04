<template>
    <div id="container">
        <header>
            <span><i></i></span>
            <p>CALCULATOR</p>
            <span><i></i></span>
        </header>
        <div>
            <input id="inputResult" type="text" :placeholder="ph" v-model="result">
        </div>
        <div id="numbers">
            <button v-on:click="addOperation('sum')" :disabled="this.result == ''|| this.nums.length == 0">+</button>
            <button v-on:click="addOperation('rest')" :disabled="this.result == ''|| this.nums.length == 0">-</button>
            <button v-on:click="addOperation('multiplication')" :disabled="this.result == ''|| this.nums.length == 0">*</button>
            <button v-on:click="addOperation('division')" :disabled="this.result == ''|| this.nums.length == 0">/</button>
            <button v-on:click="printNumber('7')">7</button>
            <button v-on:click="printNumber('8')">8</button>
            <button v-on:click="printNumber('9')">9</button>
            <button v-on:click="printNumber('0')">0</button>
            <button v-on:click="printNumber('4')">4</button>
            <button v-on:click="printNumber('5')">5</button>
            <button v-on:click="printNumber('6')">6</button>
            <button v-on:click="printNumber('.')">.</button>
            <button v-on:click="printNumber('1')">1</button>
            <button v-on:click="printNumber('2')">2</button>
            <button v-on:click="printNumber('3')">3</button>
            <button v-on:click="calculate()" :disabled="this.result == ''|| this.nums.length == 0">=</button>
        </div>
    </div>    
</template>

<script>

export default {
  name: 'Calc',
  data: function(){
      return{
        ph: '0',
        result: '',
        nums: [],
        operations: [],
      }
  },
  methods: {
      calculate: function(){
        if(this.result != ''){
           this.nums.push(this.result);
           this.result = '';
        }

        var i = 0;
        var l = this.operations.length;

        for(let o = 0; o < l; o++){
            if(this.operations[o] == "sum"){
                let n1 = parseFloat(this.nums[i]);
                let n2 = parseFloat(this.nums[i + 1])
                this.nums[i +1] = n1 + n2;
                i++;
            }
            if(this.operations[o] == "rest"){
                let n1 = parseFloat(this.nums[i]);
                let n2 = parseFloat(this.nums[i + 1])
                this.nums[i +1] = n1 - n2;
                i++;
            }
            if(this.operations[o] == "multiplication"){
                let n1 = parseFloat(this.nums[i]);
                let n2 = parseFloat(this.nums[i + 1])
                this.nums[i +1] * n1 - n2;
                i++;
            }
            if(this.operations[o] == "division"){
                let n1 = parseFloat(this.nums[i]);
                let n2 = parseFloat(this.nums[i + 1])
                this.nums[i +1] / n1 - n2;
                i++;
            }
          }
            let temp = this.nums[this.nums.length - 1];
            this.ph = temp;
            this.nums = new Array();
            this.operations = new Array();
        },
      addOperation: function(op){
        this.nums.push(parseFloat(this.result));
        this.operations.push(op);        
        this.result = '';
      },
      clear: function(){
          this.result = '';
      },
      printNumber: function(number){
        this.ph = '0';
        this.result += number;
      }
  }
}
</script>

<style lang="scss" scoped>
    #container{
        font-size: 150%;
        border-radius:5px;
        margin: 200px auto;
        width: 400px;
        height: 400px;
        header{
            font-family: Roboto;
            font-weight: normal;
            padding: 20px;
            letter-spacing: 3px;
            border-radius: 5px 5px 0px 0px;
            background-color: #e63c61;
            color:white;
            span{
                display: inline-block;
                width: 25%;
                margin: 0px;
                height: 100%;
            }
            p{
                display: inline-block;
                width: 50%;
                text-align: center;
                overflow: hidden;
                margin: 0px;
                padding: 0px;
            }
        }
        div{
            input{
                border: none;
                height: auto;
                width: 93%;
                padding-right: 5%;
                height: 80px;
                font-size: 150%;
                text-align: right;
            }
        }
       #numbers{
           height: 200px;
           border-radius: 0px 0px 5px 5px;
            button{
                width: 25%;
                height: 75px;
                margin: 0px;
                float: left;
                color: white;
                font-size: 150%;
                background-color: #161fc9;
                border: none;
            }
            button:nth-child(13){
                border-radius: 0px 0px 0px 5px;
            }
            button:last-child{
                border-radius: 0px 0px 5px 0px;
            }
            button:hover{
                background-color: #e63c61;
            }
       }
    }
</style>
