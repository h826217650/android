# 应用启动时间

【背景】  
 基于android程序的执行流程，即activity经历onCreate(),onStart(),onResume(),onPause(),onStop(),onDestroy()， 只要获得activityManager的启动时间，就能知道apk的启动时间。   

```python
 * adb logcat | grep AcaptivityManager
 * adb logcat -c && adb logcat -s ActivityManager | grep "Displayed"

```
# 页面渲染性能

【背景】  
 android页面帧绘制过程： 计算视图大小（measure）-> 安置视图位置(layout) -> 绘制视图(draw)。只要收集到每帧的处理时间，就可以得到页面的渲染性能。（fps记录页面渲染）。  
 ```python
 * 开发者选项中 打开“GPU呈现模式分析”
 * adb shell dumpsys gfxinfo com.smile.gifmaker
 * 把profile数据段的 Draw Process Execute相加即为每帧渲染时间
 
 ```  
 

