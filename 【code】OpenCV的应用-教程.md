### 一、基于openCV + mediapipe 的人脸识别应用  

wiki整理：OpenCV+mediapipe+python实现视频、实时摄像头人脸检测: 安装依赖 numpy——Python-pip /usr/local/Cellar/opencv/4.5.3_2

/usr/local/Cellar/opencv/4.5.3_2/lib/python3.9/site-packages/cv2/python-3.9/cv2.cpython-39-darwin.so

brew unlink opencv && brew link –force opencv

路线1：高清点数 1、安装依赖mediapipe， pip install mediapipe（完成） 2、OpenCV 调用摄像头（完成） 3、机器性能（完成，用FPS抽帧） 4、TPC通信 5、MySQL数据库


### 二、基于openCV + dlib 的眨眼识别  
1、参考链接  
https://www.pyimagesearch.com/2017/04/24/eye-blink-detection-opencv-python-dlib/    
2、这是CSDN关于【[疲劳检测](https://blog.csdn.net/tzh1342761595/article/details/107525749?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164069506216780366530429%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=164069506216780366530429&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-5-107525749.pc_search_result_cache&utm_term=opencv+%E7%9D%81%E9%97%AD%E7%9C%BC%E6%A3%80%E6%B5%8B&spm=1018.2226.3001.4187)】的应用实现  

3、这是CSDN用眨眼、张嘴实现【[活体检测](https://blog.csdn.net/Lee_01/article/details/89151044?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522164069506216780366530429%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=164069506216780366530429&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-27-89151044.pc_search_result_cache&utm_term=opencv+%E7%9D%81%E9%97%AD%E7%9C%BC%E6%A3%80%E6%B5%8B&spm=1018.2226.3001.4187)】  


4、这里是关于绝对面积的说法：   
https://stackoverflow.com/questions/65676833/problem-in-my-python-code-that-eye-blinks-are-too-many-detected-using-eye-aspe   

### 三、基于openCV + mediapipe实现的瞳孔追踪      
https://google.github.io/mediapipe/solutions/iris.html     


### 四、基于OpenCV-Python 实现简单数字识别 OCR   

参考链接  
https://stackoverflow.com/questions/9413216/simple-digit-recognition-ocr-in-opencv-python?rq=1  

### 五、Python中计算任意两个向量的夹角    
参考链接  
https://www.jb51.net/article/164697.htm  

