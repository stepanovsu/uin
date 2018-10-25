<template>
  <div >
      <!-- Modal Component -->
      <b-modal id="modalPrevent"
               ref="modal"
               :title="buf.header.text"
               @ok="handleSubmit">

          <form @submit.stop.prevent="handleSubmit">
              <div v-for = "item,key in formTmpl.items">
                  <iy-ctrl v-bind:ctrl-data = "buf.items"
                           v-bind:ctrl-ref = "item"
                           v-bind:data-name = "key">
                  </iy-ctrl>
              </div>
          </form>
      </b-modal>
  </div>
</template>

<script>

import iyCtrl from "./dic/iy-ctrl.vue"

export default {
  props:{
    formData : Object,
    formTmpl : Object
  },

  data () {
    return {
      buf : this.formData
    }
  },

  components: {
    iyCtrl
  },

  methods: {

    handleSubmit (evt) {
      this.$emit("newdata",this.buf);
      console.log("xxx");
      console.log(this.buf);
      this.$refs.modal.hide()

    }
  }
}
</script>