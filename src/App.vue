<template>
    <!-- <div class="container"> -->
      <h1 class="text-center">Les Amis</h1>
      <ul class="list-group">
        <un-ami v-for="unAmi in lesAmis" 
        v-bind:key="unAmi.id" :leNom="unAmi.name" :lePhone="unAmi.phone" :leMail="unAmi.email" :premium="unAmi.premium" 
        @moneventpremium="afficherStatusPremium()">
        </un-ami>
      </ul>
    <!-- </div> -->
  </template>

<script>
export default{
  data(){
    return {
      lesAmis: [
        {
            id: 'lasticot',
            name: 'COCO L ASTICOT',
            phone: '01234 5678 991',
            email: 'coco@lasticot.com',
            premium: true
        },
        {
            id: 'janine',
            name: 'Janine DeLavega',
            phone: '09876 543 221',
            email: 'janine@delavega.com',
            premium: false
        },],
    }
  },
    methods: {
        afficherStatusPremium() {
            console.log("Howdy");
        }
    }
}

</script>