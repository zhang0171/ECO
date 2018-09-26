<template>
  <div style="padding:30px 24px;box-sizing:border-box;">
    <div class="cTaskBody">
      <div class="cT-top">
        <b style="font-size:18px;">清粉任务</b>
      </div>
      <div style="height:auto;">
        <div class="c-add">
          <a-icon type="plus-circle-o" style="color:#1890ff;"/>
          <span>添加清粉账号</span>
        </div>
      </div>
      <div class="n-title">
        <b>批量清除僵尸粉</b>
      </div>
      <div class="advert">
        <p><b>·</b> 一键无痕检测僵尸粉</p>
        <p><b>·</b> 快 · 狠 · 准</p>
      </div>
      <div class="n-title">
        <b>设置方式</b>
      </div>
       <div class="radio">
        <label for="ament">
          <input name="check" type="radio" id="ament" value="修改备注" checked='checked'> 修改备注（僵尸粉）
        </label>
        <br>
        <label for="delete">
          <input name="check" type="radio" id="delete" value="直接删除"> 直接删除
        </label>
       </div>
       <div class="c-submit">
         <button>确认提交</button>
       </div>


      
    </div>
  </div>
</template>
<script>
export default {
  name:'cleanTask',
  data(){
    return{

    }
  },
  methods:{

  }
}
</script>
<style scoped>
.cTaskBody{
  min-height:804px;
  background: #ffffff;
  padding:0 30px;
  box-sizing:border-box;
  overflow:hidden;
}
.cT-top{
  height:auto;
  line-height:60px;
  border-bottom:2px solid #dddddd;
  padding-left:14px;
}
.c-add{
  font-size:18px;
  margin-top:20px;
  margin-left:20px;
  cursor: pointer;
}
.n-title{
  height:45px;
  background: #fafafa;
  font-size:16px;
  display:flex;
  align-items:center;
  padding-left:20px;
  margin-top:20px;
}
.advert{
  color:#58bc9c;
  padding:20px;
}
.radio{
  height:auto;
  padding-left:20px;
  padding-top: 20px;
  padding-bottom: 20px;
  font-size:16px;
}
.c-submit{
  text-align:center;
  height:auto;
  padding:30px 0;
}
.c-submit>button{
  background: #58bc9c;
  color:#ffffff;
  width: 90px;
  height: 30px;
  border-radius: 5px;
  cursor: pointer;
}
</style>




