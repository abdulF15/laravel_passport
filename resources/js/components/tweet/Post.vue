<template>
    <div>
        <form action="#" @submit.prevent="post"> 
            <div class="form-group">
                <textarea cols="30" rows="2" v-model="body" ></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Post</button>
        </form>
    </div>
</template>
<script>
export default{
    data () {
        return {
            body : null
        }
    }, 
    props:{
        tweets : Array
    },
    methods:{
        post(){
            axios.post('/tweets',{
                body : this.body
            }).then((response)=>{
                //unshift
                this.tweets.unshift(response.data);
                this.body = null;
            }).catch((err)=>{
                console.log(err);
            })
        }
    }
}
</script>