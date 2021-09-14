<template>
  <v-simple-table dark class="mt-16">
    <template #default>
      <thead>
        <tr>
          <th class="text-left">
            服务器名称
          </th>
          <th class="text-left">
            地图
          </th>
          <th class="text-left">
            游戏模式
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in online_server_data"
          :key="item.name"
        >
          <td>{{ item.name }}</td>
          <td>{{ MAPS_TABLE[item.map] }}</td>
          <td>{{ MODE_TABLE[item.gamemode] }}</td>
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
      online_server_data: [],
      live_status: -1,
      live_title: '载入中',
      MODE_TABLE: {
        survival: '大逃杀',
        custom_tdm: '死斗',
        survival_dev: '开发模式',
        survival_firingrange: '射击场',
        gungame: '军备竞赛'
      },
      MAPS_TABLE: {
        mp_rr_desertlands_64k_x_64k_nx: '夜晚世界边缘',
        mp_rr_desertlands_64k_x_64k: '世界边缘',
        mp_rr_canyonlands_mu1: '诸王峡谷(第2赛季)',
        mp_rr_canyonlands_mu1_night: '夜晚诸王峡谷',
        mp_rr_canyonlands_64k_x_64k: '诸王峡谷(第0赛季)',
        mp_rr_canyonlands_staging: '靶场',
        mp_lobby: '大厅'
      }
    }
  },
  computed: {
  },
  async mounted () {
    await this.fetch_online_server_data()
  },
  methods: {
    async fetch_online_server_data () {
      const APIURL = '/api/servers?version=beta%201.5'
      await this.$axios
        .get(APIURL)
        .then((res) => {
          this.online_server_data = res.data.servers
          console.log(this.online_server_data)
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
