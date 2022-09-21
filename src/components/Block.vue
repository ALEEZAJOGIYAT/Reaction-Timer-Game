<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me

    </div>
    
</template>

<script>

export default{
    props:['delay'],
    data(){
        return{
            showBlock:false,
            timer:null,
            reactionTimer:0
        }

    },
    mounted(){
        setTimeout(()=>{
            this.showBlock=true
           this.startTimer();
            console.log(this.delay,'mounted delay')
        },this.delay)
    },
    methods:{

        startTimer(){
          this.timer= setInterval(()=>{
            this.reactionTimer +=10
          },10)
          console.log("start timer function triggered")
    
        },
        stopTimer(){
            clearInterval(this.timer)
            $this.emmit('end',this.reactionTimer)
    
        }
    }

}
</script>

<style scoped>
    .block{
        width: 400px;
        border-radius: 20px;
        background: rgb(161, 136, 136);
        color:aliceblue;
        padding:100px 0;
        color: white;
        margin: 40px auto;
        

    }

</style>