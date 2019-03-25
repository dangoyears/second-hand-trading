<template>
  <div class="container">
    <div class="weui-cells commodity_title">
        <div class="weui-cell">
            <div class="weui-cell__bd">
                <input class="weui-input" type="text" placeholder="给您的商品起个名字吧"/>
            </div>
        </div>
    </div>
    <div class="weui-cells weui-cells_form commodity_description">
        <div class="weui-cell">
            <div class="weui-cell__bd">
                <textarea class="weui-textarea" placeholder="请描述要转售商品的详细信息，如新旧程度、规格尺寸等，详细的介绍更有助于您的商品售出哦" rows="3" style="width: 100%"></textarea>
                <div class="weui-textarea-counter"><span>0</span>/200</div>
            </div>
        </div>
    </div>
    <div class="photo-container">
      <p>上传图片(最多只能上传5张图片)</p>
      <!-- <div v-for="(item, index) in photoSrcArr" :key="index" class="photo">
        <img :src="item" alt="">
      </div> -->
      <img v-for="(item, index) in photoSrcArr" :key="index" :src="item" class="photo" alt="图片暂时无法加载">
      <div class="photo" @click="uploadPhoto">
        <img class="add-icon" src="../../../static/images/add.png" alt="图片暂时无法加载">
      </div>
    </div>

    <button class="weui-btn" type="primary">123</button>



    <!-- <div class="descriptionBox">
      <p for="description" class="descriptionLabel">商品详情</p>
      <textarea class="description" id="description" placeholder="请描述要转售商品的详细信息，如新旧程度、规格尺寸等，详细的介绍更有助于您的商品售出哦" placeholder-style="font-size: small" @input="changeLength" maxlength="250" >
      </textarea>
      <span class="fontLen">{{fontLen}} / 250</span>
    </div>-->
  </div>
</template>

<script>
  export default {
    data () {
      return {
        fontLen: 0,
        photoSrcArr: []
      };
    },
    methods: {
      uploadPhoto() {
        wx.chooseImage({
          count: 5,        
          //返回图片的本地文件路径列表 tempFilePaths,   
          success: res => {
            Array.from(res.tempFilePaths).map((val) => {
              this.photoSrcArr.push(val);
              console.log(this.photoSrcArr);
            });
          }, 
          fail: res => {
            console.log("error:" + res);
          },
          complete: () => {
          }
        });
      },
      // changeLength(e) {
      //   this.fontLen = e.target.value.length;
      //   if(this.fontLen > 250) {
      //     console.log("字数超出限制");
      //   }
      // }
    }
  };
</script>

<style scoped>
  @import url('./style.css');
</style>
