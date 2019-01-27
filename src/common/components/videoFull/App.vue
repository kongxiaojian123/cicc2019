<template>
	<div class="video-full">
		<video
				:src="src"
				:poster="poster"
				:autoplay="autoplay"
				@click="play"
				@ended="$emit('videoEnd')"
				ref='video'
				class="video"
				x-webkit-airplay="true"
				playsinline="true"
				webkit-playsinline="true"
				x5-video-player-type="h5"
				x5-video-player-fullscreen="true"></video>

		<div v-if='!playFlag' class="video-poster" @click='play' :style="{backgroundImage:poster?'url('+poster+')':'none'}">
			<span class="play-icon"></span>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
            autoplay: {
                type: Boolean,
                default: true
            },
            src: String,
            poster: String,
		},
		data() {
			return {
                playFlag: false,
			}
		},
		mounted() {
            if(window.netease) window.netease.autoPlay(()=>{
                if(this.autoplay){
                    this.play();
				}else{
                    this.$refs.video.load();
				}
			});
		},
		methods: {
            play() {
			    this.playFlag = true;
                this.$refs.video.play();
            },
            stop() {
                this.playFlag = false;
                this.$refs.video.pause();
            },
		},
		components: {}
	};
</script>
<style lang="postcss">
	.video-full {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: #000;
		.video {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}
		.video-poster{
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background: #000 no-repeat center;
			background-size: cover;
			.play-icon{
				position: absolute;
				top: 50%;
				left: 50%;
				transform: translate(-50%, -50%);
			}
		}
	}
</style>
