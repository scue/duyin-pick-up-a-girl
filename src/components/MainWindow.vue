<template>
  <Window title="Hello, 小姐姐~" width="400" height="100" margined>
    <Box>
      <Text>{{messages[current]}}</Text>
      <Text></Text>
      <Button width="100" v-on:click="ok">确定</Button>
    </Box>
  </Window>
</template>

<script>
import libui from 'libui-node'

export default {
  data: function() {
    return {
      current: 0,
      messages: [
        '做我女朋友好吗?',
        '房产证上写你名',
        '保大',
        '我妈会游泳',
        '我做家务',
        '我做饭',
        '宠你',
        '护犊子',
        '不凶人'
      ]
    }
  },
  methods: {
    ok() {
      this.current++
      if (this.current >= this.messages.length) {
        libui.stopLoop()
      }
    },
    exit() {
      libui.stopLoop()
    }
  }
}
</script>
