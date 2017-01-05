<template>
<x-header :left-options="{showBack: false}" ></x-header>
  <div class="vux-demo">
    <!-- <img class="logo" src="../assets/vux_logo.png">
    <h1>{{ msg }}</h1> -->
  </div>
  <group title="预定">
    <cell v-for="courtList in episode_court_map" :title="treatEpisode(courtList.episode)" :is-link="false" >
      <button-tab class='court-list'>
         <button-tab-item v-for="(index, court) in courtList.courtList" :class="[treatDivide2(index) ?'court-l' : 'court-r', court.status == 2 ? 'disable' : '', court.status == 1 ? 'active' : '']"  @click='courtClick(court)' ><span>￥200</span></button-tab-item>
      </button-tab>
    </cell>
  </group>
  <x-button type='primary' style="position: fixed; bottom: 0; background-color:#f27330" @click='doAppoint'>我要预定</x-button>
</template>

<script>
import {XHeader, Group, Cell, ButtonTab, ButtonTabItem, XButton} from 'vux/src/components';
import { _ } from 'underscore/underscore-min'
export default {
  components: {
    Group,
    Cell,
    XHeader,
    ButtonTab,
    ButtonTabItem,
    XButton
  },
  data: function (){
    console.log("data start");
    var customerAppoint = {"customerId" : 1, "customerName" : "syusuk", "appointDate" : "2017-01-05", "appointInfo":[]};
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World!',
      appointJson: [],
      episode_court_map: []
    }
    
  },
  ready () {
    console.log("ready start");
    var that = this;
    that.$http.get('http://127.0.0.1/lantu/customer/appointList.json?date=2017-01-05',{'date': '2017-01-05'}).then(function (res) {
      that.episode_court_map = res.data.episode_court_map;
      that.appointJson = res.data.appointJson;
    });
  },
  methods: {
    courtClick: function (court) {
      if (court.status == 2) {
        return
      }
      court.status = (court.status + 1) % 2;
    },
    treatEpisode: function(num) {
        return (num +':00-' + (parseInt(num)+2) + ':00');
    },
    treatDivide2: function(num) {
      return (num % 2) > 0 ? false : true
    },
    doAppoint: function () {
      console.log(this.episode_court_map);
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
  position: relative;
  margin-left: 0.1rem;
  background: url(../assets/court-l.png) no-repeat center!important;
  background-size:100% 100% !important;
  border: 0 !important;
  height: 3rem !important;
}
.court-l span{
  position: absolute;
  right: 0.4rem;
  top: 0.6rem;
  color: #999;
}
.court-r span{
  position: absolute;
  left: 0.2rem;
  top: 0.6rem;
  color: #999;
}
.court-r {
  position: relative;
  background: url(../assets/court-r.png) no-repeat center!important;
  background-size:100% 100% !important;
  border: 0 !important;
  height: 3rem !important;
}
.court-l.active {
   background: url(../assets/court-l-active.png) no-repeat center!important;
   background-size:100% 100% !important;
}
.court-r.active {
   background: url(../assets/court-r-active.png) no-repeat center!important;
   background-size:100% 100% !important;
}
.court-l.disable {
   background: url(../assets/court-l-disable.png) no-repeat center!important;
   background-size:100% 100% !important;
}
.court-r.disable {
   background: url(../assets/court-r-disable.png) no-repeat center!important;
   background-size:100% 100% !important;
}
.court-l.active span{
  color: #fff;
}
.court-r.active span{
  color: #fff;
}
.weui_cell:before {
  border: 0 !important;
}
/*.weui_cells {
  font-size: 1rem !important;
}*/
</style>