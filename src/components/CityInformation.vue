<template>
    <div class="
    lg:w-96 md:w-96
    bg-gray-50 
    relative overflow-hidden lg:py-12 md:py-12 m-2 px-2">
        <div class="max-w-7xl mx-auto">
            <div class="relative group">
                <div class="h-auto
                        relative p-4
                        bg-white ring-1 
                        ring-gray-900/5 
                        rounded-lg leading-none justify-start">
                    <div class="flex items-center">
                        <img 
                        class="h-7 w-auto" 
                        :src="countryFlag" />
                        <div class="ml-2">
                            <h3 class="text-lg text-gray-800  font-medium">{{ ipAddress }} ({{ countryCode }})</h3>
                        </div>
                    </div>
                    <div>

                    <div class="mt-6 border-t border-gray-100">
                        <dl class="divide-y divide-gray-100">
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">Country</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ country }}</dd>
                            </div>
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">City</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ city }}</dd>
                            </div>  
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">Zip Code</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ zipcode }}</dd>
                            </div>                                
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">Timezone</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ timezone }}</dd>
                            </div>                                                                                    
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">ISP</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ isp }}</dd>
                            </div>  
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">Organization</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ organization }}</dd>
                            </div>                                                                                                                                            
                        </dl>
                    </div>
                </div>

                </div>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: "CityInformation",
  props: {
    ipAddress: {
      type: String,
      required: true,
    },
    countryCode: {
      type: String,
      required: true,
    },
    country: {
      type: String,
      required: true,
    },
    city: {
      type: String,
      required: true,
    },
    timezone: {
      type: String,
      required: true,
    },
    isp: {
      type: String,
      required: true,
    },        
    zipcode: {
      type: String,
      required: true,
    },
    organization: {
      type: String,
      required: true,
    },
    countryFlag: {
      type: String,
      required: true,
    },            
  },
});
</script>
