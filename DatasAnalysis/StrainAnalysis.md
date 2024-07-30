# 应变时间序列的分析：(strain)

## 1. 分析应变原始数据

- 描述：12个一维序列表示的应变；
- 分别显示,完整序列,0-5000序列,500000-550000序列,800000-810000序列；
- 由肉眼即可看出各不同序列的不同显示图具有较强的区分性和规律性；
  ![complete_strain](./assets/pictures/complete_strain.png)
  ![5000_strain](./assets/pictures/5000_strain.png)
  ![500000_strain](./assets/pictures/500000_strain.png)
  ![8000000_strain](./assets/pictures/8000000_strain.png)

## 2.  绘制数据长度对样本摘的影响的曲线图¶(strain)

- 根据曲线图确认样本片段的长度(由于样本熵基本在200后波动不大，沿用vibration的分块长度512)

90年代初提出的近似熵简记为的概念是从衡量时间序列复杂性的角度来度量信号，它依据的是序列中产生新模式的概率大小 ，
如果一个序列产生新模式的概率越大 ， 那么此序列的复杂性就越大 ，相应的近似熵的值就越大 。
近似熵可以用来描述振动 信号的复杂性和不规则性 ，通过比较不同运行期间内机械设备近似熵的变化情况 ，
可以反映该机械设备在此期间的运行状况 。样本摘简记为是近似熵的改进算法， 它的优越性在于可以较少地依赖于时间序列长度 。
![entropies_strain](./assets/pictures/entropies_strain.png)

## 3. 按重复度为50%，固定长度为512进行分解为小片段；(strain)

![split_strain](./assets/pictures/split_strain.png)

## 4. 提取统计量特征(strain)

- 有量纲的特征(均值mean、标准差std、最大值max、最小值min、中位数median、偏度skew、峰度kurt),无量纲的特征(峰值指标peak_factor,裕度指标clearance_factor,峭度指标kurtosis,脉冲指标impulse_factor)。
- 统计量特征区分性比pressure和vibration要好，但不多；

注释：量纲，表存在不同物理量关系；有量纲特征值的数值大小常因负载，转速等条件的变化而变化， 给工程应用带来一定的困难。因此机械故障诊断中还釆用了多种无量纲指标；

![mean_strain](./assets/pictures/mean_strain.png)
![std_strain](./assets/pictures/std_strain.png)
![median_strain](./assets/pictures/median_strain.png)
![max_strain](./assets/pictures/max_strain.png)
![min_strain](./assets/pictures/min_strain.png)
![skew_strain](./assets/pictures/skew_strain.png)
![kurt_strain](./assets/pictures/kurt_strain.png)
![peak_strain](./assets/pictures/peak_strain.png)
![kurtosiss_strain](./assets/pictures/kurtosiss_strain.png)
![impulse_strain](./assets/pictures/impulse_strain.png)
![clearance_strain](./assets/pictures/clearance_strain.png)

## 5. 提取频域特征(strain)

- 由不同类型各自的4个片段的频谱图得，主频大都是靠近0，幅值有部分区分性；
- 相同类型的主频幅值的有两到三个范围;
- 不同类型的主频幅值分布情况与统计量特征的均值分布基本相同；

![100_fft_strain](./assets/pictures/100_fft_strain.png)
![1000_fft_strain](./assets/pictures/1000_fft_strain.png)
![2000_fft_strain](./assets/pictures/2000_fft_strain.png)
![3000_fft_strain](./assets/pictures/3000_fft_strain.png)

## 6. 时域特征(strain)

- 由于strain显示的都是正加速度无过零率，不算；
- 不计算互相关性函数；
- 自相关性函数由可知具无区别性；
  ![100_autocorr_strain](./assets/pictures/100_autocorr_strain.png)
  ![1000_autocorr_strain](./assets/pictures/1000_autocorr_strain.png)
  ![2000_autocorr_strain](./assets/pictures/2000_autocorr_strain.png)
  ![3000_autocorr_strain](./assets/pictures/3000_autocorr_strain.png)
  ![max_autocorr_strain](./assets/pictures/max_autocorr_strain.png)

## 7. 时频特征(strain)

- 使用EMD分解后去高频噪音数据(K小于0.1的IMF)后再重构；
- 综合评价指标K为方差贡献率和相关性的组合运算结果，表IMF与原始信号的相关性和贡献度,用其确定高频噪音；
  ![IMFs_strain](./assets/pictures/IMFs_strain.png)
  ![EMD_strain](./assets/pictures/EMD_strain.png)
