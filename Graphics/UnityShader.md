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

4. **光照**
自发光
高光反射 Specular
漫反射 Diffuse=直射光颜色*cos（光和法线）
环境光

#include"Lighting.cginc" **光照头文件**
-WorldSpaceLightPos0.xyz **入射平行光的位置**
_LightColor0.rgb **光照颜色**

normalize() **对向量进行单位化**
mul() **矩阵点乘**
UnityObjectToClipPos() **将物体空间的点转化为剪裁空间的点**
UNITY_LIGHTMODEL_AMBIENT.rgb **获取环境光（由skybox得到）**
max(n1,n2) **两个数取最大的**
dot(n1,n2) **向量点乘**