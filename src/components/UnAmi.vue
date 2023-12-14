<template>
    <div class="container my-1">
        <ul class="list-group">
            <h2 class="list-group-item">{{leNom}} {{premium === true ? '(Ami premium)':'(Ami nul)'}}</h2> 
            <div class="btn-group" role="group" aria-label="Basic example">
                <button  @click="afficherDetails" type="button" class="m-1 btn btn-outline-secondary">👁 {{detailsVisibles? 'Masquer': 'Afficher'}} Détails</button>
                <button  @click="afficherPremium" type="button" class=" m-1 btn btn-outline-success">⭐️ {{premium? 'Retirer': 'Mettre'}} Premium</button>
                <button  @click="$emit('delete',this.id)" type="button" class=" m-1 btn btn-outline-danger">🗑 Suppr.</button>
            </div>
            <ul v-if="detailsVisibles" class="list-group">
                <li class="list-group-item">{{lePhone}}</li>
                <li class="list-group-item">{{leMail}}</li>
            </ul>
        </ul>
    </div> 
</template>

<script>
export default {
    props:{
        id: {
            type:String,
            required: true
        },
        leNom:{
            type:String,
            required:true
        },
        lePhone:{
            type:String,
            required:true
        },
        leMail:{
            type:String,
            required:true
        },
        premium:{
            type:Boolean,
            required:false,
            default:false
        }
    },
    /*emits: {
        'mon-event-premium': function(id) {
            if(id) {
                return true;
            } else {
                console.warn('No Id :(');
                return false;
            }
        }
    },*/
    emits: ['mon-event-premium','delete'],
    data(){
        return{
            detailsVisibles:false,
            //premiumData: this.premium,
        }
    },
    methods:{
        afficherDetails(){
            this.detailsVisibles = !this.detailsVisibles;
        },
        afficherPremium(){
            //this.premiumData = !this.premiumData;
            this.$emit('mon-event-premium',this.id);
        }
    },
}
</script>