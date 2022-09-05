<template>
    <div class="modal-header" style="border-bottom:0">
        <button
        @click="close" class="btn-close"
        >
        </button>
      </div>
    <div class="modal-body">
            <h1 class="text-black">
            Minha primeira modal
            </h1>
      </div>
</template>
<script>
import useModal from '../../hooks/useModal'
export default {
  setup () {
    const modal = useModal()

    return {
      close: modal.close
    }
  }
}
</script>
