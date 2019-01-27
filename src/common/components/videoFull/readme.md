# 全屏视频模块

 - vue全屏视频模块
 
## 用法
 - props: 
     - `autoplay <Boolean>`: 自动播放 默认：true
     - `src <string>`: video url
     - `poster <string>`: video 预加载图片
 - emmit:
     - `videoEnd <function>`: video结束回调
     
     - 例子:
     
       ```html
        <template>
           	<VideoFull ref="videoFull" :src="video" @videoEnd="videoEnd" />
        </template>
        <script >
               import VideoFull from 'Components/videoFull/App.vue';
               import configURL from 'Js/config.url';
               export default {
                    data(){
						return{
							video:configURL.video
						}
                    },
					methods:{
						videoEnd(){
						}
					},
					components:{
						VideoFull
					}
				}
        </script>
        <style scoped>
           >>> .video-full{
               .play-icon{
                   background: url("../assets/video-btn.png");
               }
           }
        </style>
       ```
