<template>
  <main v-if="!loading" class="home">
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBoxes :stats=stats />
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching data
      <img :src="loadingImage" alt="hour glass GIF to show when loading" class="w-24 m-auto" />
    </div>
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle.vue'
import DataBoxes from '@/components/DataBoxes.vue'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif')

    }
  },
  methods: {
    async fetchCovidData() {
      // Fetch the summary data from the API
      const res = await fetch('http://127.0.0.1:8000/api/summary')
      // Parse the response to produce a JavaScript object
      const data = await res.json()
      // Return the JavaScript object
      return data
    }
  },
  async created() {
    // Once the application has fully loaded, fetch the summary data
    const data = await this.fetchCovidData()
    // Assign the internal variables to the data items on the JavaScript Object returned
    this.dataDate = data.date
    this.stats = data.global
    this.countries = data.countries
    // Application loading compete, set the loading status to false
    this.loading = false
  },
}
</script>
