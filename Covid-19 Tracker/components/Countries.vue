<template>
  <div>
      
    <select
      @change="onChange()"
      v-model="selected"
      class="form-select mt-10 block w-full border p-3 rounded"
    >
      <option value="0">Select Country</option>
      <option
        v-for="(country, index) in countries"
        :value="country.ID"
        :key="index"
      >
        {{ country.Country }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: ["countries"],
  data(){
      return{
          selected: 0,
      }
  },
  methods: {
      onChange(event) {
        const country = this.countries.find((item) => item.ID === this.selected)
        
        console.log(country)
        this.$emit('getCountry', country)
      },
  }
};
</script>
