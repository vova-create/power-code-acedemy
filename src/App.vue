<template>
  <div id="app">
    <TheHeader/>
    <div class="items-to-group">
      <InfoBlock/>
      <SignForm class="sign-form__show-full-screen" />
  </div>
    </div>
</template>

<script>


import TheHeader from "@/components/TheHeader.vue";
import InfoBlock from "@/components/InfoBlock.vue";
import SignForm from "@/components/SignForm.vue";
export default {
  name: 'App',
  components: {
    TheHeader,
    InfoBlock,
    SignForm
  },
}
</script>

<style lang="sass">
*
  margin: 0
  padding: 0
#app
  height: 100vh
  font-family: 'Roboto', sans-serif
  background-color: #272D3D

</style>
