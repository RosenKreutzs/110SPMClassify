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
- [EEMD的个人理解；](./DecompositionContrast/EMD/EEMD/EEMD.md)
- [CEEMD的个人理解；](./DecompositionContrast/EMD/CEEMD/CEEMD.md)
- [CEEMDAN的个人理解；](./DecompositionContrast/EMD/CEEMDAN/CEEMDAN.md)
- [ICEEMDAN的个人理解；](./DecompositionContrast/EMD/ICEEMDAN/ICEEMDAN.md)
- [Go_EMD的个人理解；](./DecompositionContrast/EMD/Go_EMD/Go_EMD.md)
- [LMD的个人理解；](./DecompositionContrast/EMD/LMD/LMD.md)
- [RLMD的个人理解；](./DecompositionContrast/EMD/RLMD/RLMD.md)
- [FT的个人理解；](./DecompositionContrast/FT/FT/FT.md)
### 4.未完成事项

- CWTCNN卷积层的构建；
- 探究一下奇异值分解构建自定义层的可实现性；
- KANs框架的构建；
- TFN的复现
- 再梳理一下论文，看看要学的部分；
