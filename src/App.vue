<template>
  <div class="container lg:flex md:flex mx-auto">
    <CityInformation v-if="!isLoading" 
      :ipAddress=ipAddressData 
      :city=cityData 
      :country=countryData
      :countryCode=countryCodeData 
      :isp=ispData 
      :timezone=timezoneData 
      :zipcode=zipcodeData
      :organization=organizationData 
      :countryFlag=countryFlagData />

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
      isError: false,
      ipAddressData: String,
      latituteData: Number,
      longitudeData: Number,
      cityData: String,
      countryData: String,
      countryCodeData: String,
      ispData: String,
      timezoneData: String,
      zipcodeData: String,
      organizationData: String,
      countryFlagData: String

    }
  },
  methods: {
    async getData() {
      this.isLoading = true
      try {
        const response = await fetch(`https://api.ipgeolocation.io/ipgeo?apiKey=${import.meta.env.VITE_API_GEOLOCATION}`)
        const result = await response.json()

        console.log('result.country_flag', result.country_flag)

        this.latituteData = result.latitude
        this.longitudeData = result.longitude
        this.ipAddressData = result.ip
        this.cityData = result.city
        this.countryData = result.country_name
        this.countryCodeData = result.country_code2
        this.ispData = result.isp
        this.timezoneData = result.time_zone.name
        this.zipcodeData = result.zipcode
        this.organizationData = result.organization
        this.countryFlagData = result.country_flag

      } catch (err) {
        console.log(err)
        this.isError= true
      }
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
