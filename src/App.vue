<template>
    <div class="container lg:flex md:flex mx-auto">
      <CityInformation 
          v-if="!isLoading"
          :ipAddress=ipAddressData 
          :city=cityData 
          :country=countryData 
          :countryCode=countryCodeData
          :isp=ispData :region=regionData :timezone=timezoneData 
        />

      <Map :latitute=latituteData :longitude=longitudeData :isLoading=isLoading />
    </div>

</template>

<script lang="ts">
import { defineComponent } from "vue";

import Map from './components/Map.vue'
import CityInformation from './components/CityInformation.vue'

export default defineComponent({
  data() {
    return {
      isLoading: false,
      ipAddressData: String,
      latituteData: Number,
      longitudeData: Number,
      cityData: String,
      countryData: String,
      countryCodeData: String,
      ispData: String,
      regionData: String,
      timezoneData: String
    }
  },
  methods: {
    async getData() {
      this.isLoading = true
      const result = await fetch("http://ip-api.com/json/");
      const res = await result.json();
      this.latituteData = res.lat
      this.longitudeData = res.lon
      this.ipAddressData = res.query
      this.cityData = res.city
      this.countryData = res.country
      this.countryCodeData = res.countryCode
      this.ispData = res.isp
      this.regionData = res.regionName
      this.timezoneData = res.timezone
      this.isLoading = false
    }
  },
  mounted() {
    this.getData()
  },

  components: {
    Map,
    CityInformation
  }
});
</script>

<style scoped></style>
