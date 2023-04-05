1. **从应用程序传递到顶点函数的语义a2v**
POSITION 顶点坐标（模型空间）
NORMAL 法线（模型空间）
TANGENT 切线（模型空间）
TEXCOORD0 ~n 纹理坐标
COLOR 顶点点颜色
2. **从顶点函数传递给片元函数的时候可以使用的**
SV_POSITION 剪裁空间中的顶点坐标（一般是系统直接使用）
TEXCOORD0~7 传递纹理坐标
COLOR0 可以传递一组值 4个
COLOR1 可以传递一组值 4个

3. **片元函数传递给系统**
SV_Target 颜色值，显示到屏幕上