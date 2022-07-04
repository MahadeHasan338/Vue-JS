<template>
  <header class="text-center bg-blue-800 text-white p-4 mb-10">
    <div class="text-3xl md:text-5xl font-bold mb-3">
      <font-awesome-icon :icon="['fas', 'virus-covid']" /> Covid-19 Tracker
    </div>

    <p>
      API by
      <a class="text-blue-300" href="https://covid19api.com" target="blank"
        >covid19api.com</a
      >
    </p>
  </header>
</template>

<script>
export default {
  props: ['header']
}
</script>
