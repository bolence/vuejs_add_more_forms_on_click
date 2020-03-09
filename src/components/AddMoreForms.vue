<template>
    <div>
        <center>
            <b-button variant="primary" @click.prevent="addForm">Add form<span v-show="countForms > 0">: {{ countForms }} forms</span></b-button>
        </center>
    <br>
        <b-container fluid class="bv-example-row">

            <b-col md="6" offset-md="4" v-for="(form, index) in forms" :key="index" class="mb-2">

                    <b-form inline>
                        <label class="sr-only" for="inline-form-input-name">Name</label>
                        <b-input
                        id="inline-form-input-name"
                        class="mb-2 mr-sm-2 mb-sm-0"
                        placeholder="Username"
                        v-model="data.username[index]"
                        ></b-input>

                        <label class="sr-only" for="inline-form-input-username">Last name</label>
                        <b-input 
                        id="inline-form-input-lastname" 
                        placeholder="Lastname" 
                        class="mb-2 mr-sm-2 mb-sm-0"
                        v-model="data.lastname[index]"
                        ></b-input>
                        
                        <b-button variant="primary" class="mr-2" @click.prevent="saveForm(index)">Save</b-button>
                        <b-button variant="danger" @click.prevent="removeForm(index)">Remove</b-button>
                    </b-form>
                    <hr>   
            </b-col>
            
            <b-col md="6" offset-md="4" v-show="countForms >= 2">
            <b-button variant="success" class="mr-2" @click.prevent="saveAll">Save all</b-button>
            <b-button variant="danger" @click.prevent="removeAll">Remove all</b-button>
            </b-col>
        </b-container>

        <pre v-show="formSaved">
            {{ data }}
        </pre>

    </div>
</template>

<script>
    export default {
        data() {
            return {
                forms: [],
                countForms: 0,
                data: {
                    username: [],
                    lastname: [],
                },
                formSaved: false,
               
            }
        },

        methods: {

            addForm() {
                this.forms.push({
                    username: [],
                    lastname: []
                });
                this.countForms++;
            },

            removeForm(index) {
                this.forms.splice(index, 1);
                this.countForms -= 1;
                this.data.username[index];
                this.data.lastname[index];
            },

            removeAll() {
                this.forms = [];
                this.countForms = 0;
                this.data.username = [];
                this.data.lastname = [];
            },

            saveForm() {
                this.formSaved = true;
            },

            saveAllForm() {

            }


        },
    }
</script>