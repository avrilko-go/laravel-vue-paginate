<template>
    <nav >
        <ul class="pagination">
            <li v-show="prev_page_url" @click="getPosts(prev_page_url)"><span aria-hidden="true">«</span></li>
            <li :class="{'active':number==current_page}" @click.prevent="getPosts(path+'?page='+number)"  v-for="(number,index) in last_page"><a href="">{{number}}</a></li>
            <li v-show="next_page_url" @click="getPosts(next_page_url)"><span aria-hidden="true">»</span></li>
        </ul>
    </nav>
</template>

<script>
    export default {
        name:'Paginate',
        props:['data'],
        computed:{
            current_page(){
                return this.data.current_page
            },
            prev_page_url(){
                return this.data.prev_page_url
            },
            next_page_url(){
                return this.data.next_page_url;
            },
            path(){
                return this.data.path;
            },
            last_page(){
                return this.data.last_page;
            }
        },
        methods:{
            getPosts(url){
                this.$emit('getPosts',url)
            }
        }
    }
</script>

