.<template>
 <div class="card-back">
    <div class="card-band"></div>
    <div class="card-cvv">
        <div class="card-cvvTitle">CVV</div>
        <div class="card-cvvBand"></div>
    </div>
    <div class="card-type"><img src="@/img/visa.png"></div>
  </div>
</template>

<script>
export default {
   
}
</script>

<style scoped>
.card-back {
  display: flex;
  justify-content: flex-end;
  align-items: end;
  flex-direction: column;
  
  position: absolute;
  
  z-index: 2;
  width: 450px;
  height: 280px;
  background-color: blue;
  border-radius: 15px;
}
.card-band {
  height: 55px;
  width: 100%;
  background-color: black;
  margin-bottom: 20px;
  
}
.card-cvv {
  
}
.card-cvvTitle {
  text-align: right;
  padding-right: 15px;
  font-size: 15px;
  font-weight: 500;
  color: #fff;
  margin-bottom: 5px;
  margin-top: 5px;
  font-weight: 500;
}
.card-cvvBand {
  
  box-sizing: border-box;
  height: 40px;
  background-color: white;
  width: 420px;
  margin: 0 15px 0 15px;
  text-align: right;
  border-radius: 5px;
  padding:11px 10px 0 0;
  box-shadow: 0px 10px 20px -7px rgba(32, 56, 117, 0.35);
}
.card-type {
  margin-bottom: 20px;
  margin-right: 15px;
  margin-top: 15px;
}
.card-type img{
  
  opacity: 0.8;
  width: 70px;
  height: 50px;
  

}

</style>