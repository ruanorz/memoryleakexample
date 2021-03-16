<template>
  <GridLayout columns="50, *" rows="100, 400" height="300">
    <Image row="0" col="0" :src="imageUrl()" stretch="aspectFit"/>
    <Label row="0" col="1" :text="randomText(5)"/>
    <GridLayout row="1" col="1" rows="50,50,50" columns="*, *, *, *, *, *, *, *, *, *">
      <Image row="0" col="0" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="1" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="2" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="3" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="4" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="5" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="6" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="7" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="8" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="0" col="9" :src="imageUrl()" stretch="aspectFit"/>

      <Image row="1" col="0" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="1" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="2" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="3" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="4" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="5" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="6" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="7" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="8" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="1" col="9" :src="imageUrl()" stretch="aspectFit"/>

      <Image row="2" col="0" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="1" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="2" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="3" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="4" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="5" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="6" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="7" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="8" :src="imageUrl()" stretch="aspectFit"/>
      <Image row="2" col="9" :src="imageUrl()" stretch="aspectFit"/>
    </GridLayout>

  </GridLayout>
</template>

<script>
export default {
  props: {
    item: {
      required: false,
      type: Number,
      default: 0
    }
  },
  methods: {
    randomText(length) {
      var result           = '';
      var characters       = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
      var charactersLength = characters.length;
      for ( var i = 0; i < length; i++ ) {
          result += characters.charAt(Math.floor(Math.random() * charactersLength));
      }
      return result;
    },
    imageUrl() {
      if(parseInt(this.item % 2) === 0)
        return 'https://picsum.photos/200'
      return 'https://picsum.photos/200'
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
