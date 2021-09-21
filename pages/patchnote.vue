<template>
  <v-container grid-list-md text-xs-center fluid>
    <v-card
      class="mt-16"
    >
      <v-card-title
        class="blue-grey white--text"
      >
        <span class="text-h6">更新日志</span>
        <v-spacer />
      </v-card-title>
      <v-card-text class="py-0">
        <v-timeline>
          <v-slide-x-reverse-transition
            group
            hide-on-leave
          >
            <v-timeline-item
              v-for="(item,id) in patch_notes"
              :key="id"
              :color="item.color"
              small
              fill-dot
            >
              <template #opposite>
                <span
                  :class="`headline font-weight-bold`"
                  v-text="item.date"
                />
              </template>
              <v-alert
                :value="true"
                :color="item.color"
                :icon="item.icon"
                class="white--text"
              >
                {{ item.content }}
              </v-alert>
            </v-timeline-item>
          </v-slide-x-reverse-transition>
        </v-timeline>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
const COLORS = [
  'info',
  'warning',
  'error',
  'success'
]
const ICONS = {
  info: 'mdi-information',
  warning: 'mdi-alert',
  error: 'mdi-alert-circle',
  success: 'mdi-check-circle'
}

export default {
  data: () => ({
    interval: null,
    items: [
      {
        id: 1,
        color: 'info',
        icon: ICONS.info
      }
    ],
    nonce: 2,
    patch_notes: [{
      version: '3.1.1',
      date: '2021.9.19',
      content: '靶场更新:修复有关靶场练习范围的bug',
      color: COLORS[0],
      icon: ICONS.info
    }, {
      version: '3.1.0',
      date: '2021.9.19',
      content: '更新了NKProtect 1.0b反作弊系统',
      color: 'info',
      icon: ICONS.info
    }
    ]
  }),

  beforeDestroy () {
    // this.stop()
  },

  methods: {
  }
}
</script>
