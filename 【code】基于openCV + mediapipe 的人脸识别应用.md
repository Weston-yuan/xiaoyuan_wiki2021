wiki整理：OpenCV+mediapipe+python实现视频、实时摄像头人脸检测: 
安装依赖
numpy——Python-pip
 /usr/local/Cellar/opencv/4.5.3_2

/usr/local/Cellar/opencv/4.5.3_2/lib/python3.9/site-packages/cv2/python-3.9/cv2.cpython-39-darwin.so

brew unlink opencv && brew link --force opencv  



路线1：高清点数
1、安装依赖mediapipe， pip install mediapipe（完成）
2、OpenCV 调用摄像头（完成）
3、机器性能（完成，用FPS抽帧）
4、TPC通信
5、MySQL数据库