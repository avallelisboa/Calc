<template>
    <div id="container">
        <header>
            <span><i></i></span>
            <p>CALCULATOR</p>
            <span><i></i></span>
        </header>
        <div>
            <input type="text" v-model="result">
        </div>
        <div id="numbers">
            <button v-on:click="addOperation('sum')">+</button>
            <button v-on:click="addOperation('rest')">-</button>
            <button v-on:click="addOperation('multiplication')">*</button>
            <button v-on:click="addOperation('division')">/</button>
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
            <button v-on:click="calculate()">=</button>
        </div>
    </div>    
</template>

<script>

export default {
  name: 'Calc',
  props:{
        result: String,
        numbers: [Array, String],
        operations: [Array, String]
  },
  methods: {
      calculate: function(){
          if(this.operation == "sum"){
            let r = 0;
            this.numbers.forEach(e => {
                var n = parseInt(e);
                r += n;
            });
            this.$emit('result', toString(r));
          }if(this.operation == "rest"){
              let l = this.numbers.length - 1;
              let r = 0;
              let n1, n2;
              for(let i = 1 ; i < l; i++){
                if(i == 1){
                    n1 = parseInt(this.numbers[i-1]);
                    n2 = parseInt(this.numbers[i]);
                
                    r = n1 - n2;
                }else{
                    n2 = parseInt(this.numbers[i]);
                    r = r - n2; 
                }
              }
            this.$emit('result', toString(r));
          }
          if(this.operation == "multiplication"){
              let r = 1;
              this.numbers.forEach(e => {
                var n = parseInt(e);
                r *= n;
            });
            this.$emit('result', toString(r));
          }
          if(this.operation == "division"){
              let l = this.numbers.length - 1;
              let r = 0;
              let n1, n2;
              for(let i = 1 ; i < l; i++){
                if(i == 1){
                    n1 = parseInt(this.numbers[i-1]);
                    n2 = parseInt(this.numbers[i]);
                
                    r = n1 / n2;
                }else{
                    n2 = parseInt(this.numbers[i]);
                    r = r / n2; 
                }
              }
            this.$emit('result', toString(r));
          }
          else{
            this.$emit('result', '0');
          }
      },
      addOperation: function(op){
        this.$emit('operation', op);
        let nums = this.numbers;
        nums.push(this.result);
        this.$emit('nums', nums);
        this.$emit('result', '0');
      },
      clear: function(){
          this.$emit('result','0');
      },
      printNumber: function(number){
          let Result = this.result;
          Result += number;
          this.$emit('result', Result);
      },
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
