<template>
  <div class="geolocation-hot-city">

    <div class="hotCity-cite">
      <cite>热门城市查询</cite>
    </div>
    <div class="hotCity-range">
      <slot-range/>
    </div>

    <div class="hotCity-number">
      <slot-number/>
    </div>

    <div class="hotCity-lang">
      <slot-lang/>
    </div>

    <button @click="getHotCity()">getHotCity</button>
  </div>
  <div class="hotCity-show">
    <ol v-for="topCityList in hotCity">
      <li>地区/城市名称:{{ topCityList.name }}</li>
      <li>地区/城市ID:{{ topCityList.id }}</li>
      <li>地区/城市纬度:{{ topCityList.lat }}</li>
      <li>地区/城市经度：{{ topCityList.lon }}</li>
      <li>地区/城市的上级行政区划名称：{{ topCityList.lon }}</li>
      <li>地区/城市所属一级行政区域：{{ topCityList.lon }}</li>
      <li>地区/城市所属国家名称{{ topCityList.counter }}</li>
      <li>地区/城市所在时区:{{ topCityList.tz }}</li>
      <li>地区/城市目前与UTC时间偏移的小时数，{{ topCityList.utcOffset }}</li>
      <li>地区/城市的属性:{{ topCityList.type }}</li>
      <li>地区评分:{{ topCityList.rank }}</li>
    </ol>
  </div>
</template>

<script>
import slotLang from "@/components/slot/slotLang"
import slotNumber from "@/components/slot/slotNumber"
import slotRange from "@/components/slot/slotRange"
import { LOCATION_HOT_CITY } from "@/store/type.mjs"
import { computed } from "vue"
import { useStore } from 'vuex'

export default {
  name: "HotCity",
  components: { slotRange, slotNumber, slotLang },
  setup() {
    const store = useStore ()

    function getHotCity() {
      store.dispatch (LOCATION_HOT_CITY)
    }

    return {
      getHotCity,
      hotCity: computed (() => store.state.a.hotCity.data),
    }
  },
}
</script>

<style lang="scss" scoped>
.geolocation-hot-city {

  background-color: #42b983;

  .hotCity-cite {
    cite {
      font-style: normal;
      font-size: large;
    }
  }
}


</style>
