<template>
  <v-simple-table dark>
    <template #default>
      <thead>
        <tr>
          <th class="text-left">
            Name
          </th>
          <th class="text-left">
            Calories
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in leaderboard_data"
          :key="item.score"
        >
          <td>{{ item.name }}</td>
          <td>{{ item.score }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
export default {
  components: {},
  data () {
    return {
      loading: true,
      leaderboard_data: [],
      live_status: -1,
      live_title: '载入中'
    }
  },
  computed: {
  },
  async mounted () {
    await this.fetch_leaderboard_data()
  },
  methods: {
    async fetch_leaderboard_data () {
      const APIURL = '/api/score?type=1'
      await this.$axios
        .get(APIURL)
        .then((res) => {
          this.leaderboard_data = res.data.result
          console.log(this.leaderboard_data)
        })
        .catch((err) => {
          console.log(err)
        })
        .finally(() => {
          this.loading = false
        })
    }
  }
}
</script>
