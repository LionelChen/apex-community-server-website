<template>
  <v-simple-table dark class="mt-16">
    <template #default>
      <thead>
        <tr>
          <th class="text-left">
            段位
          </th>
          <th class="text-left">
            排名
          </th>
          <th class="text-left">
            ID
          </th>
          <th class="text-left">
            分数
          </th>
          <th class="text-left">
            命中率
          </th>
          <th class="text-left">
            使用武器
          </th>
          <th class="text-left">
            上传时间
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(item, index) in leaderboard_data"
          :key="item.score"
        >
          <td>{{ item.rankTier }}</td>
          <td>{{ index+1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.score }}</td>
          <td>{{ item.accurate }}</td>
          <td>{{ item.weapon }}</td>
          <td>{{ item.updateTime }}</td>
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
