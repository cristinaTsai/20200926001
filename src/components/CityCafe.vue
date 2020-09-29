<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        {{ cityCode }}
        <v-select
          v-model="cityCode"
          :items="cities"
          item-value="code"
          item-text="name"
        />
      </v-col>
      <v-col cols="6">
        {{ regionCode }}
        <v-select
          v-model="regionCode"
          :items="regions"
          item-value="code"
          item-text="name"
        />
      </v-col>
    </v-row>

    <!--     <pre>
        {{JSON.stringify(zip, null, 2)}}
    </pre> -->
  </v-container>
</template>

<script>
import zip from "../zip.json";

export default {
  data: () => ({
    zip,
    cityCode: 100,
    regionCode: 0,
  }),
  computed: {
    cities() {
      return this.zip.cities;
    },
    regions() {
      const city = this.cities.find((elm) => elm.code === this.cityCode);
      return city.region;
    },
  },
  watch: {
    cityCode: {
      handler() {
        this.regionCode = this.regions[0].code;
      },
      immediate: true,
    },
  },
};
</script>

<style scoped>
</style>