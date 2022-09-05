<template>
  <modal-factory />
  <router-view/>
</template>
<script>
import modalFactory from './components/ModalFactory'
export default {
  components: { modalFactory }
}
</script>
