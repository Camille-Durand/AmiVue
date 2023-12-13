<template>
    <div class="container my-1">
        <ul class="list-group">
            <h2 class="list-group-item">{{leNom}} {{premium === true ? 'Ami premium':'Ami nul'}}</h2> 
            <button @click="afficherPremium" class="btn btn-danger">Premium ?</button>
            <button @click="afficherDetails" class="btn btn-primary">{{detailsVisibles? 'Masquer': 'Afficher'}}</button>           
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
            this.$emit('moneventpremium',this.id);
        }
    },
}
</script>