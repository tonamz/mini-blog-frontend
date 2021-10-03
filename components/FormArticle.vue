<template>
        <div>
            <b-form class="mt-2" @submit="onSubmit" @reset="onReset">
                <b-form-group
                    id="input-group-1"
                    label="Name"
                    label-for="input-1"
                >
                    <b-form-input
                    id="input-1"
                    v-model="form.name"
                    type="text"
                    placeholder="Enter name"
                    required
                    ></b-form-input>
                </b-form-group>

                <b-form-group id="input-group-2" class="mt-2" label="Content" label-for="input-2">
  
                    <b-form-textarea
                        id="input-2"
                        v-model="form.content"
                        placeholder="Enter content"
                        rows="3"
                        max-rows="6"
                    ></b-form-textarea>
                </b-form-group>

                <b-form-group id="input-group-3" class="mt-2" label="Category" label-for="input-3">
                    <b-form-select
                    class="form-control"
                    id="input-3"
                    v-model="form.category"
                    :options="categories"
                    required
                    ></b-form-select>
                </b-form-group>


                <b-form-group id="input-group-3" class="mt-2" label="Status" label-for="input-3">
                    <b-form-select
                    class="form-control"
                    id="input-3"
                    v-model="form.status"
                    :options="status"
                    required
                    ></b-form-select>
                </b-form-group>


                <b-button type="submit" class="mt-4" variant="primary">Submit</b-button>
                <b-button type="reset" class="mt-4" variant="danger">Reset</b-button>
            </b-form>
        </div>

</template>

<script>
export default {
    props: {
        article: Object
    },
    data() {
      return {
        form: {
            name: '',
            content: '',
            category: null,
            status: null,
            author: 1,
            
        },
        categories: [
          { value: null, text: 'Please select an option' },
          { value: '1', text: 'Physics' },
          { value: '2', text: 'Technlogy' },
          { value: '3', text: 'Chemistry' },
        ],        
        status: [
          { value: null, text: 'Please select an option' },
          { value: '1', text: 'Publish' },
          { value: '2', text: 'Draft' },
          { value: '3', text: 'Private' },
        ]
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))
        this.$axios.$post('/article/add', 
        JSON.stringify(this.form), {

        })
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.name = ''
        this.form.content = ''
        this.form.category = null
        this.form.status = null
      }
    }
}
</script>
