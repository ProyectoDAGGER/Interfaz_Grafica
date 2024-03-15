<template>
  <q-page>
    <div
      style="
        background-color: gray;
        width: 10%;
        height: 30%;
        position: absolute;
        margin-left: 90%;
        text-align: right;
        padding: 0.3%;
        border-radius: 0 0 10px 10px;
      "
    >
      <!-- Botones en el lado derecho -->
      <q-btn
        flat
        icon="photo_camera"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        @click="accionBoton1"
        label="Camara"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="Ubicacion"
      />
      <q-btn
        flat
        icon="info"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="Informacion del drone dagger"
      />
    </div>
    <div
      style="
        background-color: gray;
        width: 10%;
        height: 55%;
        position: absolute;
        padding: 0.3%;
        border-radius: 0 0 10px 10px;
      "
    >
      <!-- Botones en el lado derecho -->
      <q-btn
        flat
        icon="photo_camera"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        @click="accionBoton1"
        label="Video"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="Bateria"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="Motores"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="radio"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="estructura del drone"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="Seguridad"
      />
      <q-btn
        flat
        icon="pin_drop"
        @click="accionBoton2"
        style="
          background-color: rgb(255, 255, 255);
          width: 100%;
          margin-bottom: 5%;
        "
        label="Parametros"
      />
    </div>

    <div id="map"></div>
  </q-page>
</template>

<script>
import mapboxgl from "mapbox-gl";

export default {
  mounted() {
    // Configura la clave de acceso de Mapbox
    mapboxgl.accessToken =
      "pk.eyJ1IjoiamxhcmExMjMiLCJhIjoiY2xzdXk2eGxqMmJrdjJxdGdxcG5nNTduZCJ9.-wQcOTVQSYzV_e0lCrauag";

    // Crea una instancia del mapa
    const map = new mapboxgl.Map({
      container: "map", // el ID del contenedor en tu template
      //style: 'mapbox://styles/mapbox/streets-v11', // puedes cambiar el estilo
      center: [-74.5, 40], // coordenadas iniciales del centro del mapa
      zoom: 9, // nivel de zoom inicial
    });

    // Obtén la ubicación actual del usuario
    navigator.geolocation.getCurrentPosition(
      (position) => {
        const { latitude, longitude } = position.coords;

        // Agrega un marcador en la ubicación actual
        console.log([longitude, latitude]);
        new mapboxgl.Marker().setLngLat([longitude, latitude]).addTo(map);

        // Centra el mapa en la ubicación actual
        map.flyTo({ center: [longitude, latitude], zoom: 13 });
      },
      (error) => {
        console.error("Error al obtener la ubicación:", error);
      }
    );
  },
};
</script>
<style scoped>
#map {
  height: 100vh;
  /* Establece la altura al 100% del viewport */
}
</style>
