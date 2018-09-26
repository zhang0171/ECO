<template>
<div style="padding:30px 24px; box-sizing:border-box;">
  <div class="cleanBody">
    <div class="c-top">
       <b style="font-size:18px;">清粉任务</b>
    </div>
    <div class="c-tit">
      <div class="c-tit-time">
        <p style="color: rgba(0, 0, 0, 0.45);font-size:16px;"><a-icon type="user-add" />加粉次数</p>
        <p style="color: rgba(0, 0, 0, 0.85);font-size:30px;">12</p>
      </div>
      <div class="c-tit-people">
        <p style="color: rgba(0, 0, 0, 0.45);font-size:16px;"><a-icon type="usergroup-add" />加粉人数</p>
        <p style="color: rgba(0, 0, 0, 0.85);font-size:30px;">30</p>
      </div>
    </div>
    <div class="c-title">
      <b>任务明细</b>
    </div>
    <div class="c-handle">
      <a-button>删除</a-button>
      <a-button type="primary" @click="task()">新建任务</a-button>
    </div>

    <a-row class="c-table">
      <a-col :span="1"><a-checkbox></a-checkbox></a-col>
      <a-col :span="3">&nbsp;&nbsp;全选</a-col>
      <a-col :span="6">创建时间</a-col>
      <a-col :span="3">清粉账号（个）</a-col>
      <a-col :span="3">目标好友（个）</a-col>
      <a-col :span="3">成功清粉（个）</a-col>
      <a-col :span="3">操作方式</a-col>
      <a-col :span="2">详情</a-col>
    </a-row>
    <!--- 动态展示的数据 -->
    <div class="oList">
      <a-row class="c-table-two" v-for='(info,index) in wxInfos' :key='index'> 
        <a-col :span="1"><a-checkbox></a-checkbox></a-col>
        <a-col :span="3">&nbsp;&nbsp;{{info.name}}</a-col>
        <a-col :span="6">2018-09-12 13:08:42</a-col>
        <a-col :span="3" style="display: flex;align-items: center;justify-content: center;"><div class="imgBox"></div>{{info.service}}</a-col>
        <a-col :span="3">{{info.number}}</a-col>
        <a-col :span="3">{{info.state}}</a-col>
        <a-col :span="3"><a>修改备注</a></a-col>
        <a-col :span="2">已结束</a-col>
      </a-row>
    </div>



  </div>

</div>
</template>
<script>
export default {
  name:'fansClean',
  data(){
    return {
      wxInfos: [{name: 'ninja', acount: '123', service: 'sfsf445rio', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '4fffffsfdsfafa56', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: '大王叫', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: 'ninja', acount: '123', service: 'mario', number: '456', state: 'open'},{name: '来巡山', acount: '123', service: 'mario', number: '456', state: 'open'},{name: '我把人间', acount: '123', service: 'mario', number: '456', state: 'open'}],

    }
  },

  methods:{
    task(){
      this.$router.push('/cleanTask')

    }
  }



}
</script>
<style scoped>
.cleanBody{
  min-height:804px;
  background: #ffffff;
  padding:0 30px;
  box-sizing:border-box;
  overflow:hidden;
}
.c-top{
  height:auto;
  line-height:60px;
  border-bottom:2px solid #dddddd;
  padding-left:14px;
}
.c-tit{
  height:auto;
  display: flex;
  align-items: center;
}
.c-tit>p{
  width:100%;
}
.c-tit-time{
  width:230px;
  height:131px;
  display: inline-block;  
  text-align: center;
  padding-top:30px;
  box-sizing:border-box;
}
.c-tit-people{
  width:230px;
  height:131px;
  display: inline-block;  
  text-align: center;
  padding-top:30px;
  box-sizing:border-box;
}
.c-title{
  height:45px;
  background: #fafafa;
  font-size:16px;
  display:flex;
  align-items:center;
  padding-left:20px;
}
.c-handle{
  height:auto;
  margin-top:20px;
  margin-bottom:20px;
  display:flex;
  justify-content:space-between;
  padding:0 40px;
  box-sizing:border-box;
}
.c-table{
  text-align:center;
  background: #fafafa;
  height:40px;
  display:flex;
  align-items:center;
}
.c-table-two{
  text-align:center;
  background: #ffffff;
  height:40px;
  display:flex;
  align-items:center;
  border-bottom:1px solid #fafafa;
}
.imgBox{
    margin-right: 5px;
    width: 25px;
    height: 25px;
    border-radius: 25px;
    overflow: hidden;
    border:.5px solid #dddddd;
    display: inline-block;
}
</style>
