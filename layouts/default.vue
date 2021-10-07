<template>
  <div id="app" style="min-height: 100vh;">
    <v-app>
      <v-main>
        <v-container fluid class="page" pa-0>
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
              {{ new Date().getFullYear() }} — <strong>APEX社区服</strong>
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
  mdiServerNetwork,
  mdiQqchat,
  mdiHome
} from '@mdi/js'

export default {
  data () {
    return {
      collapseOnScroll: true,
      icons: {
        leaderboard: mdiPodiumGold,
        faq: mdiFrequentlyAskedQuestions,
        update_note: mdiUpdate,
        servers: mdiServerNetwork,
        qq_chat: mdiQqchat,
        home_icon: mdiHome
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
