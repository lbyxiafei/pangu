<template>
  <div class="sider">
    <div v-for="tag in tags" :key="tag">
      <SiderLeftItem :tag="tag" @click-tag="clickTag" />
    </div>
  </div>
</template>

<script>
import SiderLeftItem from './SiderLeftItem.vue';

export default{
  name:"SiderLeft",
  data() {
    return {
      tagSelected: null
    }
  },
  props: {
    tags: Array
  },
  methods: {
    clickTag(tag){
      if(this.tagSelected!==null){
        document.querySelector(this.tagSelected)?.setAttribute('style', 'background:null');
      }
      let siderId='#sider_'+tag;
      if(this.tagSelected!==siderId){
        document.querySelector(siderId).setAttribute('style', 'background:wheat');
        this.tagSelected=siderId;
      }
      else{
        this.tagSelected=null;
      }
      this.$emit('click-tag', this.tagSelected===null ? null : tag);
    }
  },
  components: {
    SiderLeftItem
  }
}
</script>

<style scoped>
@import '../assets/base.css';
.sider{
  background-color: aqua;
  padding-left: 1vw;
  padding-right: 1vw;
  min-height: 90vh;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>