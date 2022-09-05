<template>
    <div class="container">
      <contact @login="handleLogin" />
    </div>
</template>

<script>
import Contact from './Contact.vue'
import useModal from '../../hooks/useModal'
export default {
  components: {
    Contact
  },
  setup () {
    const modal = useModal()

    function handleLogin () {
      modal.open({
        component: 'ModalLogin'
      })
    }

    return {
      handleLogin
    }
  }

}
</script>
