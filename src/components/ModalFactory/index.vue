<template>
    <teleport to='body'>
      <div v-if="state.isActive" class="modal animate__animated animate__fadeInDown animate__faster" style="display:block">
        <div class="modal-dialog">
         <div class="modal-content">
              <component :is="state.component" v-bind="state.props" />
         </div>
        </div>
      </div>

    </teleport>

</template>

<script>
import { defineAsyncComponent, onBeforeUnmount, onMounted, reactive } from 'vue'
import useModal from '../../hooks/useModal'

const ModalLogin = defineAsyncComponent(() => import('../ModalLogin'))

export default {
  components: {
    ModalLogin
  },
  setup () {
    const modal = useModal()
    const state = reactive({
      isActive: false,
      component: {},
      props: {}
    })
    onMounted(() => {
      modal.listen(handleModalToogle)
    })

    onBeforeUnmount(() => {
      modal.off(handleModalToogle)
    })

    function handleModalToogle (payload) {
      if (payload.status) {
        state.component = payload.component
        state.props = payload.props
      } else {
        state.component = {}
        state.props = {}
      }

      state.isActive = payload.status
    }
    return {
      state,
      handleModalToogle
    }
  }
}
</script>
<style scoped>

.modal-content{
  overflow: hidden;
  display: flex;
  background: #fff;
  border-radius: 8px;
}

.modal-head{
  position: fixed;
  margin-left: 10px;
}

.modal-body{
  position: fixed;
  padding-left: 12px;
  padding-right: 10px;
  background: #fff;

}
</style>
