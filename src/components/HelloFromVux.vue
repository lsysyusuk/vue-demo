<template>
<x-header :left-options="{showBack: false}" ></x-header>
  <div class="vux-demo">
    <img class="logo" src="../assets/vux_logo.png">
    <h1>{{ msg }}</h1>
  </div>
  <group title="预定">
    <cell title="10:00-12:00" :is-link="false">
      <flexbox >
         <flexbox-item><div class="flex-demo">&nbsp;</div></flexbox-item>
         <flexbox-item><div class="flex-demo">&nbsp;</div></flexbox-item>
         <flexbox-item><div class="flex-demo">&nbsp;</div></flexbox-item>
         <flexbox-item><div class="flex-demo">&nbsp;</div></flexbox-item>
      </flexbox>
    </cell>
    <cell title="10:00-12:00" :is-link="false">
      <button-tab class='court-list'>
         <button-tab-item class='court-l' @click='court' ></button-tab-item>
         <button-tab-item class='court-r' @click='court'  selected></button-tab-item>
         <button-tab-item class='court-l' @click='court' ></button-tab-item>
         <button-tab-item class='court-r' @click='court' ></button-tab-item>
      </button-tab>
    </cell>
  </group>
</template>

<script>
import {XHeader, Group, Cell, Flexbox, FlexboxItem, ButtonTab, ButtonTabItem} from 'vux/src/components'
export default {
  components: {
    Group,
    Cell,
    XHeader,
    Flexbox,
    FlexboxItem,
    ButtonTab,
    ButtonTabItem
  },
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World!'
    }
  },
  methods: {
      court: function () {
         console.log(this.$el);
      }
  }
}

</script>

<style>
.vux-header {
  background-color: #f27330 !important;
}
.vux-demo {
  text-align: center;
}

.logo {
  width: 100px;
  height: 100px
}
.flex-demo {
   width: 3.5rem;
  text-align: center;
  color: #fff;
  background-color: #20b907;
  margin-bottom: 0rem;
  border-radius: 0rem;
  -webkit-background-clip: padding-box;
}
.weui_cell {
   padding: 0.3rem !important;
   height: 3rem !important;
}
.vux-button-group > a:first-child {
    border-width: 1px;
    border-top-left-radius: 0!important;
    border-bottom-left-radius: 0!important;
    background-clip: padding-box;
}
.vux-button-group > a:last-child {
    border-top-right-radius: 0!important;
    border-bottom-right-radius: 0!important;
    background-clip: padding-box;
}
.court-list {
   width: 16.5rem;
}
.court-l {
   margin-left: 0.1rem;
   background: url(../assets/court-l.png) no-repeat center!important;
   background-size:100% 100% !important;
   border: 0 !important;
   height: 3rem !important;
}
.court-r {
   background: url(../assets/court-r.png) no-repeat center!important;
   background-size:100% 100% !important;
   border: 0 !important;
   height: 3rem !important;
}
.court-l .active {
   background: url(../assets/court-l-active.png) no-repeat center!important;
}
.court-r .active {
   background: url(../assets/court-r-active.png) no-repeat center!important;
}

</style>