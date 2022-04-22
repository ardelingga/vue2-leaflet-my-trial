<template>
  <div id="app">
    <div style="height: 1000px; width: 100%">
      <l-map
        :zoom="zoom"
        :center="center"
        style="height: 100%"
      >
        <l-tile-layer
          :url="url"
          :attribution="attribution"
        />
        <l-marker :lat-lng="withPopup">
          <l-popup>
            <div>
              I am a popup
              <p v-show="showParagraph">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
                sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
                Donec finibus semper metus id malesuada.
              </p>
            </div>
          </l-popup>
        </l-marker>
        <l-marker :lat-lng="withTooltip">
          <l-tooltip :options="{ permanent: true, interactive: true }">
            <div>
              I am a tooltip
              <p v-show="showParagraph">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
                sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
                Donec finibus semper metus id malesuada.
              </p>
            </div>
          </l-tooltip>
        </l-marker>
      </l-map>
    </div>
  </div>
</template>

<script>
import { latLng } from "leaflet";
import { LMap, LTileLayer, LMarker, LPopup, LTooltip } from "vue2-leaflet";
import 'leaflet/dist/leaflet.css';

export default {
  name: "Example",
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LPopup,
    LTooltip
  },
  data() {
    return {
      zoom: 15,
      center: latLng(-6.200000, 	106.816666),
      // url: 'https://tile.thunderforest.com/cycle/{z}/{x}/{y}.png?apikey=b6523c316e8445a999f57b5aeeb18508', // Tile Layer URLs 1 OpenCycleMap
      url: 'https://tile.thunderforest.com/transport/{z}/{x}/{y}.png?apikey=b6523c316e8445a999f57b5aeeb18508', // Tile Layer URLs 2 Transport
      url: 'https://tile.thunderforest.com/landscape/{z}/{x}/{y}.png?apikey=b6523c316e8445a999f57b5aeeb18508', // Tile Layer URLs 3 Landscape
      // url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
      // attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
      attribution: 'Haritamiz',
      withPopup: latLng(-6.200000, 	106.816666),
      // withPopup: latLng(47.41322, -1.219482),
      // withTooltip: latLng(47.41422, -1.250482),
      currentZoom: 20,
      currentCenter: latLng(-6.200000, 	106.816666),
      showParagraph: false,
      // mapOptions: {
      //   zoomSnap: 0.5
      // },
      // showMap: true
    };
  },
  methods: {
    zoomUpdate(zoom) {
      this.currentZoom = zoom;
    },
    centerUpdate(center) {
      this.currentCenter = center;
    },
    showLongText() {
      this.showParagraph = !this.showParagraph;
    },
    innerClick() {
      alert("Click!");
    }
  }
};
</script>

<style>
</style>
