<template>
  <div id="app" >
     <b-btn v-b-modal.modalPrevent>Launch demo modal</b-btn>
    <!-- Main UI -->
    <div class="mt-2 mb-4" >
      Submitted Names:
      <ul>
        <li v-for="n in names">{{n}}</li>
      </ul>
    </div>

    <MyModal @newdata="handleData($event)"  v-bind:form-data="getFormData()"
                                            v-bind:form-tmpl="formTemplate"/>

  </div>
</template>

<script>

import  MyModal from "./components/iy-modal.vue"

export default {

  data () {
    return {
              names: [],
              formData: {
                header: {text :"Express form"},
                footer: {text :"----footer-----"},
                items:{

                }
              },

              formTemplate :{
                items:{name:
                        {label:"Your name",
                         hint: "Enter your name",
                         type: "text",
                         length: 20
                        },
                      phone:
                        {label:"Phone number",
                         hint:"Enter your phone",
                         type: "tel",
                         length: 20
                        },
                      birth:
                        {label:"Date of birth",
                         type: "date",
                         length: 20
                        },
                      age:
                        {label:"Age",
                         type: "range",
                         length: 20
                        }
                }
              }
            }
  },

  components: {
    MyModal
  },
  methods: {
    getFormData () {
       var buf = Object.create(this.formData);
       return buf
    },
    handleData: function(e) {
      this.names.push(e);
      console.log(e);
      console.log(this.names)
    }
  }, 

}
</script>

