<template>
    <div class="container bg-info my-1">
        <form @submit.prevent="submitData">
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Name</label>
            <input  class="form-control form-control-sm" type="text" placeholder="votre nom" aria-label=".form-control-sm example"
            v-model="enteredName">
        </div>
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Tél</label>
            <input class="form-control form-control-sm" type="tel" placeholder="Votre Tél" aria-label=".form-control-sm example"
            v-model="enteredPhone">
        </div>       
        <div class="mb-3">
            <label for="exampleFormControlInput1" class="form-label">Email</label>
            <input  class="form-control form-control-sm" type="email" placeholder="Votre EMAIL" aria-label=".form-control-sm example"
            v-model="enteredMail">
        </div>     
        <button class="btn btn-primary btn-sm col-12 my-1">Ajouter Ami</button>
        </form>
    </div>
</template>

<script>
    export default {
        emits: ['add-ami'],
        data() {
            return {
            enteredName: '',
            enteredPhone: '',
            enteredMail: ''
            }
        },
        methods: {
            submitData() {
                this.$emit('add-ami',this.enteredName,this.enteredPhone,this.enteredMail);
            }
        }
    }
</script>