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
高光反射 Specular=直射光*pow（max（cos，0），高光参数x）角度是反射光方向和视野方向的夹角
漫反射 Diffuse=直射光颜色*maxn（cos（光和法线））
环境光
5. **关键字**
`#include"Lighting.cginc"` **光照头文件**
`-WorldSpaceLightPos0.xyz` **入射平行光的位置**
`_LightColor0.rgb` **光照颜色**

`normalize()` **对向量进行单位化**
`mul()` **矩阵点乘**
`UnityObjectToClipPos()` **将物体空间的点转化为剪裁空间的点**
`UNITY_LIGHTMODEL_AMBIENT.rgb` **获取环境光（由skybox得到）**
`max(n1,n2)` **两个数取最大的**
`dot(n1,n2)` **向量点乘**
`pow（x，y`）**x的y次方**
`reflect(入射光单位向量，物体发法线)` **计算反射光方向**
`_WorldSpaceCameraPos.xyz` **获取摄像机的世界坐标**

6. **UnityCG.cginc 中一些常用函数**
   1. **摄像机方向（视角方向）**
`float3 WorldSpaceViewDir(float4 v)` **根据模型空间中的顶点坐标 得到 （世界空间）这个点到摄像机的观察方向**
`float3 UnityWorldSpaceViewDir(float4 v)` **世界空间中的顶点坐标 ->世界坐标下这个点到摄像机的观察方向**
`float3 ObjSpaceViewDir(float4 v)` **模型空间顶点坐标->模型空间下这个点到摄像机的观察方向**
   2. **光源方向**
`float3 WorldSpaceLightDir(float4 v)` **模型空间中的顶点坐标->世界空间下这个点到光源的方向**
`float3 UnityWorldSpaceLightDir(float4 v)` **世界空间中的顶点坐标->世界坐标下这个点到光源的方向**
`float3 ObjSpaceLightDir(float4 v)` **模型空间顶点坐标->模型空间下这个点到光源的方向**
   3. **方向转换**
`float3 UnityObjectToWorldNormal(float3 norm)` **把法线方向 模型空间->世界空间**
`float3 UnityObjectToWorldDir(float3 Dir)` **把方向 模型空间->世界空间**
`float3 UnityWorldToObjectDir(float3 Dir)`  **把方向 世界空间->模型空间**

`TANGENT_SPACE_ROTATION` **调用函数后，会得到将模型空间下方向转换到切线空间下的矩阵

**法线贴图上像素与对应的法线的关系** `像素=（法线+1）/2`