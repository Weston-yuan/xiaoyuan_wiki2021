参考教程：  

[https://www.youtube.com/watch?v=nPW6tKeapsM](https://www.youtube.com/watch?v=nPW6tKeapsM)  

### 一、初始化 + 游戏循环   

<img src="https://i.loli.net/2021/11/29/aH2l1ciFBdvXyTe.png" width="40%">  

<img src="https://i.loli.net/2021/11/29/oZBRh51pbze7cGa.png" width="40%">  


### 二、C#调用其他脚本的函数/变量    

* 第一种，被调用脚本函数为static类型，调用时直接用  脚本名.函数名()。很不实用……
* 第二种，GameObject.Find("脚本所在物体名").SendMessage("函数名");  此种方法可以调用public和private类型函数
* 第三种，GameObject.Find("脚本所在物体名").GetComponent<脚本名>().函数名();此种方法只可以调用public类型函数   
例如：   
GameObject.Find("Canvas/MainManu/UI").SetActive(true);   

eg.  
```
public class eyeup : MonoBehaviour
{
    int eye_close;
    void Start()
    {
        //这里得调用 unityserver.cs 里的 ReceiveData() ，再获取 eye_close 的值
        GameObject.Find("eyebrow").SendMessage("ReceiveData");
        eye_close = GameObject.Find("eyebrow").GetComponent<unityserver>().eye_close;
    }
```

### 三、动画的引入/编辑   

1、先在 Assets 创建 “animation controller” ；  
2、点选 gameobject ，右侧栏 add component 新增“animator”；   
3、将[1]创建的“animation controller” 赋值到[2]“animator”的“controller”；   
4、在“animation controller” 内创建 animation 并拖入关键帧图片、调整速率、组装动画；   
5、顶部工具栏window —— 打开animator窗口 —— 将animation动画拖入该窗口 —— 编辑/切换动画播放顺序（定义触发动画的bool/triggle,并在脚本中进行编辑/赋值）； 

### 四、图片的引入 + 图层   

1、先在 Assets 拖入图片素材；   
2、点选 gameobject ，右侧栏 add component 新增 “sprite renderer",赋值"sprite";     
3、若看不到图片，在Inspector页面中，修改“Texture Type”属性为“Sprite （2D and UI）”    

<img src="https://s2.loli.net/2021/12/20/7R8mFTQZ39NCJXL.png" width="20%">  

4、图层：sorting layers图层分组；order in layer组内图层排序；  


### 五、场景切换SceneManagement  

加载下一个场景： SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);    
参考链接：[第21课](https://www.bilibili.com/video/BV1gJ411374p?spm_id_from=333.999.0.0)  

### 六、UI组件 + canvas     
1、UI组件都在canvas的容器里展示，canvas自动生成eventSystem；  
2、用于编辑UI的canvas画布独立于游戏主界面；  
3、用以调整组件相对中心点的位置；     
<img src="https://s2.loli.net/2021/12/20/2Wykj9QDMoAgPTu.png" width="50%">   

4、UI组件的脚本联动，参考[第12课](https://www.bilibili.com/video/BV1Z4411z7MZ?spm_id_from=333.999.0.0)    
5、dialog组件：选中canvas，创建panel（panel组件覆盖于游戏界面上方，调整其属性以适应设定）；  [参考第19课](https://www.bilibili.com/video/BV1b4411y7yq?spm_id_from=333.999.0.0)    
6、引入字体：Assets Store中购买并引入字体；   

 
build打包，第30课   
dialog，第19课   


十、Assets Store资源引入  
可在Assets Store买一些免费的字体、音效、bgm、图片等素材   





