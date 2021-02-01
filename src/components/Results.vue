<template>
  <ion-card>
    <img src="" />
    <ion-card-header>
      <ion-card-subtitle>test</ion-card-subtitle>
      <ion-card-title>test</ion-card-title>
    </ion-card-header>
    <ion-card-content>
      test
    </ion-card-content>
  </ion-card>
</template>

<script>

import { IonCardHeader, IonCardSubtitle, IonCardTitle , IonCard, IonCardContent} from '@ionic/vue';


export default {
  name: "Results",
  components: {
    IonCard,
    IonCardContent,
    IonCardTitle,
    IonCardSubtitle,
    IonCardHeader
  }
}
</script>

<style scoped>

ion-card {
  --ion-safe-area-top: 10px;
  --ion-safe-area-bottom: 12px;
}

</style>