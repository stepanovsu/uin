<template>
	<div v-if="type === 'text'">
		<label >{{ctrlRef.label}}:</label>
		<b-form-input :type="ctrlRef.type"
                    :placeholder="ctrlRef.hint"
                    v-model = "ctrlData[get()]">            
      	</b-form-input>
	</div>

</template>

<script >
	export default {
		props:{
			ctrlData: Object,
			ctrlRef:Object,
			dataName: String
		},
		data () {
			return {
				type : 'text',
			}
		},
		methods: {
			get () {
				return this.dataName
			}
		}
	}
</script>