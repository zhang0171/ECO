<template>
  <div>
    <a-row>
      <a-col :span="22" :offset="1">
        <h1>发朋友圈</h1>
      </a-col>
      <a-col :span="22" :offset="1" class="title">
        <h3>发布内容</h3>
      </a-col>
      <a-col :span="22" :offset="1">
        <a-button type="primary" @click="visible=true"><a-icon type="plus-circle" />选择发布账号</a-button>
        <a-modal
          title="选择好友"
          v-model="visible"
          @ok="visible=false"
          okText="确认"
          cancelText="取消"
          width='500px'
        >
          <a-transfer
            :dataSource="mockData"
            showSearch
            :filterOption="filterOption"
            :targetKeys="targetKeys"
            @change="handleChange"
            :render="item=>item.title"
          >
          </a-transfer>
        </a-modal>
      </a-col>
      <a-col :span="22" :offset="1">
        <div id="editor"></div>
      </a-col>
      <a-col :span="22" :offset="1" class="title">
        <h3>评论提醒设置</h3>
      </a-col>
      <a-col :span="22" :offset="1">
        <a-radio-group name="radioGroup" :defaultValue="1">
          <a-radio :value="1">展示评论</a-radio>
          <a-radio :value="2">隐藏评论</a-radio>
        </a-radio-group>
      </a-col>
      <a-col :span="22" :offset="1">
        <a-button type="primary" @click="showConfirm">立即群发</a-button>
        <a-button type="primary" @click="date=true">定时群发</a-button>
      </a-col>
    </a-row>
    <a-modal
      title="定时群发"
      :visible="date"
      @ok="date=false"
      @cancel="date=false"
    >
      <a-date-picker placeholder="选择日期" />
       <a-time-picker :defaultValue="moment('12:08', 'HH:mm')" format="HH:mm" />
    </a-modal>
  </div>
</template>
<script>
  import moment from 'moment';
  import E from 'wangeditor'
  export default {
    name:"friends",
    data () {
      return {
        visible: false,
        mockData: [],
        targetKeys: [],
        date: false,
      }
    },
    methods: {
      moment,
      showConfirm() {
        this.$confirm({
          title: '立即群发',
          content: '消息开始群发后无法撤销，是否确认群发？',
          onOk() {
            return new Promise((resolve, reject) => {
              setTimeout(Math.random() > 0.5 ? resolve : reject, 1000);
            }).catch(() => console.log('Oops errors!'));
          },
          onCancel() {},
        });
      },
      getMock() {
        const targetKeys = [];
        const mockData = [];
        for (let i = 0; i < 20; i++) {
          const data = {
            key: i.toString(),
            title: `content${i + 1}`,
            description: `description of content${i + 1}`,
            chosen: Math.random() * 2 > 1,
          };
          if (data.chosen) {
            targetKeys.push(data.key);
          }
          mockData.push(data);
        }
        this.mockData = mockData
        this.targetKeys = targetKeys
      },
      filterOption(inputValue, option) {
        return option.description.indexOf(inputValue) > -1;
      },
      handleChange(targetKeys, direction, moveKeys) {
        console.log(targetKeys, direction, moveKeys);
        this.targetKeys = targetKeys
      },
    },
    mounted () {
      this.getMock()  
      var E = require('wangeditor')  // 使用 npm 安装
      // 创建编辑器
      var editor = new E('#editor')
      editor.customConfig.menus = [
        'emoticon',  // 表情
        'image',  // 插入图片
        'link',  // 插入链接
      ]
      var c = [{
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/7a/shenshou_thumb.gif",
        value : "[草泥马]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/60/horse2_thumb.gif",
        value : "[神马]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/bc/fuyun_thumb.gif",
        value : "[浮云]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/c9/geili_thumb.gif",
        value : "[给力]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/f2/wg_thumb.gif",
        value : "[围观]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/70/vw_thumb.gif",
        value : "[威武]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6e/panda_thumb.gif",
        value : "[熊猫]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/81/rabbit_thumb.gif",
        value : "[兔子]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/bc/otm_thumb.gif",
        value : "[奥特曼]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/15/j_thumb.gif",
        value : "[囧]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/89/hufen_thumb.gif",
        value : "[互粉]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/c4/liwu_thumb.gif",
        value : "[礼物]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/ac/smilea_thumb.gif",
        value : "[呵呵]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/0b/tootha_thumb.gif",
        value : "[嘻嘻]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6a/laugh.gif",
        value : "[哈哈]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/14/tza_thumb.gif",
        value : "[可爱]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/af/kl_thumb.gif",
        value : "[可怜]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/a0/kbsa_thumb.gif",
        value : "[挖鼻屎]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/f4/cj_thumb.gif",
        value : "[吃惊]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6e/shamea_thumb.gif",
        value : "[害羞]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/c3/zy_thumb.gif",
        value : "[挤眼]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/29/bz_thumb.gif",
        value : "[闭嘴]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/71/bs2_thumb.gif",
        value : "[鄙视]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6d/lovea_thumb.gif",
        value : "[爱你]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/9d/sada_thumb.gif",
        value : "[泪]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/19/heia_thumb.gif",
        value : "[偷笑]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/8f/qq_thumb.gif",
        value : "[亲亲]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/b6/sb_thumb.gif",
        value : "[生病]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/58/mb_thumb.gif",
        value : "[太开心]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/17/ldln_thumb.gif",
        value : "[懒得理你]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/98/yhh_thumb.gif",
        value : "[右哼哼]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6d/zhh_thumb.gif",
        value : "[左哼哼]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/a6/x_thumb.gif",
        value : "[嘘]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/af/cry.gif",
        value : "[衰]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/73/wq_thumb.gif",
        value : "[委屈]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/9e/t_thumb.gif",
        value : "[吐]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/f3/k_thumb.gif",
        value : "[打哈欠]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/27/bba_thumb.gif",
        value : "[抱抱]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/7c/angrya_thumb.gif",
        value : "[怒]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/5c/yw_thumb.gif",
        value : "[疑问]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/a5/cza_thumb.gif",
        value : "[馋嘴]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/70/88_thumb.gif",
        value : "[拜拜]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/e9/sk_thumb.gif",
        value : "[思考]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/24/sweata_thumb.gif",
        value : "[汗]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/7f/sleepya_thumb.gif",
        value : "[困]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6b/sleepa_thumb.gif",
        value : "[睡觉]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/90/money_thumb.gif",
        value : "[钱]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/0c/sw_thumb.gif",
        value : "[失望]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/40/cool_thumb.gif",
        value : "[酷]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/8c/hsa_thumb.gif",
        value : "[花心]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/49/hatea_thumb.gif",
        value : "[哼]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/36/gza_thumb.gif",
        value : "[鼓掌]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d9/dizzya_thumb.gif",
        value : "[晕]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/1a/bs_thumb.gif",
        value : "[悲伤]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/62/crazya_thumb.gif",
        value : "[抓狂]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/91/h_thumb.gif",
        value : "[黑线]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6d/yx_thumb.gif",
        value : "[阴险]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/89/nm_thumb.gif",
        value : "[怒骂]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/40/hearta_thumb.gif",
        value : "[心]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/ea/unheart.gif",
        value : "[伤心]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/58/pig.gif",
        value : "[猪头]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d6/ok_thumb.gif",
        value : "[ok]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d9/ye_thumb.gif",
        value : "[耶]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d8/good_thumb.gif",
        value : "[good]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/c7/no_thumb.gif",
        value : "[不要]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d0/z2_thumb.gif",
        value : "[赞]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/40/come_thumb.gif",
        value : "[来]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d8/sad_thumb.gif",
        value : "[弱]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/91/lazu_thumb.gif",
        value : "[蜡烛]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/6a/cake.gif",
        value : "[蛋糕]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/d3/clock_thumb.gif",
        value : "[钟]"
    }, {
        icon : "http://img.t.sinajs.cn/t35/style/images/common/face/ext/normal/1b/m_thumb.gif",
        value : "[话筒]"
    }
];
      let cc = c.map(i=>{
        let img = {}
        img.src = i.icon
        img.alt = i.value
        return img
      })
      editor.customConfig.emotions = [
        {
          // tab 的标题
          title: '默认',
          // type -> 'emoji' / 'image'
          type: 'image',
          // content -> 数组
          content: cc
      }
    ]
      editor.customConfig.uploadImgShowBase64 = true
      editor.create()
      document.querySelector('.w-e-text-container').style.height = '200px'
      document.querySelector('.w-e-text-container').style.zIndex = '0'  
    }
  }
</script>

<style scoped> 
  .ant-row>div {
    margin-bottom: 20px
  }
  .title {
    background: #bbdefb ;
    padding: 8px
  }
</style>
