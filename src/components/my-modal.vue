<template>
  <div >
      <!-- Modal Component -->
      <b-modal id="modalPrevent"
               ref="modal"
               title="Submit your name 3"
               @ok="handleOk"
               @shown="clearName">
          <form @submit.stop.prevent="handleSubmit">
              <b-form-input type="text"
                            placeholder="Enter your name"
                            v-model="name">            
              </b-form-input>
          </form>
      </b-modal>
  </div>
</template>

<script>
export default {
  props :{
    dataModel : Object,
    formData : Object
  },
  data () {
    return {
      name: ''
    }
  },
  methods: {
    clearName () {
      this.name = ''
    },
    handleOk (evt) {
      // Prevent modal from closing
      evt.preventDefault()
      if (!this.name) {
        alert(formData.message)
      } else {
        this.handleSubmit()
      }
    },
    handleSubmit () {
      this.$emit("newdata",this.name);
      this.clearName()
      this.$refs.modal.hide()

    }
  }
}
</script>