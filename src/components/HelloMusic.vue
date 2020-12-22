<template>
  <div class="hello">
    <p>{{ str2 }} </p>
    <search :initType="initType" :selectItems="selectItems"  @searchOk="searchOk"/>
    <footer>@Luer</footer>
  </div>
</template>


<script>
import search  from "./search";
export default {
  name: 'HelloMusic',
  components: {search},
  data () {
    return {
      str: '凡音之起，由人心生也，人心之动，物使之然也',
      i: 0,
      timer: 0,
      str2: "",
      result: '',
      selectItems: [], //条目
      initType: '', //初始类型
    }
  },
  created () {
    this.setSelectItems()
    this.setInitType()
  },
  methods: {
    typing() {  //字体输入特效
      console.log(this.str)
      if (this.i <= this.str.length) {
        this.str2 = this.str.slice(0, this.i++) + '_';
        this.timer = setTimeout(() => {
          this.typing();
        }, 200);
      } else {
        clearTimeout(this.timer)
      }
    },
    setSelectItems () {  //搜索条目数据
      this.selectItems = [{value: '基本乐理', label: '基本乐理'}, {value: '歌曲', label: '歌曲'}, {value: '乐器', label: '乐器'}]
    },
    setInitType () {  //设置初始搜索框类型
      this.initType = '基本乐理'
    },
    searchOk (value) {
      console.log(value) //得到 类型+搜索内容
      // 调用你的搜索接口，搜索条件为搜索的类型 + 搜索值
      // yourSearch (this.selectStatus, value)
    },
  },
  mounted() {
      this.typing();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  p{
    margin-top: -80px;
    color: bisque;
  }

  footer{
    color: white;
    width: 100%;
    position: absolute;
    bottom:0;
    left: 0;
  }

</style>
