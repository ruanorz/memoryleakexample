<template>
  <Page>
    <ActionBar title="Welcome to NativeScript-Vue!"/>
    <GridLayout columns="*" rows="*, 50">
      <ListView row="0" ref="itemsListView" for="(item, index) in items" separatorColor="transparent">
        <v-template >
          <ListItem :item="index"/>
        </v-template>
      </ListView>
      <GridLayout row="1" columns="*, *">
        <Button col="0" text="Go Back" @tap="navigateBack()"/>
        <Button col="1" text="Next Page" @tap="nextPage()"/>
      </GridLayout>
    </GridLayout>
  </Page>
</template>

<script >
// Components
import ListItem from './ListItem'
import Main from './App'

export default {
  components: {
    ListItem
  },
  data() {
    return {
      msg: 'Hello World!',
      items: new Array(1045)
    }
  },

  methods: {
    nextPage() {
      this.$navigateTo(Main)
    },
    navigateBack() {
      this.$navigateBack()
      gc()
    }
  }
}
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
