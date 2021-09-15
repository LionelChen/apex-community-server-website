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
          :key="index"
        >
          <td :class="item.rankTier" style="text-align: center;">
                {{ RANK_TIER_TABLE[item.rankTier] }}
          </td>
          <td>{{ index+1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.score }}</td>
          <td>{{ item.accurate }}</td>
          <td>{{ WEAPON_TABLE[item.weapon] }}</td>
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
      live_title: '载入中',
      WEAPON_TABLE: {
        mp_weapon_alternator_smg: '转换者冲锋枪',
        mp_weapon_defender: '充能步枪',
        mp_weapon_esaw: '专注轻机枪',
        mp_weapon_shotgun: 'EVA8霰弹枪',
        mp_weapon_vinson: 'VK-47平行步枪',
        mp_weapon_g2: 'G7侦查步枪',
        mp_weapon_energy_ar: '哈沃克步枪',
        mp_weapon_hemlok: '赫姆洛克连发步枪',
        mp_weapon_sniper: '克雷贝尔狙击枪',
        mp_weapon_dmr: '长弓DMR狙击枪',
        mp_weapon_lstar: 'L-Star轻机枪',
        mp_weapon_mastiff: '獒犬霰弹枪',
        mp_weapon_shotgun_pistol: '莫桑比克霰弹枪',
        mp_weapon_semipistol: 'P2020',
        mp_weapon_energy_shotgun: '和平捍卫者霰弹枪',
        mp_weapon_pdw: '猎兽冲锋枪',
        mp_weapon_rspn101: 'R-301自动步枪',
        mp_weapon_r97: 'R-99冲锋枪',
        mp_weapon_autopistol: 'RE-45',
        mp_weapon_lmg: '喷火轻机枪',
        mp_weapon_doubletake: '三重击狙击枪',
        mp_weapon_wingman: '辅助手枪',
        mp_weapon_melee_survival: '近战攻击'
      },
      RANK_TIER_TABLE: {
        BRONZE: '青铜',
        SILVER: '白银',
        GOLD: '黄金',
        PLATINUM: '铂金',
        DIAMOND: '钻石',
        MASTER: '大师',
        PREDATOR: '猎杀者',
        APEX_PREDATOR: '顶尖猎杀者'
      },
      RANK_TIER_ICON_TABLE: {
        BRONZE: 'Ranked_Tier1_Bronze.png',
        SILVER: 'Ranked_Tier2_Silver.png',
        GOLD: 'Ranked_Tier3_Gold.png',
        PLATINUM: 'Ranked_Tier4_Platinum.png',
        DIAMOND: 'Ranked_Tier5_Diamond.png',
        MASTER: 'Ranked_Tier6_Master.png',
        PREDATOR: 'Ranked_Tier7_Apex_Predator.png',
        APEX_PREDATOR: 'Ranked_Tier7_Apex_Predator.png'
      }
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
          // console.log(this.leaderboard_data)
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

<style scoped>
.APEX_PREDATOR{
  background: url('/test.gif');
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  max-height: 50px;
}
</style>
