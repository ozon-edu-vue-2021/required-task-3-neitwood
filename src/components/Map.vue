<template>
  <div class="map">
    <h3>Карта офиса</h3>

    <div v-if="!isLoading" class="map-root">
      <!-- map -->
      <MapSvg />
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import MapSvg from "../assets/images/map.svg";

export default {
  data() {
    return {
      isLoading: false,
    };
  },
  components: {
    MapSvg,
  },
};
</script>

<style scoped>
.map {
  height: 100%;
  width: 100%;
  padding: 24px;
  overflow: hidden;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
}

.map-root {
  height: 100%;
  width: 100%;
  overflow: hidden;
  box-sizing: border-box;
}

h3 {
  margin-top: 0;
}

::v-deep svg {
  height: 100%;
  width: 100%;
}
</style>
