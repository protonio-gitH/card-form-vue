<template>
<div class="wrapper" >
  <div  class="card-front">  
    <div class="front">
      <div class="card-mark"><img src="@/img/chip.png"></div>
      
      <div class="card-logo"><img :src="cardType" v-if="cardType"  alt=""></div>
      
      
      <div class="card-number">
        <label for="cardNumber" class="card-number__number">
          <span v-for="(n,$index) in defaultPlaceholder" :key="$index">
            
            <div
              class="card-item__numberItem"
                  :class="{ '-active' : n.trim() === '' }"
                  :key="defaultPlaceholder"
                  v-if="CardNumber.length > $index"
                >{{CardNumber[$index]}}</div>
            <div 
                  class="card-item__numberItem"
                  :class="{ '-active' : n.trim() === '' }"
                  v-else
                  :key="defaultPlaceholder + 1">{{ n}}</div>
          </span>
        
        </label>
      </div>
      <div class="card-item__content">
      <div class="cardHolder">
        
        <label for="cardName" class="card__info">
          
          <div class="card__holder">Card Holder</div>
          
          <div 
          class="card__name"
          v-if="FullName.length >0"
          >{{ FullName }}</div>
        
          <div v-else class="card__name">Full Name</div>
      </label>
    
      </div>
      <div class="card-expries">
        <label for="cardMonth" class="card-item__dateTitle">Expires</label>
        <label for="cardMonth" class="card-item__dateItem" >
          
          <span :key="Month" v-if="Month">{{ Month }}</span>
          <span v-else >MM</span>
          </label>
          /
        <label for="cardYear" class="card-item__dateItem">
        
          <span :key="Year" v-if="Year">{{ Year.slice(2,4) }}</span>
          <span v-else>YY</span>
        
      </label>
    </div>
    
  </div>
</div>

</div>
<div  class="card-back" >
    <div class="card-band"></div>
    <div class="card-cvv">
        <div class="card-cvvTitle">CVV</div>
        <div v-if="CVV"  class="card-cvvBand"><span v-for="n in CVV" >*</span></div>

        <div v-else class="card-cvvBand"></div>
    </div>
    <div class="card-type"><img :src="cardType"></div>
</div>
</div>

    
</template>

<script>

    export default {
      props:{
        CardNumber:{
          type:String,
          
        },
        FullName:{
          type:String
        },
        Year:{
          type:String
        },
        Month:{
          type:Number
        },
        CVV :{
          type:Number
        },
        isReverse:{
          type:Boolean,
          default:true
          
          
          
        }
      },
      data(){
        return{
          defaultPlaceholder:"#### #### #### ####",
          
          
          
        }
      },
      methods:{
        
        
        
      },
      computed: {
        cardType () {
          let number = this.CardNumber
          let re = new RegExp('^4')
          if (number.match(re) != null) return 'https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/visa.png'

          re = new RegExp('^5[1-5]')
          if (number.match(re) != null) return 'https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/mastercard.png'

          re = new RegExp('^2.')
          if (number.match(re) != null) return 'https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Mir-logo.SVG.svg/2560px-Mir-logo.SVG.svg.png'
          return 'https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/visa.png' 
        }
      
      }
    }
</script >

