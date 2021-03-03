<template>
  <div class="container">
    <div class="columns has-text-centered is-mobile">
      <div class="column is-3 is-hidden-mobile"></div>
      <div class="column m-4">
        <div class="card-item">

          <!-- Brand name & Eye toggle Area -->
          <div class="columns p-5 is-mobile">
            <div class="column has-text-left">
              <img src="../assets/patricia-logo.png" alt="Patricia Logo" srcset="">
            </div>
            <div class="column has-text-right is-highted">
              <img v-if="!isMasked" v-on:click="maskCardNo" src="../assets/unmask-eye.png" alt="Show card no " srcset="">
              <img v-if="isMasked" v-on:click="loadCardNo" src="../assets/mask-eye.png" alt="Hide card no" srcset="">
            </div>
          </div>
          <!-- Card Number Area -->
          <div class="columns p-5 is-mobile pt-6 pb-6 ard">
            <div class="column has-text-left is-color-smoke">
             <span class="card-number mr-6"> {{cardNo.first}} </span>
             <span class="card-number mr-6 ml-4"> {{cardNo. second}} </span>
             <span class="card-number mr-6 ml-4"> {{cardNo.third}} </span>
             <span class="card-number ml-5"> {{cardNo.last}} </span>
            </div>
          </div>
          <!-- Card Holder & Date Area -->
          <div class="columns p-5 is-mobile is-color-smoke is-size-7">
            <div class="column is-5 has-text-left">
              Cardholder Name
            </div>
            <div class="column has-text-right">
              <span class="boxed-text"> VALID THRU</span> <span class="is-size-6 is-date-text"> 10/12 </span>

             <span class="ml-4"><sub> CVV</sub></span> <span class="is-size-6"> 455</span>
            </div>
          </div>

        </div>
      </div>
      <div class="column is-3 is-hidden-mobile"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  data() {
    return {
      isMasked: false,
      cardNo: {
        first: '',
        second: '',
        third: '',
        last: '',
      },
    };
  },
  created() {
    this.loadCardNo();
  },
  methods: {
    loadCardNo() {
      // assume credit card no received from API
      // array destructure card number for easy spaced display
      this.isMasked = false;
      const cCardNunber = '2345 6789 0123 4568';
      [this.cardNo.first, this.cardNo.second, this.cardNo.third, this.cardNo.last] = cCardNunber.split(' ');
    },
    maskCardNo() {
      this.isMasked = true;
      const cCardNunber = '•••• •••• •••• 4568';
      [this.cardNo.first, this.cardNo.second, this.cardNo.third, this.cardNo.last] = cCardNunber.split(' ');
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.columns {
  transition: height 2s linear;
}
.card-item {
  border-radius: 15px;
  border: 1px solid #131313;
  background-color: #131313;
  background-repeat: no-repeat;
  background-size: contain;
  background-image: url('../assets/patricia-bg.png');
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
}

.is-color-smoke {
  color: #D3DCE6;
}
.card-number {
  font-size: 1.6vw;
  letter-spacing: 2px;
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
}
.has-text-left {
  font-size: 1rem;
}
sub {
  vertical-align: baseline;
  font-size: 0.4rem;
  margin-right: 1em;
}
.boxed-text {
  display: inline-block;
  width: 20px;
  font-size: 0.4rem;
  text-align: left;
  padding-right: 0.2em;
}
.is-date-text {
  display: inline-block;
  padding-top: -10px;
}
.is-highted {
  height: 10px;
}

@media only screen and (max-width: 768px) {
  .card-number {
    font-size: 4vw;
    letter-spacing: 2px;
  }
  .mr-6 {
    margin-right: 0.8rem !important;
  }
  .ml-4 {
    margin-left: 0.4rem !important;
  }
  .p-5 {
    padding-top: 1rem !important;
    padding-bottom: 1rem !important;
  }
  .has-text-left {
    font-size: 0.6rem;
  }
}

</style>
