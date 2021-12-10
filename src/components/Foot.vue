<template>
  <Footer :class="isMobile ? 'mobile' : 'pc'">
    <div class="link-menu">
      <NuxtLink :to="linkUrl.home"><span>Home</span></NuxtLink>
      <img v-if="!isMobile" class="logo" src="@/assets/icons/round.svg" />
      <NuxtLink :to="linkUrl.app"><span>App</span></NuxtLink>
      <img v-if="!isMobile" class="logo" src="@/assets/icons/round.svg" />
      <NuxtLink :to="linkUrl.info"><span>Info</span></NuxtLink>
    </div>
  </Footer>
</template>

<script lang="ts">
import { Vue, Component } from 'nuxt-property-decorator'

import { Layout } from 'ant-design-vue'

const { Footer } = Layout

@Component({
  components: {
    Footer
  }
})
export default class Foot extends Vue {
  navOpened = false
  linkUrl = {
    home: '/',
    app: '/swap/',
    info: '/info/',
    listing: 'https://forms.gle/Ct7ySJkxQyUvrHR99',
    twitter: 'https://twitter.com/RaydiumProtocol',
    discord: 'https://discord.com/invite/6EvFwvCfpx',
    telegram: 'https://t.me/raydiumprotocol',
    medium: 'https://raydium.medium.com/'
  }

  get isMobile() {
    return this.$accessor.isMobile
  }

  beforeMount() {
    this.$accessor.queryIsMobile()
  }
}
</script>

<style lang="less" scoped>
.mobile {
  .link-menu {
    span {
      display: inline-block;
      width: 100%;
      text-align: center;
      font-size: 14px;
      color: #84879c;
      padding-top: 16px;
    }
  }

  .icon_list {
    text-align: center;
    margin: 48px 0;
  }

  .logo {
    text-align: center;
    margin-bottom: 50px;
  }
}

.pc {
  display: flex;
  justify-content: center;
  background-image: linear-gradient(80deg, #003C3F 0%, #210545 76%);
  .link-menu {
    a {
      display: inline-block;
      width: 100px;
      text-align: center;
      font-size: 14px;
      color: #84879c;

      &:hover {
        color: #fff;
      }
    }
  }
}
</style>
