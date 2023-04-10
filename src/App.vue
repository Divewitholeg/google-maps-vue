<script setup lang="ts">
import { GoogleMap, Marker, CustomMarker, InfoWindow, CustomControl } from 'vue3-google-map'

//Your location
const center = { lat: 59.40989085951935, lng: 24.643809184746956 }

//Your Google API key
const key = import.meta.env.VITE_GOOGLE_API_KEY

// Feature and Element types
// https://developers.google.com/maps/documentation/javascript/style-reference
const custom = [
  {
    featureType: 'all',
    elementType: 'all',
    stylers: [
      {
        saturation: -70
      }
    ]
  },
  {
    featureType: 'road',
    elementType: 'geometry',
    stylers: [
      {
        hue: '#ff0000'
      }
    ]
  },
  {
    featureType: 'landscape.man_made',
    elementType: 'fill',
    stylers: [
      {
        color: '#f9a8d4'
      }
    ]
  },
  {
    featureType: 'landscape.natural',
    elementType: 'fill',
    stylers: [
      {
        color: '#fce7f3'
      }
    ]
  },
  {
    featureType: 'poi.park',
    elementType: 'geometry',
    stylers: [
      {
        color: '#f472b6'
      }
    ]
  },
  {
    featureType: 'poi.attraction',
    elementType: 'geometry',
    stylers: [
      {
        color: '#f472b6'
      }
    ]
  },
  {
    featureType: 'water',
    elementType: 'geometry',
    stylers: [
      {
        color: '#d946ef'
      }
    ]
  },
  {
    featureType: 'poi.sports_complex',
    elementType: 'geometry',
    stylers: [
      {
        color: '#f472b6'
      }
    ]
  }
]

//Marker or CustomMarker options
const markerOptions = {
  position: center,
  anchorPoint: 'TOP_CENTER',
  label: 'Õ',
  title: 'Oleg Rõbnikov Web Development'
}

//Function to alert address and contacts
const alertAddress = () => {
  alert(
    `Oleg Rõbnikov Web Development

      Address:
      Õismäe tee 65-47
      13515 Tallinn
      Estonia

      Contacts:
      Tel: +372 5604 5484
      Email: oleg@rybnikov.online`
  )
}
</script>

<template>
  <div class="bg-pink-100 h-full w-full">
    <h1 class="text-3xl font-bold text-center p-5 text-fuchsia-950">
      Oleg Rõbnikov Web Development
    </h1>

    <GoogleMap
      :api-key="key"
      :styles="custom"
      style="width: 80%; height: 500px"
      class="mx-auto mt-[10vh] border-4 border-fuchsia-700 rounded"
      :center="center"
      :zoom="15"
    >
      <!-- <Marker :options="markerOptions">
        <InfoWindow>
          <article>
            <h1>Oleg Rõbnikov Web Development</h1>
            <h2>Address:</h2>
            <p>Õismäe tee 65-47</p>
            <p>13515 Tallinn</p>
            <p>Estonia</p>
            <h2>Contacts:</h2>
            <p>Tel: +372 5604 5484</p>
            <p>Email: oleg@rybnikov.online</p>
          </article>
        </InfoWindow>
      </Marker> -->
      <CustomMarker
        @click="alertAddress"
        :options="{ position: center, anchorPoint: 'TOP_CENTER' }"
      >
        <img src="@/assets/logo200black.svg" alt="Oleg Rõbnikov Web Development" />
      </CustomMarker>
      <CustomControl position="BOTTOM_CENTER">
        <a href="https://goo.gl/maps/wbDCkVD79FnrNQQA7" target="_blank">
          <img
            src="@/assets/sports-car-icon.svg"
            alt="Oleg Rõbnikov Web Development on Google Maps"
          />
        </a>
      </CustomControl>
    </GoogleMap>
  </div>
</template>
