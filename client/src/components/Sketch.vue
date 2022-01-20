<template>
  <div class="h-100 w-100">
     <!-- <h1>test</h1> -->
      <div id="canvas-container" class="h-100 w-100">
      </div>
  </div>
</template>

<script>
import Konva from 'konva'

export default {
  name: 'Sketch',
  props: {
    msg: String,
    // frameHeight:Number,
    // frameWidth:Number
  },
  data(){
      return{
        stage:null,
        layer:null,
        box:null,
        xpos: 200,
        ypos: 200,
      }
  },
  mounted:function(){
     let frame = document.getElementById("canvas-container");
     console.log(frame.parentElement.offsetWidth);
     console.log(frame.offsetHeight);
      this.stage = new Konva.Stage({
  
          container: 'canvas-container', //親要素のdivタグのidを指定
          width: frame.offsetWidth, //キャンバスの横幅
          height: frame.offsetHeight //キャンバスの高さ
        }),
      this.layer = new Konva.Layer(),
      this.box = new Konva.Rect({
            width: frame.offsetWidth, //横幅
            height: frame.offsetHeight, //高さ
            fill: "#ddd", //塗り潰しの色
            stroke: "#000", //枠線の色
            strokeWidth: 1, //枠線の太さ
            opacity: 1, //透過率
            cornerRadius: [3, 3, 3, 3] //四角の角を丸める
      })
    this.layer.add(this.box); //作った四角をlayerにadd
    this.stage.add(this.layer); //layerをstageにadd (階層の上に順番に追加していく)

    this.layer.draw(); //これで描画

    this.stage.addEventListener('mouseup', this.mouseup)
  },
  methods:{

  }
}
</script>