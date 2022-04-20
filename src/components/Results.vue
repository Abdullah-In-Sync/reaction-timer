<template>
    <p>
        Your Reaction Time is :
    </p>
    <span id="bold">{{score}}</span><span> ms</span>
    <h3>{{this.rank}}</h3>

</template>


<script>
export default {
    props:['score'],
    data(){
      return{

          rank:null,
      }  
    },
    mounted(){
        if (this.score<310) {
            this.rank = "Ninja Fingers"
        } else if(this.score <500 && this.score >200){
            this.rank = "Rapid Reflexes"
        } else{
            this.rank = "Snail Pace....."
        }
    }
}
</script>

<style scoped>
#bold{
    font-weight: bold;
}
</style>