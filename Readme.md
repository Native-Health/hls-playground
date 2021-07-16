## Playground for HLS streams

### Features
* script to convert mp4 to adaptive HLS [`create-vod-hls`](./create-vod-hls.sh)
  * by default works with **horizontal** videos
* static server to serve HLS


### Serving HLS

HLS streams can be natively played in Safari Browser
* Run `yarn serve`
  
  Currently serving
  * Horizontal
    * http://localhost:3474/media/highway-between-trees/playlist.m3u8
    * http://localhost:3474/media/seashore/playlist.m3u8
  * Vertical
    * http://localhost:3474/media/skatepark/playlist.m3u8

### Converting mp4 to HLS
**Horizontal videos**

The script works without modification for **horizontal** videos
* `sh create-vod-hls.sh mp4s/highway-between-trees.mp4 media/highway-between-trees`

**Vertical videos**

* Comment out lines 11:19 in [`create-vod-hls`](./create-vod-hls.sh)
* Uncomment lines 21:30
* `sh create-vod-hls.sh mp4s/skatepark.mp4 media/skatepark`

### Requirements
* `ffmpeg` installed and available on `PATH`


### Useful commands

* Compress large mp4s
  * `ffmpeg -i <input_filename>.mp4 -vcodec libx264 -crf 28 <output_filename>.mp4`

* Get number of frames of mp4
  * `mediainfo --Output="Video;%FrameCount%" mp4s/highway-between-trees.mp4`
  
  `944`

* Show mp4 info
  * `ffprobe -hide_banner mp4s/highway-between-trees.mp4`

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'mp4s/highway-between-trees.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf58.76.100
  Duration: 00:00:39.37, start: 0.000000, bitrate: 1097 kb/s
  Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p(tv, bt709), 1920x1080 [SAR 1:1 DAR 16:9], 1094 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc (default)
    Metadata:
      handler_name    : ETI ISO Video Media Handler
      vendor_id       : [0][0][0][0]
```
### Assets used
* Horizontal videos
  * [highway-between-trees.mp4](https://mixkit.co/free-stock-video/highway-between-trees-506/)
  * [seashore.mp4](https://mixkit.co/free-stock-video/top-aerial-shot-of-seashore-with-rocks-1090/)

* Portrait videos
  * [skatepark.mp4](https://mixkit.co/free-stock-video/top-aerial-shot-of-a-skater-skating-on-a-half-1364/)
