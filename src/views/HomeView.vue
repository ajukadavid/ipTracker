<template>
  <div class="flex flex-col h-screen max-h-screen">
<!--    Search /Results -->
    <div class="flex justify-center bg-hero-pattern bg-cover relative px-4 pt-8 pb-32">

      <!--  Search Input -->
      <div class="w-full max-w-screen-sm">
        <h1 class="text-white text-center text-3xl pb-4">IP Address Tracker</h1>

        <div class="flex">
      <input type="text" class="flex-1 py-3 px-2 rounded-tl-md rounded-bl-md focus:outline-none"
        placeholder="Search for any IP address or leave it empty to get your ip info"
      />
          <i class="cursor-pointer bg-black text-white px-4 rounded-tr-md rounded-br-md flex items-center fas fa-chevron-right"></i>
        </div>
      </div>
      <IpInfo />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import IpInfo from '../components/IpInfo.vue'
export default {
  name: 'HomeView',
  components: {
    IpInfo
  }

}
</script>
