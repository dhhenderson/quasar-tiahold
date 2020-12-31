<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          <router-link
            style="text-decoration: none; color: inherit;"
            to="/">TIAHOLD
          </router-link>
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item to="/tindoz" exact>
          <q-item-section avatar>
            <q-icon name="construction" />
          </q-item-section>
          <q-item-section>
            <q-item-label>TINDOZ</q-item-label>
            <q-item-label caption>
              website in progress
            </q-item-label>
          </q-item-section>
        </q-item>

        <q-item-label
          header
          class="text-grey-8"
        >
          External Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container class="bg-grey-13">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'TIAHOLD Video',
    caption: 'Youtube clip',
    icon: 'movie',
    link: 'https://www.youtube.com/watch?v=hh1oaumUoyc&feature=emb_logo'
  },
  {
    title: 'TINDOZ Video',
    caption: 'Youtube clip',
    icon: 'movie',
    link: 'https://www.youtube.com/watch?v=lg7MAacSPNM'
  }
]

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
