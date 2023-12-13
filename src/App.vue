<template>
    <!-- <div class="container"> -->
      <h1 class="text-center">Les Amis</h1>
      <ul class="list-group">
        <new-ami v-on:add-ami="ajouterAmi">
        </new-ami>

        <un-ami v-for="unAmi in lesAmis" 
        v-bind:key="unAmi.id" :id="unAmi.id" :leNom="unAmi.name" :lePhone="unAmi.phone" :leMail="unAmi.email" :premium="unAmi.premium" 
        @mon-event-premium="afficherStatusPremium">
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
        afficherStatusPremium(leIdDansUnAmi) {
            let unAmiIdentified = this.lesAmis.find(unTruc => unTruc.id === leIdDansUnAmi);
            unAmiIdentified.premium = !unAmiIdentified.premium;
            console.log(unAmiIdentified);
        },
        ajouterAmi(name, phone, email) {
            let newAmiContact = {
                id: new Date().toISOString(),
                name: name,
                phone: phone,
                email: email,
                premium: false
            };
            this.lesAmis.push(newAmiContact);
        }
    }
}

</script>