<template>
  <div class="app">
    <div class="row header">
      <div>
        <b>Pages</b>
        <ul class="menu">
          <li v-for="item in menuItems" :key="item.name">
            <router-link :to="item.path">/{{ item.name }}</router-link>
          </li>
        </ul>
      </div>
    </div>
    <div class="row content">
      <transition name="fade" mode="out-in">
        <router-view class="view"></router-view>
      </transition>
    </div>
    <div class="row footer">footer</div>
  </div>
</template>

<script>
import './styles/index.scss'
import { mapGetters } from 'vuex'

export default {
  name: 'App',
  computed: {
    ...mapGetters(['menuItems']),
  },
}
</script>

<style lang="scss">
.app {
  display: flex;
  flex-flow: column;
  height: 100%;

  .row {
    border: 1px dotted grey;

    &.header {
      flex: 0 1 auto;
      /* The above is shorthand for:
      flex-grow: 0,
      flex-shrink: 1,
      flex-basis: auto
      */
    }

    &.row.content {
      flex: 1 1 auto;
    }

    &.row.footer {
      flex: 0 1 40px;
    }
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.75s ease;
}

.fade-enter,
.fade-leave-active {
  opacity: 0;
}
</style>
