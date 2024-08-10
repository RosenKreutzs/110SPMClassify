# 110SPMClassify

### 1.主线
- 目标A：[Vibration](./DataAnalysis/VibrationAnalysis.md),[Pressure](./DataAnalysis/PressureAnalysis.md),[Strain]((./DataAnalysis/StrainAnalysis.md))的数据分析;
- 目标B：[不同模型的效果对比](./ModelsContrast/ModelsAnalysis.md);
- 目标C：模态分解方法的效果对比;


### 2.anconda环境

> 环境名：110SPMEnv;

- 打包环境

``conda env export > environment.yml``

- 加载环境

``conda env create -f environment.yml``

### 3.突出点
- 自定义的由离散离散小波变换原理构成的[小波卷积层DWTCNN](./ModelsContrast/110spmdwtcnnlstm.ipynb)

### 4.未完成事项
- EMD的个人理解版本2；
- - EEMD的个人理解；
- - CEEMDAN的个人理解;
- - CEEMD的个人理解;
- - FCEEMD的个人理解;
- - ICEEMDAN的个人理解;
- - LMD的个人理解;
- - RLMD的个人理解;
- - Go_emd的个人理解;

- VMD的个人理解版本2；

- FFT的个人理解版本2；
- - CWT的个人理解版本2
- - DWT的个人理解；

- CWTCNN卷积层的构建；
- KANs框架的构建；
- 再梳理一下论文，看看要学的部分；
