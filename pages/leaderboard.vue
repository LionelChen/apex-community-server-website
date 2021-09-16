<template>
  <v-simple-table
    dark
    class="mt-16"
    loading
    loading-text="Loading... Please wait"
  >
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
          <td>
            <div
              :class="(item.rankTier=='APEX_PREDATOR') ? 'APEX_PREDATOR_USER_NAME' : ''"
              :data-text="item.name"
            >
              {{ item.name }}
            </div>
          </td>
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

.APEX_PREDATOR_USER_NAME {
  color: white;
  position: relative;
  width: 400px;
  margin-left: 0;
}

@keyframes noise-anim {
  0% {
    clip-path: inset(30% 0 3% 0);
  }
  5% {
    clip-path: inset(19% 0 57% 0);
  }
  10% {
    clip-path: inset(38% 0 33% 0);
  }
  15% {
    clip-path: inset(49% 0 19% 0);
  }
  20% {
    clip-path: inset(52% 0 3% 0);
  }
  25% {
    clip-path: inset(1% 0 36% 0);
  }
  30% {
    clip-path: inset(38% 0 53% 0);
  }
  35% {
    clip-path: inset(27% 0 74% 0);
  }
  40% {
    clip-path: inset(49% 0 1% 0);
  }
  45% {
    clip-path: inset(18% 0 25% 0);
  }
  50% {
    clip-path: inset(91% 0 1% 0);
  }
  55% {
    clip-path: inset(100% 0 1% 0);
  }
  60% {
    clip-path: inset(87% 0 10% 0);
  }
  65% {
    clip-path: inset(39% 0 52% 0);
  }
  70% {
    clip-path: inset(26% 0 62% 0);
  }
  75% {
    clip-path: inset(32% 0 58% 0);
  }
  80% {
    clip-path: inset(9% 0 74% 0);
  }
  85% {
    clip-path: inset(91% 0 2% 0);
  }
  90% {
    clip-path: inset(95% 0 3% 0);
  }
  95% {
    clip-path: inset(12% 0 32% 0);
  }
  100% {
    clip-path: inset(45% 0 52% 0);
  }
}
.APEX_PREDATOR_USER_NAME::after {
  content: attr(data-text);
  position: absolute;
  left: 2px;
  text-shadow: -1px 0 red;
  top: 0;
  color: white;
  background: rgb(30, 30, 30);
  overflow: hidden;
  animation: noise-anim 5s infinite linear alternate-reverse;
}

@keyframes noise-anim-2 {
  0% {
    clip-path: inset(28% 0 45% 0);
  }
  5% {
    clip-path: inset(9% 0 35% 0);
  }
  10% {
    clip-path: inset(79% 0 7% 0);
  }
  15% {
    clip-path: inset(87% 0 11% 0);
  }
  20% {
    clip-path: inset(4% 0 22% 0);
  }
  25% {
    clip-path: inset(2% 0 64% 0);
  }
  30% {
    clip-path: inset(17% 0 3% 0);
  }
  35% {
    clip-path: inset(14% 0 71% 0);
  }
  40% {
    clip-path: inset(49% 0 24% 0);
  }
  45% {
    clip-path: inset(93% 0 3% 0);
  }
  50% {
    clip-path: inset(23% 0 56% 0);
  }
  55% {
    clip-path: inset(7% 0 22% 0);
  }
  60% {
    clip-path: inset(20% 0 47% 0);
  }
  65% {
    clip-path: inset(96% 0 4% 0);
  }
  70% {
    clip-path: inset(23% 0 9% 0);
  }
  75% {
    clip-path: inset(37% 0 60% 0);
  }
  80% {
    clip-path: inset(83% 0 15% 0);
  }
  85% {
    clip-path: inset(32% 0 5% 0);
  }
  90% {
    clip-path: inset(49% 0 33% 0);
  }
  95% {
    clip-path: inset(20% 0 75% 0);
  }
  100% {
    clip-path: inset(11% 0 89% 0);
  }
}
.APEX_PREDATOR_USER_NAME::before {
  content: attr(data-text);
  position: absolute;
  left: -2px;
  text-shadow: 1px 0 blue;
  top: 0;
  color: white;
  background: rgb(30, 30, 30);
  overflow: hidden;
  animation: noise-anim-2 30s infinite linear alternate-reverse;
}

</style>
