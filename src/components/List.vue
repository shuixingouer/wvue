<template>
  <div class="list">
    <div>{{tip}}</div>
    <a href="" class="weui-media-box weui-media-box_appmsg"  v-for="item in listData">
      <div class="weui-media-box__hd">
      </div>
      <div class="weui-media-box__bd">
        <h4 class="weui-media-box__title">{{item.title}}</h4>
        <p class="weui-media-box__desc">{{item.genres}}</p>
        <p class="weui-media-box__time">{{item.subtype}}</p>
      </div>
    </a>
  </div>
</template>

<script>
import { bus } from '../bus.js'
export default {
  name: 'list',
  data () {
    return {
      list: [{
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }, {
        imgs: './assets/images/logo.png',
        title: 'Jack',
        desc: 'Jack',
        time: 'Jack'
      }],
      listData: [],
      tip: '0',
      apiUrl: 'https://api.douban.com/v2/movie/top250?count=10'
    }
  },
  created () {
    bus.$on('tip', (text) => {
      this.tip = text
      this.getLists()
    })
  },
  ready () {
    console.log('数据取出来了吗')
  },
  methods: {
    getLists: function () {
      var resource = this.$resource(this.apiUrl)
      var vm = this
      resource.get().then((response) => {
        vm.$set('listData', response.data.subjects)
      }).catch(function (response) {
        console.log(response)
      })
    }
  }
}
</script>
