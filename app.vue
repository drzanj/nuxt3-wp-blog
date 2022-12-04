<template>
  <div>
    <MenuTop />
    <NuxtPage />
    <p>Hello World</p>
  </div>
</template>
<script>
if (process.browser) {
  require('aframe')
}
export default {

}
</script>
