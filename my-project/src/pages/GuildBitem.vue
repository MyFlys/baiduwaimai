<template>
  <div class="bitemBody">
    <bitem-header></bitem-header>
    <bitem-section :lists="imgList"></bitem-section>
    <bitem-footer></bitem-footer>
  </div>

</template>

<script>
  import GuildApis from "../apis/GuildApis"
  import BitemHeader from "../components/guildBitem/BitemHeader"
  import BitemSection from "../components/guildBitem/BitemSection"
  import BitemFooter from "../components/guildBitem/BitemFooter"

  export default {
    name: "GuildBitem",

    components:{
      BitemHeader,
      BitemFooter,
      BitemSection
    },
    data(){
      return{
        imgList:{}
        // imgIndex:""
      }
    },
    methods:{
      __initPage(){
        GuildApis.getGuildSwiperLists( this.$route.query.id ,(data)=>{
          // this.imgList = data[this.imgIndex];
          this.imgList = data;

          console.log(this.imgList);
        })
      }
    },
    mounted(){
      // this.checked();
    },
    created(){
      this.__initPage();
    },

  }
</script>

<style scoped>

  .bitemBody{
    background: #000;
    width: 100%;
    height: 100%;
    display: -webkit-flex;
    flex-direction: column;
  }
</style>
