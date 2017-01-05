<template>
<x-header :left-options="{showBack: false}" ></x-header>
  <div class="vux-demo">
    <img class="logo" src="../assets/vux_logo.png">
    <h1>{{ msg }}</h1>
  </div>
  <group title="预定">
    <cell v-for="eipsode in episodeList" :title="treatEpisode(eipsode)" :is-link="false" >
      <button-tab class='court-list'>
         <button-tab-item v-for="(index, court) in courtList" :class="[treatDivide2(index) ?'court-l' : 'court-r']"  @click='courtClick(court, episode)' ></button-tab-item>
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
    var episodeData = '[{"episode": "10","courtlist":[{"court":1, "status":0},{"court":2, "status":0},{"court":3, "status":0},{"court":4, "status":0}]},{"episode": "12","courtlist":[{"court":1, "status":0},{"court":2, "status":0},{"court":3, "status":0},{"court":4, "status":0}]}]';
    var episodeJson = JSON.parse(episodeData);
    var episodeList = [10, 12, 14, 16, 18, 20];
    var courtList = [1, 2, 3, 4];

    var appointDate = '[{"_id" : "5860f30ece8d803c719fdef4","customerId" : 1,"customerName" : "syusuk","appointDate" : "2017-01-05","appointInfo" : [ {"episode" : 10,  "court" : 1, "status": 1 }, { "episode" : 12, "court" : 2, "status" : 1 } ], "valid" : 1, "isPay" : 1 }, {"_id" : "5860f33ece8d803c719fdef5","customerId" : 2,"customerName" : ".","appointDate" : "2017-01-05","appointInfo" : [ {"episode" : 16,  "court" : 3, "status": 1 }, { "episode" : 16, "court" : 4, "status" : 1 } ], "valid" : 1, "isPay" : 1 }]';
    var customerAppoint = {"customerId" : 1, "customerName" : "syusuk", "appointDate" : "2017-01-05", "appointInfo":[]};
    console.log(customerAppoint);
    var appointJson = JSON.parse(appointDate);
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World!',
      episodeLists: episodeJson,
      episodeList: episodeList,
      courtList: courtList,
      appointJson: appointJson
    }
  },
  methods: {
      courtClick: function (court, episode) {
         // court.status = (court.status + 1) % 2;
      },
      treatEpisode: function(num) {
          return (num +':00-' + (parseInt(num)+2) + ':00');
      },
      treatDivide2: function(num) {
        return (num % 2) > 0 ? false : true
      },
      isDisable: function (episode, court) {
        
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

</style>