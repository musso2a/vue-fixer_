<template>

  <form @submit.prevent="putCurrency">
  <ion-item>
    <ion-label>Amount</ion-label>
    <ion-input placeholder="EUR" type="number" v-model="euroAmount"></ion-input>
  </ion-item>

  <ion-item>
    <ion-label>Currrency</ion-label>
    <ion-select interface="popover" id="v-for-list">
      <ion-select-option >test</ion-select-option>

    </ion-select>
  </ion-item>
    <ion-button expand="block">Convert</ion-button>
  </form>
</template>

<script>

import { IonLabel, IonInput, IonItem, IonSelectOption, IonSelect , IonButton} from '@ionic/vue';

import axios from "axios";
export default {
  el: '#v-for-list',
  data() {
    return {
      currencyList: [],
      conversion: "",
      euroAmount: "",
    }
  },
  name: 'Search',
  components: {
    IonLabel,
    IonInput,
    IonItem,
    IonSelectOption,
    IonSelect,
    IonButton

  },
  methods: {

    putCurrency() {

        axios
            .get(`http://data.fixer.io/api/symbols?access_key=${process.env.VUE_APP_API_KEY}` )
            .then((response) => {
              console.log(this.euroAmount);
              this.currencyList = response.data;
              console.log(this.currencyList);
            })
            .catch((error) => {
              console.log(error);

            })
      },
    }

}
</script>

<style scoped>

</style>