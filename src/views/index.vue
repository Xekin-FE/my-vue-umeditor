<template>
  <div id="app">
    123123
    <v-ueditor
      id="ueditor"
      :config="config"
      :content="content"
      @ready="ueditorReady"
      @change="ueditorChange"
      @imageUpload="divUpload"
    ></v-ueditor>
  </div>
</template>

<script>
import vUeditor from '../components/v-ueditor.vue'
export default {
  name: 'app',
  components:{ vUeditor},
  data () {
    return {
      ue: '',
      content: '',
      config: {
            convertImageToBase64Enable:true,
            // imageUploadBySelf: true,
            initialFrameWidth:800, //编辑器宽高
            initialFrameHeight:400,
            toolbar: [
            'source | fontfamily paragraph fontsize | undo redo | bold italic underline strikethrough | superscript subscript | forecolor backcolor | removeformat |',
            'insertorderedlist insertunorderedlist | selectall cleardoc',
            '| justifyleft justifycenter justifyright justifyjustify |',
            'imagenone imageleft imageright imagecenter |',
            'link unlink | emotion video imageUploadBySelf',
            '| inserttable insertrow insertcol deleterow deletecol splittocells mergecells',
            '| horizontal print preview fullscreen', 'drafts', 'formula'
            ]
      }
    }
  },
  methods: {
    ueditorReady (ue) {
      this.ue = ue
    },
    ueditorChange (ue) {
      console.log(ue)
    },
    divUpload(file, callback){
      console.log('event back here', file)
      callback('no url')
    }
  },
  mounted () {
    setTimeout(() => {
      this.content = '初始化内容'
    }, 0)
  }
}
</script>

<style>
#app {
  text-align: center;
}
a {
  color: #42b983;
}
</style>
