<template>

    <form @submit.prevent="putNameCity">
     <ion-item>
      <ion-label position="floating">Saisir le nom d'une ville</ion-label>
      <ion-input  v-model="nameCity"></ion-input>
    </ion-item>
    </form>
</template>

<script>
import {IonItem, IonInput, IonLabel } from '@ionic/vue';
import axios from "axios";
export default {
  data(){
    return{
      nameCity : "",
      weather : ""
    }
  },
  name: 'Search',
  components: {
      IonLabel,
      IonInput,
      IonItem,
      
  },
  methods: {

    putNameCity(){
      let openWeatherMap = {
        key: "729172fe143c7159f66492956582b6a1",
      }

      axios
        .get("https://api.openweathermap.org/data/2.5/weather?q=" + this.nameCity +"&appid="+ openWeatherMap.key +"&lang=fr&units=metric")
        .then((response) => {
            this.weather = response.data;
            console.log(this.weather);
            this.$bus.emit("weather", this.weather);
        })
        .catch((error) => {
          console.log(error);
          const toast = document.createElement('ion-toast');
          toast.message = "Merci d'enter le nom d'une ville valide";
          toast.duration = 4000;
          toast.color = "danger";
          document.body.appendChild(toast);
          return toast.present();
        })
    },
  }
}
</script>
