<template>
  <q-layout view="lHr lpR fFf" class="main-my-view">
    <q-header bordered class="bg-white text-black">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title class="text-weight-bold">
          <!-- <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar> -->
          Qtwitter
        </q-toolbar-title>

        <!-- <q-btn dense flat round icon="menu" @click="toggleRightDrawer" /> -->
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <!-- drawer content -->
      <q-icon
        class="q-pa-md"
        name="fa-solid fa-dove"
        size="lg"
        color="primary"
      />
      <!-- list items -->
      <q-list>
        <q-item
          clickable
          v-ripple
          v-for="item in navItems"
          :key="`${item.name}-${item.id}-${Math.ceil(Math.random())}`"
          @click="toggleSelectedItem(item.id)"
        >
          <q-item-section avatar>
            <q-icon
              :color="item.id === selectedNavItem ? 'primary' : 'black'"
              size="md"
              :name="item.icon"
            />
          </q-item-section>

          <q-item-section
            :class="item.id === selectedNavItem ? 'text-primary' : 'text-black'"
            class="text-h5 text-weight-bold"
            >{{ item.title }}</q-item-section
          >
        </q-item>
      </q-list>
    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <!-- drawer content -->
      <q-input
        color="primary"
        class="q-ma-md"
        rounded
        outlined
        v-model="text"
        label="Search Twitter"
      >
        <template v-slot:prepend>
          <q-icon name="search" />
        </template>
      </q-input>

      <q-list separator padding>
      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label overline class="color-grey">Education</q-item-label>
          <q-item-label class="text-weight-bold">Something Amazing Happened</q-item-label>
          <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>5 min ago</q-item-label>
        </q-item-section>
      </q-item>
      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label overline class="color-grey">Political</q-item-label>
          <q-item-label class="text-weight-bold">Something Amazing Happened</q-item-label>
          <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>5 min ago</q-item-label>
        </q-item-section>
      </q-item>
      <q-item class="q-pa-md">
        <q-item-section>
          <q-item-label overline class="color-grey">Entertainment</q-item-label>
          <q-item-label class="text-weight-bold">Something Amazing Happened</q-item-label>
          <q-item-label caption>Secondary line text. Lorem ipsum dolor sit amet, consectetur adipiscit elit.</q-item-label>
        </q-item-section>

        <q-item-section side top>
          <q-item-label caption>5 min ago</q-item-label>
        </q-item-section>
      </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const rightDrawerOpen = ref(false);
    const navItems = ref([
      {
        id: 1,
        title: "Home",
        route: "/home",
        icon: "home",
      },
      {
        id: 2,
        title: "Explore",
        route: "/explore",
        icon: "tag",
      },
      // {
      //   id: 3,
      //   title: 'Notifications',
      //   route: '/notifications',
      //   icon: 'notifications'
      // },
      // {
      //   id: 4,
      //   title: 'Messages',
      //   route: '/messages',
      //   icon: 'email'
      // },
      // {
      //   id: 5,
      //   title: 'Bookmarks',
      //   route: '/bookmarks',
      //   icon: 'bookmark_border'
      // },
      // {
      //   id: 6,
      //   title: 'Twitter Blue',
      //   route: '/subscription',
      //   icon: 'airplane_ticket'
      // },
      // {
      //   id: 7,
      //   title: 'Profile',
      //   route: 'profile',
      //   icon: 'person'
      // },
      // {
      //   id: 8,
      //   title: 'More',
      //   route: '/more',
      //   icon: 'more_horiz'
      // }
    ]);

    const selectedNavItem = ref(1);
    const toggleSelectedItem = (itemId) => (selectedNavItem.value = itemId);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },

      rightDrawerOpen,
      toggleRightDrawer() {
        rightDrawerOpen.value = !rightDrawerOpen.value;
      },
      navItems,
      selectedNavItem,
      toggleSelectedItem,
    };
  },
};
</script>

<!-- <style lang="scss">
.main-my-view {
  padding: 1rem;
}
</style> -->