<template>
<div class="block" v-if="showBlock" @click="stopTimer">
<p>click me</p>

</div>
</template>

<script>
export default {
props:['delay'],
data(){
    return{
        showBlock:false,
        timer:null,
        countdown:0,
    
    }
},
 mounted() {
     setTimeout(() => {
         console.log(`the components is now mounted.`)
         this.showBlock= true;
         this.startTimer();
        
    }, this.delay);
  },
methods:{
    startTimer(){
        this.timer = setInterval(() => {
           this.countdown+=10;

        }, 10);

    },
    stopTimer(){
clearInterval(this.timer);
this.showBlock = false;
console.log(this.countdown);
this.$emit('end',this.countdown)
    }
}
}
</script>
<style>
.block{
    width: 300px;
    height: 300px;
    background-color: rgb(144, 167, 209);
    margin: 100px auto;
    border-radius: 10px;
    text-align: center;
    vertical-align: middle;

}
p{
    padding-top: 130px;
}
</style>