<template>
  <div>
      {{cityCode}}
    <select v-model="cityCode">
      <option v-for="city in cities" :key="city.code" :value="city.code">
        {{ city.name }}
      </option>
    </select>
     <select v-model="regionCode">
       <option v-for="region in regions" :key="region.code" :value="region.code">
        {{ region.name }}
      </option>       
    </select>
    <!--     <pre>
        {{JSON.stringify(zip, null, 2)}}
    </pre> -->
  </div>
</template>



<script>
import zip from "../zip.json";

export default {
  data: () => ({
    zip,
    cityCode: 100,
  }),
  computed: {
    cities() {
      return this.zip.cities;
    },
    regions() {
      return [];
    },
  },
};
</script>

<style scoped>
</style>