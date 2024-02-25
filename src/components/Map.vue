<template>
  <div class="
    w-full
    bg-gray-50 
    flex flex-col 
    justify-center 
    relative overflow-hidden lg:py-12 md:py-12 py-4">
    <div class="max-w-7xl mx-auto">
      <div class="relative group">
        <div class="
          relative p-4 
          bg-white ring-1 
          ring-gray-900/5 
          rounded-lg leading-none flex items-top justify-start">
          <div id="mapContainer" class="lg:h-[80vh] md:w-[110vh] h-80 w-96"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

import * as L from "leaflet";
import "leaflet/dist/leaflet.css";
import "@geoman-io/leaflet-geoman-free";
import "@geoman-io/leaflet-geoman-free/dist/leaflet-geoman.css";

export default defineComponent({
  name: "Map",
  props: {
    latitute: {
      type: Number,
      required: true,
    },
    longitude: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      map: null,
    };
  },
  methods: {
    setMapView() {

      var map = L.map("mapContainer").setView([this.latitute, this.longitude], 11);
      L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
        attribution:
          '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      }).addTo(map);

      const svgIcon = L.divIcon({
        html: `
      <svg
        width="24"
        height="40"
        viewBox="0 0 100 100"
        version="1.1"
        preserveAspectRatio="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path d="M0 0 L50 100 L100 0 Z" fill="#7A8BE7"></path>
      </svg>`,
        className: "",
        iconSize: [24, 40],
        iconAnchor: [12, 40],
      });

      L.marker([this.latitute, this.longitude], { icon: svgIcon }).addTo(map);

      map.pm.addControls({
        position: 'topleft',
        drawCircleMarker: false,
        rotateMode: false,
      });

      map.pm.addControls({
        drawControls: true,
        editControls: false,
        optionsControls: true,
        customControls: true,
        oneBlock: false,
      });

      map.pm.Toolbar.changeControlOrder([
        "drawCircle",
        "drawRectangle",
        "removalMode",
        "editMode",
      ]);
    }
  },
  watch: {
    latitute: function () {
      this.setMapView();
    },
    longitude: function () {
      this.setMapView();
    }
  },
});
</script>

<style