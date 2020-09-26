<template>
  <div>
    <div v-if="zip">
      {{ cityCode }}
      <select v-model="cityCode">
        <option v-for="city in cities" :key="city.code" :value="city.code">
          {{ city.code }} {{ city.name }}
        </option>
      </select>
      <br />
      {{ regionCode }}
      <select v-model="regionCode">
        <option
          v-for="region in regions"
          :key="region.code"
          :value="region.code"
        >
          {{ region.code }} {{ region.name }}
        </option>
      </select>
    </div>
    <!--     <pre>
        {{JSON.stringify(zip, null, 2)}}
    </pre> -->
    <div v-else>
      Loading...
      <button @click="getData">GET</button>
    </div>
  </div>
</template>



<script>
// import zip from "../zip.json";

export default {
  data: () => ({
    zip: null,
    cityCode: 0,
    regionCode: 0,
  }),
  computed: {
    cities() {
      return this.zip ? this.zip.cities : [];
      // if (this.zip) {
      //   return this.zip.cities;
      // } else {
      //   return [];
      // }
    },
    regions() {
      const city = this.cities.find((elm) => elm.code === this.cityCode);
      return city ? city.region : [];
      // if (city) {
      //   return city.region;
      // } else {
      //   return [];
      // }
    },
  },
  mounted() {
    this.getData();
  },
  watch: {
    cities() {
      const city = this.cities[0];
      this.cityCode = city ? city.code : 0;
    },
    regions() {
      const region = this.regions[0];
      this.regionCode = region ? region.code : 0;
    },
  },
  methods: {
    async getData() {
      //$get
      //axios
      const result = await fetch("http://10.2.1.46/");
      const zip = await result.json();
      zip.cities.sort((a, b) => a.code - b.code)
      this.zip = zip;
      console.log(zip);
    },
    // getData() {
    //   fetch("http://10.2.1.46/")
    //     .then((result) => result.json())
    //     .then((zip) => {
    //       this.zip = zip;
    //     });
    // },
  },
};
</script>

<style scoped>
</style>