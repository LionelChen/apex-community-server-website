<template>
  <div id="app">
    <v-app>
      <v-app-bar
        color="red accent-4"

        dark
        fixed
      >
        <v-app-bar-nav-icon />

        <v-toolbar-title>APEX社区服</v-toolbar-title>

        <v-spacer />

        <v-btn class="pa-2 ma-2" to="/leaderboard" router exact>
          排行榜
          <v-icon>{{ icons.leaderboard }}</v-icon>
        </v-btn>
        <v-btn class="pa-2 ma-2" to="/servers" router exact>
          服务器
          <v-icon>{{ icons.servers }}</v-icon>
        </v-btn>
        <v-btn class="pa-2 ma-2" to="/faq" router exact>
          常见问题
          <v-icon>{{ icons.faq }}</v-icon>
        </v-btn>
        <v-btn class="pa-2 ma-2" to="/patchnote" router exact>
          更新日志
          <v-icon>{{ icons.update_note }}</v-icon>
        </v-btn>

        <v-menu
          left
          bottom
        >
          <template #activator="{ on, attrs }">
            <v-btn
              icon
              v-bind="attrs"
              v-on="on"
            >
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
          </template>

          <v-list>
            <v-list-item
              v-for="n in 5"
              :key="n"
              @click="() => {}"
            >
              <v-list-item-title>Option {{ n }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </v-app-bar>
      <v-main>
        <v-container fluid class="page">
          <nuxt />
        </v-container>
        <v-footer
          :padless="true"
        >
          <v-card
            flat
            tile
            width="100%"
            class="red lighten-1 text-center"
          >
            <v-card-text>
              <v-btn
                v-for="icon in icons"
                :key="icon"
                class="mx-4"
                icon
              >
                <v-icon size="24px">
                  {{ icon }}
                </v-icon>
              </v-btn>
            </v-card-text>

            <v-divider />

            <v-card-text class="white--text">
              {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
            </v-card-text>
          </v-card>
        </v-footer>
      </v-main>
    </v-app>
  </div>
</template>

<script>
import {
  mdiPodiumGold,
  mdiFrequentlyAskedQuestions,
  mdiUpdate,
  mdiServerNetwork
} from '@mdi/js'

export default {
  data () {
    return {
      collapseOnScroll: true,
      icons: {
        leaderboard: mdiPodiumGold,
        faq: mdiFrequentlyAskedQuestions,
        update_note: mdiUpdate,
        servers: mdiServerNetwork
      }
    }
  }
}
</script>

<style lang="scss">
$blur-function: blur(3px);

.page {
  box-sizing: border-box;
  min-height: 100%;
  padding-bottom: 112px;
}

</style>
