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
                        <svg class="h-10 w-10 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                        </svg>
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
                                <dt class="text-sm font-medium leading-6 text-gray-900">Region</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ region }}</dd>
                            </div>
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">City</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ city }}</dd>
                            </div>    
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">Timezone</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ timezone }}</dd>
                            </div>                                                                                    
                            <div class="p-2 sm:grid sm:grid-cols-3 sm:gap-4 sm:px-0">
                                <dt class="text-sm font-medium leading-6 text-gray-900">ISP</dt>
                                <dd class="mt-1 text-sm leading-6 text-gray-700 sm:col-span-2 sm:mt-0">{{ isp }}</dd>
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
    region: {
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
  },
});
</script>