<template>
    <div class="game" @touchmove.stop.prevent>
        <canvas ref="canvas"></canvas>
    </div>
</template>

<script>
    import flash from './lib/flash/flashScroller';
    export default {
        data(){
            return{
            }
        },
        mounted(){
            new flash(this.$refs.canvas,this.$parent.getAssets(),{

            });
        },
        methods:{
        },
        components:{
        }
    };
</script>

<style lang="postcss" scoped>
.game{
    &,canvas{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }
}
</style>
