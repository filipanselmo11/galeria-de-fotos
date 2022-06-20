<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Galeria de Fotos</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-fab vertical="bottom" horizontal="center" slot="fixed">
        <ion-fab-button @click="takePhoto()">
          <ion-icon :icon="camera"></ion-icon>
        </ion-fab-button>
      </ion-fab>
      <ion-grid>
        <ion-row>
          <ion-col size="6" :key="photo" v-for="photo in photos">
            <ion-img :src="photo.webviewPath"></ion-img>
          </ion-col>
        </ion-row>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { usePhotoGallery, UserPhoto } from "@/composables/usePhotoGallery";
import { defineComponent } from "vue";
import {
  IonPage,
  IonHeader,
  IonFab,
  IonFabButton,
  IonIcon,
  IonToolbar,
  IonTitle,
  IonContent,
  IonGrid,
  IonRow,
  IonCol,
  IonImg,
} from "@ionic/vue";
import { camera, trash, close } from "ionicons/icons";
// import ExploreContainer from '@/components/ExploreContainer.vue';

export default defineComponent({
  name: "Tab2Page",
  components: {
    IonPage,
    IonHeader,
    IonFab,
    IonFabButton,
    IonIcon,
    IonToolbar,
    IonTitle,
    IonContent,
    IonGrid,
    IonRow,
    IonCol,
    IonImg,
  },
  setup() {
    const { photos, takePhoto } = usePhotoGallery();
    return {
      photos,
      takePhoto,
      camera,
      trash,
      close,
    };
  },
});
</script>
