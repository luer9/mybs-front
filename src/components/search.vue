<template>
  <div class="search">

    <el-select v-model="type" @change="changeType" class="select">
      <el-option
        v-for="item in selectItems"
        :key="item.value"
        :lable="item.label"
        :value="item.value">
      </el-option>
    </el-select>

    <el-input v-model="searchValue" placeholder="请输入内容" class="inputSearch"></el-input>
    <el-button type="info" icon="el-icon-search" @click="search" class="btn">搜索</el-button>
  </div>

</template>

<script>
    export default {
        name: "search",
      data() {
        return {
          searchValue: '',
          type: '',

        }
      },
      props: {
        selectItems: {
          type: Array,
          require: true
        },
        initType: {
          type: String,
          require: true
        }
      },
      methods:{
        changeType (newType) {
          this.$emit('changeType', newType)
        },
        search () {
          this.$emit('searchOk', this.searchValue)
          this.$emit('searchOk', this.type)
        }
      },
      created () {
        this.type = this.initType
      }
    }
</script>

<style scoped>

  .select{
    width: 110px;
    box-sizing: border-box;
    border-right: none;
    border-radius: 0;

  }

  .inputSearch{
    margin-top: 130px;
    width: 40%;
    border-radius: 0;
  }

  .btn{
    background-color: #666666;
    border: 1px solid #666666;
  }
</style>
