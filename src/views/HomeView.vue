<template>
  <div class="flex flex-col h-screen max-h-screen">
<!--    Search /Results -->
    <div class="z-20 flex justify-center bg-hero-pattern bg-cover relative px-4 pt-8 pb-32">

      <!--  Search Input -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text-white text-center text-3xl pb-4">IP Address Tracker</h1>

        <div class="flex">
      <input
          v-model="queryIp"
          type="text" class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
          placeholder="Search for any IP address or leave it empty to get your ip info"
      />
          <i class="cursor-pointer bg-black text-white px-4 rounded-tr-md rounded-br-md flex items-center fas fa-chevron-right"></i>
        </div>
      </div>
      <IpInfo v-if="ipInfo"/>
    </div>
<!--Map -->
    <div id="map" class="h-full z-10"></div>

  </div>
</template>

<script>
// @ is an alias to /src
import IpInfo from '../components/IpInfo.vue'
import leaflet from 'leaflet'
import { onMounted, ref} from "vue";
export default {
  name: 'HomeView',
  components: {
    IpInfo
  },
setup(){
  let myMap;
  const queryIp = ref("")
  const ipInfo = ref(null)
  onMounted(() => {
    myMap = leaflet.map('map').setView([51.505, -0.09], 13);


    leaflet.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=pk.eyJ1IjoiaXRoaWVsODMzIiwiYSI6ImNsMTVkeXU5cjB2cmszYm10eWEwd2h3dDUifQ.xFp4RAvn-s2moWsEmI-poQ', {
      attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
      maxZoom: 18,
      id: 'mapbox/streets-v11',
      tileSize: 512,
      zoomOffset: -1,
      accessToken: 'pk.eyJ1IjoiaXRoaWVsODMzIiwiYSI6ImNsMTVkeXU5cjB2cmszYm10eWEwd2h3dDUifQ.xFp4RAvn-s2moWsEmI-poQ'
    }).addTo(myMap);
  })

  return {
    queryIp,
    ipInfo
  }
}
}
</script>
