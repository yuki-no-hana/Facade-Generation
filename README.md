![](https://github.com/pilipiliwang/Facade_Gengames_2022/blob/main/FacadewebGIF_.gif)

# Facade_Gengames_2022
This is a facade generation demo based on [pix2pix](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix).
## Installation
- clone this repo:

       git clone https://github.com/junyanz/pytorch-CycleGAN-and-pix2pixhttps://github.com/pilipiliwang/Facade_Gengames_2022.git
 
  
- necessary library：
  - pytorch\flask\numpy\json\PIL
  - Since threejs and Web commands are written in JavaScript, some js files will be downloaded automatically after running. It is recommended to use the server in the United States, otherwise it is easy to report an error
## Run
- Pretrained pix2pix download
  - create ‘checkpoints’ folder，download model from[baidu网盘](链接：https://pan.baidu.com/s/1RMM093Jv-E8Xo7v9kf52sw 提取码：ogyj )
- build labelcanvas folder in static/images or modify the code below：
 
        cropArea = img[y0:y1,x0:x1]
        route = 'static/images/labelcanvas/imgcutted_'+str(i)+'.png' 
        print(route)
        cv2.imwrite(route,cropArea)
        
   It's worthy norting that you need to manually delete the labelcanvas every time.
## Description
- The code for load&run of the pix2pix model is in flask.app, generally only need to modify the path of .pth, which is the pytorch model file
- Codes related to 3D models are in static/test3D.js; codes related to 2D drawing are in static/sketch.js. If you need to modify the drawing method or the characteristics of the label, you need to modify these two files at the same time and retrain the model
- The code related to the web interface is in templates/home.html, and the CSS style is in static/style.css
## Some bugs
- 现在点击trasfer两次，才会在outputcanvas里面出现pix2pix生成的图片，而此时3Dcanvas里面已经被贴上了pix2pix生成图片。这应该是因为点击操作的问题，暂时没有去解决
- THREEJS关于窗洞布尔运算没有实现，原因是toshapes命令在进行多次扣洞的布尔运算的时候，旋转方向出现了错误。目前用墙体后退的方式从视觉效果上解决这个问题，后续可以优化
