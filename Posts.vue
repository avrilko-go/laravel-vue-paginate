<template>
    <div class="container">
        <div class="row">
            <div class="col-lg-10 col-lg-offset-1" >
                <div class="panel panel-default">
                    <div class="panel-heading">
                        <h3 class="panel-title">文章内容</h3>
                    </div>
                    <div class="panel-body">
                        <ul>
                            <li v-for="(post,index) in posts">
                                <a href=""><h4>{{post.title}}</h4></a>
                                <p>{{post.body}}</p>
                            </li>
                        </ul>
                    </div>
                </div>
                <paginate :data="data" @getPosts="getPosts"></paginate>
            </div>
        </div>
    </div>
</template>

<script>
    import Paginate from '../common/Paginate'
    export default {
        components: {Paginate},
        name:'Posts',
        data(){
            return {
                posts:[],
                data:{}
            }
        },
        computed:{

        },
        mounted(){
            this.getPosts();
        },
        methods:{
            getPosts(url=''){
                let postUrl;
                if(url){
                    postUrl=url;
                }else{
                    postUrl='api/posts';
                }
                axios.get(postUrl).then((result)=>{
                    this.posts=result.data.data;
                    this.data=result.data;
                })
            }
        }
    }
</script>

<style lang="scss" scoped>
    ul {
        list-style: none;
        padding: 0;
        margin: 0;
        li {
            padding: 10px;
            h4 {
                padding: 0;
                margin: 0;
            }
        }
    }
</style>
