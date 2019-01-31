<template>
    <div class="app" ref="app">
        <transition name="fadeout">
            <Game v-if="pageIndex===0"/>
            <Loading v-if="pageIndex===-1" :assets="loadAssets" @complete="loadComplete"/>
        </transition>
        <audio src="../assets/song.mp3" loop="loop" ref="audio"></audio>
    </div>
</template>

<script>
    import Loading from 'Components/loading/App';
    import Game from './Game.vue';
    let assets;
    export default {
        data(){
            return{
                loadAssets:require.context("../assets", true, /\.(png|jpg)$/i),
                pageIndex:-1
            }
        },
        mounted(){
            this.$refs.app.ontouchstart = ()=>{
                this.$refs.app.ontouchstart = null;
                this.$refs.audio.play();
            };
        },
        methods:{
            loadComplete(res){
                assets = res;
                this.pageIndex = 0;
            },
            getAssets(){
                return this.loadAssets;
                return assets;
            }
        },
        components:{
            Loading,Game
        }
    };
</script>

<style lang="postcss" scoped>

</style>
