<template>
  <v-layout column justify-center align-center app mt-16>
    <v-container grid-list-md text-xs-center fluid pa-0>
      <v-layout row wrap>
        <v-flex id="landing" xs12 class="px-0 text-h1" style="height: 100vh;">
          <v-container fill-height fluid>
            <v-row
              align="center"
              justify="center"
            >
              <v-col>
                <p
                  class="header text-center"
                >
                  APEX社区服务器
                </p>
                <v-col />
              </v-col>
            </v-row>
            <v-row
              align="center"
              justify="center"
            >
              <a href="#works_top">
                <v-btn
                  elevation="2"
                >
                  <v-icon>{{ icons.down_arrow }}</v-icon>
                </v-btn>
              </a>
            </v-row>
          </v-container>
        </v-flex>
        <v-flex id="works_top" xs12 class="px-0" style="height: 40vh">
          <v-container fill-height fluid>
            <v-row
              align="center"
              justify="center"
            >
              <v-col>
                <p
                  class="header text-center white--text"
                  style="font-size: 50px"
                >
                  公告
                </p>
                <v-col />
              </v-col>
            </v-row>
          </v-container>
        </v-flex>
        <v-flex id="works_content" xs12 class="pt-0 mb-5" style="height: 80vh">
          <v-container fill-height fluid class="pl-10 pr-10">
            <v-row
              align="center"
              justify="center"
            >
              <v-flex xs4 pa-2>
                <section style="height: 80vh;">
                  <v-card-text class="px-0">
                    <v-flex>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <img src="/team_1.jpg" alt="">
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <p style="font-size: 25px" class="pt-10 pb-5">
                          立即下载
                        </p>
                      </v-row>
                      <v-divider />
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <a
                          href="https://apexdownload.bk201.icu/"
                          style="font-size: 25px"
                          class="pt-10 pb-5"
                        >
                          云盘链接
                        </a>
                      </v-row>
                    </v-flex>
                  </v-card-text>
                </section>
              </v-flex>
              <v-flex xs4 pa-2>
                <section style="height: 80vh;">
                  <v-card-text class="px-0">
                    <v-flex>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <img src="/team_2.jpg" alt="">
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <p style="font-size: 25px" class="pt-10 pb-5">
                          更新日志
                        </p>
                      </v-row>
                      <v-divider />
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <p style="font-size: 20px" class="pt-10 pb-5">
                          版本号: {{ latest_patch.version }}, 更新日期: {{ latest_patch.date }}
                        </p>
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <p style="font-size: 20px">
                          {{ latest_patch.content }}
                        </p>
                      </v-row>
                    </v-flex>
                  </v-card-text>
                </section>
              </v-flex>
              <v-flex xs4 pa-2>
                <section style="height: 80vh;">
                  <v-card-text class="px-0">
                    <v-flex>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <img src="/team_3.jpg" alt="">
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <p style="font-size: 25px" class="pt-10 pb-5">
                          近期开发目标
                        </p>
                      </v-row>
                      <v-divider />
                    </v-flex>
                  </v-card-text>
                </section>
              </v-flex>
            </v-row>
          </v-container>
        </v-flex>

        <v-flex id="contact_top" xs12 class="px-0" style="height: 40vh">
          <v-container fill-height fluid>
            <v-row
              align="center"
              justify="center"
            >
              <v-col>
                <p
                  class="header text-center white--text"
                  style="font-size: 50px"
                >
                  联系我们
                </p>
                <v-col />
              </v-col>
            </v-row>
          </v-container>
        </v-flex>

        <v-flex id="contact" xs12 class="px-0" style="height: 80vh">
          <v-container fill-height fluid class="pl-10 pr-10">
            <v-row
              align="center"
              justify="center"
            >
              <v-flex xs4 pa-2>
                <section style="height: 80vh;">
                  <v-card-text class="px-0">
                    <v-flex>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <img src="/team_1.jpg" alt="">
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <p style="font-size: 25px" class="pt-10 pb-5">
                          社交账号
                        </p>
                      </v-row>
                      <v-divider />
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <a
                          href="https://space.bilibili.com/694820807"
                          style="font-size: 25px"
                          class="pt-10 pb-5"
                        >
                          Bilibili
                        </a>
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <a
                          href="https://kaihei.co/WFfWRm"
                          style="font-size: 25px"
                          class="pt-10 pb-5"
                        >
                          开黑啦
                        </a>
                      </v-row>
                      <v-row
                        align="center"
                        justify="center"
                      >
                        <a
                          href=""
                          style="font-size: 25px"
                          class="pt-10 pb-5"
                        >
                          QQ群：959166167
                        </a>
                      </v-row>
                    </v-flex>
                  </v-card-text>
                </section>
              </v-flex>
            </v-row>
          </v-container>
        </v-flex>
      </v-layout>
    </v-container>
  </v-layout>
</template>

<script>
import {
  mdiPodiumGold,
  mdiFrequentlyAskedQuestions,
  mdiUpdate,
  mdiChevronTripleDown
} from '@mdi/js'

export default {
  data () {
    return {
      collapseOnScroll: true,
      icons: {
        leaderboard: mdiPodiumGold,
        faq: mdiFrequentlyAskedQuestions,
        update_note: mdiUpdate,
        down_arrow: mdiChevronTripleDown
      },
      latest_patch: {
        version: '3.1.1',
        date: '2021.9.19',
        content: '靶场更新:修复有关靶场练习范围的bug'
      }
    }
  }
}
</script>

<style>

html{
  scroll-behavior: smooth;
}

#landing{
  background: url('/loader.png');
  background-repeat: no-repeat;
  background-size: cover;
}

#works_top {
  /* The image used */
  background-image: url("/works_bg.jpg");

  /* Full height */
  height: 100%;

  /* Create the parallax scrolling effect */
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

#contact_top {
  /* The image used */
  background-image: url("/gallery_bg.jpg");

  /* Full height */
  height: 100%;

  /* Create the parallax scrolling effect */
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
