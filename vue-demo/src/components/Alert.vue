<template>
<div class="alert alert-warning alert-dismissible" role="alert">
  <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
  <!-- <h1>{{msg}}</h1> -->
  test
</div>
</template>

<script>
export default {
  name: 'About',
  //接收外部消息
  props:[
    'alert'
  ],
  data () {
    return {
      msg: 'about'
    }
  }
}
</script>
