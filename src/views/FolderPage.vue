<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-menu-button color="primary"></ion-menu-button>
        </ion-buttons>
        <ion-title>{{ $route.params.id }}</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">{{ $route.params.id }}</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-item>
        <ion-label position="stacked">Date</ion-label>
        <ion-input type="date" v-model="receptionNote.date" required></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="stacked">Supplier</ion-label>
        <ion-select v-model="receptionNote.supplier_id" interface="popover">
          <ion-select-option v-for="supplier in suppliers" :key="supplier.id">{{ supplier.name }}</ion-select-option>
        </ion-select>
      </ion-item>

      <ion-item>
        <ion-label position="stacked">Source</ion-label>
        <ion-input type="text" v-model="receptionNote.source" required></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="stacked">Batch Cost</ion-label>
        <ion-input type="number" v-model="receptionNote.batch_cost" required></ion-input>
      </ion-item>

      <ion-item>
        <ion-label position="stacked">Picture</ion-label>
        <ion-input type="text" v-model="receptionNote.picture" placeholder="Enter image URL"></ion-input>
      </ion-item>

      <ion-button expand color="primary" @click="submitReceptionNote">Create Reception Note</ion-button>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel, IonInput, IonSelect, IonButton } from '@ionic/vue';

interface Supplier {
  id: number;
  name: string;
}

export default {
  data() {
    return {
      receptionNote: {
        date: "",
        supplier_id: null as number | null, // Optional supplier ID
        source: "",
        batch_cost: 0.0,
        picture: "",
      },
      suppliers: [{id: 1, name: "Ivan"}, {id: 2, name: "Renata"}, {id: 3, name: "Mladen"},{id: 4, name: "Other"}] as Supplier[], // Replace with your logic to fetch suppliers
    };
  },
  methods: {
    submitReceptionNote() {
      // Implement your logic to submit reception note data to your backend
      console.log("Submitting reception note:", this.receptionNote);
    },
  },
};


</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
