<template>
  
  <CardFront :CVV="CVV" :Month="Month" :Year="Year" :CardNumber="CardNumber" :FullName="FullName"></CardFront>
<div class="card-form">
    <div class="card-form__inner">
        <div class="card-input">
          <label for="cardNumber" class="card-input__title">Card Number</label>
          <input :value="CardNumber" @input="addNumber" type="tel" maxlength="19" id="cardNumber" autocomplete="off" class="card-input__input">
        </div>
        <div class="card-input">
          <label for ="cardName" class="card-input__title">Card Name</label>
          <input type="text" id="cardName" autocomplete="off" class="card-input__input" :value="FullName" @input="addName">
        </div>
        <div class="card-form__row">
          <div class="card-form__col">
            <div class="card-form__group">
              <label for="cardMonth" class="card-input__title">Expiration Date</label>
              <select :value="Month" @change="changeMonth" class="card-input__input -select" id="cardMonth">
                <option value disabled="disabled" selected="selected">Month</option>
                <option 
                v-bind:value="n < 10 ? '0' + n : n"
                v-for="n in 12"
                v-bind:key="n">
                {{generateMonthValue(n)}}
                </option>
                
              </select>
              <select :value="Year" @change="changeYear" class="card-input__input -select" id="cardYear">
                <option value disabled="disabled" selected="selected">Year</option>
                <option 
                v-bind:value="$index + minCardYear"
                v-for="(n, $index) in 12"
                v-bind:key="n"
                >{{$index + minCardYear}}</option>
                
              </select>
            </div>
            <div class="card_form__col -cvv">
              <label for="cardCvv" class="card-input__title">CVV</label>
              <input :value="CVV" @input="addCVV" type="text" id="cardCvv" maxlength="3" autocomplete="off" class="card-input__input">
            </div>
            
          </div>
          <button class="card-form__button">Submit</button>
        </div>
    </div>
  </div>
</template>

<script>
import CardFront from "@/components/CardFront"

    export default {
      components:{
      CardFront
      },
      
        data(){
          return{
            CardNumber:'',
            FullName:'',
            minCardYear: new Date().getFullYear(),
            Month:'',
            Year:'',
            CVV:'',
            isReverse:false
            
          }
        },
        methods:{
          addNumber(event){
            
            event.target.value= event.target.value.replace(/[^0-9\s]/g, '');
            this.CardNumber=event.target.value
            if (event.inputType !== 'deleteContentBackward'){
              if (this.CardNumber.length=== 4 || this.CardNumber.length === 9 || this.CardNumber.length === 14){
                this.CardNumber = this.CardNumber+" "
              }
            }
            
          },
          addName(event){
              this.FullName=event.target.value
          },
          generateMonthValue (n) {
            return n < 10 ? `0${n}` : n
          },
          changeMonth(event){
            this.Month = event.target.value
          },
          changeYear(event){
            this.Year = event.target.value
          },
          addCVV(event){
            event.target.value= event.target.value.replace(/[^0-9]/g, '');
            this.CVV = event.target.value
          }
        
         
        }
    }
</script>
