# 1. 训练数据为vibration的DNN模型

> [相关代码；](./110spmdnnvibration.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/DNNVibration.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T112417Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=3ab46931d66f88627ae7e2225b37d8fd1677e2ba4cab48b6c78a40c1873db33438d138c7fcb9da921ecd78d063ae0fb30c56520ddfce8e9290257fd621bbc270aaf2bdfc5e66c3d235c180bbf744d3fe583eb44f826b7c4caa5fdd081fd3efe6fa7889046566d172e50861a5da9ec110fe16e1d88a45455e84576c20d235acdfea24c33192f5b3a8ef5f4ea343c2b553a387ab32e8680bac990c98563cc7fca1cb9c887ea42b92ada129d1d821b6dc88bad7f3faa51bcb8a60348f81649750c66c105294385b9e067296481c82fcc284c73786aeb9f8032ecc899d95c5285d3c34a6a3315069a10388f17572437e0864a8fbdd4888033e6512edd247fc798c77)

- 使用测试集获得loss函数为1.1295，准确率为0.5921；(效果较差)
- 混淆矩阵不堪入目；
- 很多类别的f1-score小于40%；
- future-DNN的模式效果不好不建议采用；

精确率衡量的是模型预测为正类的样本中，真正为正类的比例；召回率衡量的是所有正类样本中，
被模型正确预测为正类的比例。F1分数则是这两个指标的调和平均，
因此它同时考虑了模型的精确度和其对所有类别的覆盖率（或灵敏度）。
'macro': 简单地对每个类别的F1分数进行未加权平均，赋予每个类别相同的权重，不考虑它们各自的样本数。
'weighted': 对每个类别的F1分数进行加权平均，权重是每个类别的支持度（即每个类别的样本数）。
这可以看作是对每个类别重要性的一种度量。
![DNN_Vibration_Loss](../assets/pictures/DNN_Vibration_Loss.png)
![DNN_Vibration_Accuracy](../assets/pictures/DNN_Vibration_Accuracy.png)
![DNN_Vibration_ConfusionMatrix](../assets/pictures/DNN_Vibration_ConfusionMatrix.png)


| Class | Precision    | Recall | F1-Score | Support |
| ----- | ------------ | ------ | -------- | ------- |
| 0     | 0.62         | 0.31   | 0.41     | 550     |
| 1     | 0.70         | 0.88   | 0.78     | 1068    |
| 2     | 0.52         | 0.63   | 0.57     | 1074    |
| 3     | 0.61         | 0.61   | 0.61     | 1129    |
| 4     | 0.51         | 0.71   | 0.59     | 983     |
| 5     | 0.60         | 0.34   | 0.44     | 653     |
| 6     | 0.75         | 0.46   | 0.57     | 598     |
| 7     | 0.49         | 0.61   | 0.55     | 957     |
| 8     | 0.97         | 0.31   | 0.47     | 517     |
| 9     | 0.57         | 0.75   | 0.65     | 961     |
| 10    | 0.94         | 0.55   | 0.69     | 533     |
| 11    | 0.51         | 0.44   | 0.47     | 519     |
|       |              |        | Accuracy | 0.59    |
|       | Macro Avg    |        | 0.65     | 9542    |
|       | Weighted Avg |        | 0.62     | 9542    |

# 2. 训练数据为vibration的LSTM模型

> [相关代码；](./110spmlstmvibration.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/LSTMVibration.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T112510Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=688ac485e4a43f0cf52002771199ba2a62a41965e21cc96e9d03579f4d79992a99d364cc70952bcf92715d3c270913d6acaf28f86c97dc571bddc8455dd3eb6c880e8b0592a267a13d52a83f9d97d881290e0801246a60899092958534cf36e8dd73932e274606f83e18b6ceff3fa584ea1615aa3abe8c21eb01e993720403bc4acb6387a149fe3a0e2339c6318142407a9ea4ac5914a228b66fa88ce316345652a11f13a03b04883f7acb48f2dbccb6280f7be8f92588e1d356842e04a76ba7d61c256c3fd164fd94861c57db35c55133200a411e2d37709ab483abee3c082299bb51062601aae7ad6b3c6f1c8b400f89abf20d69205e2e0b2b532e4510ac32)

- loss和accuracy在训练过程中太不稳定，但accuracy幸运的达到了83%;
- loss和accuracy在训练过程中太不稳定的原因可能是噪音太多了
- 由混淆矩阵和F1-Score可看出除了11vector的判断准确率为54%以外其他的准确率都挺高；
  ![LSTM_Vibration_Loss](../assets/pictures/LSTM_Vibration_Loss.png)
  ![LSTM_Vibration_Accuracy](../assets/pictures/LSTM_Vibration_Accuracy.png)
  ![LSTM_Vibration_ConfusionMatrix](../assets/pictures/LSTM_Vibration_ConfusionMatrix.png)


  | Class | Precision    | Recall | F1-Score | Support |
  | ----- | ------------ | ------ | -------- | ------- |
  | 0     | 0.84         | 0.87   | 0.85     | 550     |
  | 1     | 0.91         | 0.96   | 0.94     | 1068    |
  | 2     | 0.83         | 0.91   | 0.87     | 1074    |
  | 3     | 0.87         | 0.86   | 0.86     | 1129    |
  | 4     | 0.81         | 0.88   | 0.84     | 983     |
  | 5     | 0.82         | 0.78   | 0.80     | 653     |
  | 6     | 0.85         | 0.77   | 0.80     | 598     |
  | 7     | 0.89         | 0.82   | 0.85     | 957     |
  | 8     | 0.70         | 0.72   | 0.71     | 517     |
  | 9     | 0.79         | 0.88   | 0.83     | 961     |
  | 10    | 0.85         | 0.82   | 0.83     | 533     |
  | 11    | 0.69         | 0.44   | 0.54     | 519     |
  |       |              |        | Accuracy | 0.83    |
  |       | Macro Avg    |        | 0.82     | 9542    |
  |       | Weighted Avg |        | 0.83     | 9542    |

# 3. 训练数据为pressure的LSTM模型

> [相关代码；](./110spmlstmpressure.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/LSTMPressure.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T112556Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=a5897efb83f255332616405bc124d319bd3ce1341530734ea895aee3fa17b35133c77662b57b8c3a725b2765a9df69f6b4b0efea1e003dced9306d56fb584aab6b8c8bfa5f7e2402695cd2c2413c5d4e6444bae706d471d2e4da5a284f5e00f9406e2d6f314bfaa5b923fc6de6591e74151977900cbdf14c1a6cce031af4bfc5755c10c440d967577411f2d909b35775443b50370769eba331b27f060a13489983e14a1774848366bc01a8718d48d25822d03e8e92a72d07c87355aec8ac2dbc7bc2b67cce6450a4461389b25c7fd8047810ce9e4c955460d77703dfe89cbe2144cd548999a63a77445267cb3b8f6128a4da747d206c8d92c77cb2794ca0b935)

- loss和accuracy在训练过程中比较稳定，但accuracy却只有73%;
- accuracy在loss和accuracy比较稳定的情况下可以通过增加训练次数来提高；(pressure序列噪音较少)
- 由混淆矩阵和F1-Score可看出大体平均，而且7vector的准确率是100%;
  ![LSTM_Pressure_Loss](../assets/pictures/LSTM_Pressure_Loss.png)
  ![LSTM_Pressure_Accuracy](../assets/pictures/LSTM_Pressure_Accuracy.png)
  ![LSTM_Pressure_ConfusionMatrix](../assets/pictures/LSTM_Pressure_ConfusionMatrix.png)


| Class | Precision    | Recall | F1-Score | Support |
| ----- | ------------ | ------ | -------- | ------- |
| 0     | 0.72         | 0.65   | 0.68     | 511     |
| 1     | 0.57         | 0.69   | 0.62     | 1090    |
| 2     | 0.76         | 0.60   | 0.67     | 1139    |
| 3     | 0.74         | 0.71   | 0.72     | 1102    |
| 4     | 0.58         | 0.80   | 0.67     | 1033    |
| 5     | 0.90         | 0.93   | 0.92     | 636     |
| 6     | 0.69         | 0.82   | 0.75     | 553     |
| 7     | 0.73         | 0.71   | 0.72     | 1015    |
| 8     | 1.00         | 1.00   | 1.00     | 514     |
| 9     | 0.73         | 0.53   | 0.61     | 921     |
| 10    | 0.81         | 0.62   | 0.70     | 499     |
| 11    | 0.91         | 0.91   | 0.91     | 529     |
|       |              |        | Accuracy | 0.72    |
|       | Macro Avg    |        | 0.76     | 9542    |
|       | Weighted Avg |        | 0.74     | 9542    |

# 4. 训练数据为strain的LSTM模型

> [相关代码；](./110spmlstmstrain.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/LSTMStrain.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T111928Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=7dfd48eaf64e8818b9ee0c416cc658c6777f2cd0400d8bfe41ff13b62e0a7560fb3680961dc07c786bc3090e65afe28c3071cd62f67c4672bd74239e13d082c0895a8f0cf31aa0190f84b8a24c691048db35dba514a90189ccfafb11f72c49f23b359d3199a91ea2bd0f9d537f4d3468b9c1f6cda73ff43ef5d81da15c5be9717ee4279b5f1ee1a190c4f5a6bff7adbb705139a4dd84cbaf2927e4db0a475acf4f7abc66c456d65da88d39e503c1a8dd23d7bd70f227d9a82128b87767abe670c69de9ab89980475f0f423dc8a69e48d18a473b49ca4bf5a91acebd06eab1d7ff97d5f7fed6e18d51b3016b0b01ee4d2e151cf9814a980a95bc4ed04c6c74405)
- loss和accuracy在训练过程中局部波动大,且accuracy只有58%;
- 由混淆矩阵的对角线数据并未连续可知，效果非常不好；
- 且在训练过程中60%的准确率似乎是由未降噪的数据导致的；

![LSTM_Strain_Loss](../assets/pictures/LSTM_Strain_Loss.png)
![LSTM_Strain_Accuracy](../assets/pictures/LSTM_Strain_Accuracy.png)
![LSTM_Strain_ConfusionMatrix](../assets/pictures/LSTM_Strain_ConfusionMatrix.png)


| Class | Precision    | Recall | F1-Score | Support |
| ----- | ------------ | ------ | -------- | ------- |
| 0     | 0.50         | 0.00   | 0.00     | 499     |
| 1     | 0.40         | 0.25   | 0.31     | 1107    |
| 2     | 0.91         | 0.60   | 0.72     | 1130    |
| 3     | 1.00         | 0.87   | 0.93     | 1068    |
| 4     | 0.25         | 0.81   | 0.38     | 949     |
| 5     | 0.00         | 0.00   | 0.00     | 607     |
| 6     | 0.45         | 0.46   | 0.45     | 554     |
| 7     | 0.43         | 0.30   | 0.35     | 995     |
| 8     | 1.00         | 1.00   | 1.00     | 539     |
| 9     | 0.88         | 1.00   | 0.93     | 1020    |
| 10    | 1.00         | 1.00   | 1.00     | 519     |
| 11    | 0.44         | 0.51   | 0.47     | 555     |
|       |              |        | Accuracy | 0.58    |
|       | Macro Avg    |        | 0.60     | 9542    |
|       | Weighted Avg |        | 0.62     | 9542    |

# 5. 训练数据为vibration的EMD-LSTM模型

> [相关代码；](./110spmemdlstmvibration.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/EMDLSTMVibration.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T095720Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=b0454998f3d5e98e4e9b1f7bbece7d809621d56012671fa80e78a53a1a0941272f1b800210cea4139a40db4c53f18bc38f347610b6e18a7e185bfdfebf35bbfd4b1da0c87659f96d1cd4bd8e98ed2edb9eb4a565e1c8b40e03b008cdf91bb35e0626a930037ad35c62edf36047e15b0439b34f563776df80defb660ac68126433a949a1a89daebc6a3867694b9868f9cce5358dab59c1623705086d147e027c98a8983d5f8ab0b677d1387903aec6a2d30fe698d55e8d7b4c016aa113bd45579ee36a6c2f529012938685301be570a599f84af9c3bbb66030136fe6fb48588e9d1cae1ec2e6ca733152368c62ccf7b419d4eae77de3540a99bcac6f0f63f68c6)


- loss和accuracy在训练过程中较为平滑，且准确率为76%。且尚未到极限，依然可以通过增加训练次数通过准确率；
- 由混淆矩阵和F1-Score可看出除了11vector的判断准确率为48%以外其他的准确率都挺高；
  ![EMDLSTM_Vibration_Loss](../assets/pictures/EMDLSTM_Vibration_Loss.png)
  ![EMDLSTM_Vibration_Accuracy](../assets/pictures/EMDLSTM_Vibration_Accuracy.png)
  ![EMDLSTM_Vibration_ConfusionMatrix](../assets/pictures/EMDLSTM_Vibration_ConfusionMatrix.png)


| Class | Precision    | Recall | F1-Score | Support |
| ----- | ------------ | ------ | -------- | ------- |
| 0     | 0.70         | 0.64   | 0.67     | 550     |
| 1     | 0.85         | 0.91   | 0.88     | 1068    |
| 2     | 0.69         | 0.84   | 0.76     | 1074    |
| 3     | 0.84         | 0.77   | 0.80     | 1129    |
| 4     | 0.74         | 0.74   | 0.74     | 983     |
| 5     | 0.72         | 0.68   | 0.70     | 653     |
| 6     | 0.78         | 0.70   | 0.74     | 598     |
| 7     | 0.77         | 0.79   | 0.78     | 957     |
| 8     | 0.67         | 0.74   | 0.70     | 517     |
| 9     | 0.73         | 0.81   | 0.76     | 961     |
| 10    | 0.87         | 0.78   | 0.82     | 533     |
| 11    | 0.64         | 0.39   | 0.48     | 519     |
|       |              |        | Accuracy | 0.76    |
|       | Macro Avg    |        | 0.75     | 9542    |
|       | Weighted Avg |        | 0.76     | 9542    |

# 6. 训练数据为pressure的EMD-LSTM模型

> [相关代码；](./110spmemdlstmpressure.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/EMDLSTMPressure.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T100120Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=2d927d78b80b5f1e25c685a038c0692710c77b4394e1c90e9599918a5ec812bbb4a9db4632584898b7933d770834eef8d251dcc0ca0b03e00f7620abfc985c6e602b9375c16f773f79b95566bcf5d2684740b0c772248455304dd4cbe83ec1422a8fc5e7f27cebd7da403f21c8431033cca113997e41190138d1571a2860d8e56fade576907820efd6772906a6aa070ffdefcac95f443aac7bac363f657c44e37e6662f18c3e7c81348a878f89b9ca0447f08efdb8f93c4571f5d8cfe67f1d0033f842feb8bfec2081ac51b8422f5fd41a2829f7be1a3ef602768d9ddadd08716e713cb7d20c3fac715b4d381094e7523849c386a97a3287974b5fc5b7187531)


- loss和accuracy在训练过程中不仅波动大，而且准确率巨低29%；
- 混淆矩阵和F1-Score效果极其不好；
- 原因是可能是是pressure序列不适应于EMD降噪，与原始的pressure序列效果相比相差太远了；

![EMDLSTM_Pressure_Loss](../assets/pictures/EMDLSTM_Pressure_Loss.png)
![EMDLSTM_Pressure_Accuracy](../assets/pictures/EMDLSTM_Pressure_Accuracy.png)
![EMDLSTM_Pressure_ConfusionMatrix](../assets/pictures/EMDLSTM_Pressure_ConfusionMatrix.png)


| Class | Precision    | Recall | F1-Score | Support |
| ----- | ------------ | ------ | -------- | ------- |
| 0     | 0.32         | 0.24   | 0.27     | 511     |
| 1     | 0.24         | 0.34   | 0.28     | 1090    |
| 2     | 0.16         | 0.09   | 0.12     | 1139    |
| 3     | 0.24         | 0.24   | 0.24     | 1102    |
| 4     | 0.16         | 0.31   | 0.21     | 1033    |
| 5     | 0.20         | 0.05   | 0.07     | 636     |
| 6     | 0.20         | 0.11   | 0.14     | 553     |
| 7     | 0.18         | 0.15   | 0.16     | 1015    |
| 8     | 0.85         | 0.99   | 0.91     | 514     |
| 9     | 0.15         | 0.30   | 0.20     | 921     |
| 10    | 0.09         | 0.00   | 0.01     | 499     |
| 11    | 0.70         | 0.33   | 0.45     | 529     |
|       |              |        | Accuracy | 0.25    |
|       | Macro Avg    |        | 0.29     | 9542    |
|       | Weighted Avg |        | 0.26     | 9542    |

# 7. 训练数据为strain的EMD-LSTM模型
> [相关代码；](./110spmemdlstmstrain.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/EMDLSTMStrain.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T100245Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=9fdf8cfbcab4622349b8406e019b6672f6c66754d9ef021ff839858e88938ebcb19e1aa0406528bae7ac8ec9b0ce90a3e419393c9a3d84e3d2ee19a753b53f46e5a5c68597554f18abc83e05250c1ab72e0976ea8a63e716ccd6e5f45fa896ac4035fa42f9cf7a43331fc5eeda38cf9661f28b70e429bafaa6a77c78fd688f8f8a860c19c5199c5e542fdeb1bf03ca7bb334abf1a0850044e81e8653ccaa71890f043ea20c72de90dcaff32f358b26919a824866726224fc55137500bc360264c63a1b65386a914f936735c6427b564feb01ed6b30831982304377fa6d97cd75e90a49e9864b246bcc71d5e5fdddeb3f725d325363fc9f0d4ec99f0486d1de55)

- loss和accuracy在训练过程中大体稳定但局部波动大，但之前相较于原始数据而已比较Loss与Accuracy的变化过程相对稳定；
- 准确率也从54%提升到了62%，且还未到极限；
- strain序列的EMD降噪效果不错；

  ![EMDLSTM_Strain_Loss](../assets/pictures/EMDLSTM_Strain_Loss.png)
  ![EMDLSTM_Strain_Accuracy](../assets/pictures/EMDLSTM_Strain_Accuracy.png)
  ![EMDLSTM_Strain_ConfusionMatrix](../assets/pictures/EMDLSTM_Strain_ConfusionMatrix.png)


  | Class | Precision    | Recall | F1-Score | Support |
  | ----- | ------------ | ------ | -------- | ------- |
  | 0     | 0.52         | 0.12   | 0.19     | 499     |
  | 1     | 0.43         | 0.43   | 0.43     | 1107    |
  | 2     | 0.77         | 0.74   | 0.75     | 1130    |
  | 3     | 0.88         | 0.87   | 0.88     | 1068    |
  | 4     | 0.33         | 0.71   | 0.45     | 949     |
  | 5     | 0.49         | 0.14   | 0.22     | 607     |
  | 6     | 0.56         | 0.59   | 0.58     | 554     |
  | 7     | 0.45         | 0.37   | 0.41     | 995     |
  | 8     | 0.98         | 0.91   | 0.95     | 539     |
  | 9     | 0.84         | 0.95   | 0.89     | 1020    |
  | 10    | 0.89         | 0.89   | 0.89     | 519     |
  | 11    | 0.52         | 0.37   | 0.43     | 555     |
  |       |              |        | Accuracy | 0.62    |
  |       | Macro Avg    |        | 0.64     | 9542    |
  |       | Weighted Avg |        | 0.63     | 9542    |

# 7. 训练数据为vibration/pressure/strain的CNN模型

> [相关代码；](./110spm3emdcnn.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/EMDCNN3.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T095418Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=afb6ea5d887792613ac93a5ae61127b02f65abf15c351ebcf3caa40710035a039c662a4bca9835e6a24120248d9af1634318df505f04efd1901172e37bfbbd5be9c2e573087aa212487a93a1309fc8d733c296294447992ae889d46f48982451ae6f753d4de414c6ed723815505f8bd7c862613161f7d4eb835f391fac97becd54f7047f9320a0e024340bce05d7417d5e7e41db4ec3987ba86b661485af280b3f740c568b3022ff46d3daccd453df14eb909bb08d86bebd4cd6af2478a24c9238894d8bff4bb5485d0ca303a18ad26e72012a45dede359cb3251f4b71892483672cbb367b544cf63f225c14190c3d9e7ee4c9b91bb16c026188e2a5c9f847b4)

- CNN的loss和accuracy效果太差了，证明vibration/pressure/strain基本上没有空间上的相关性；
  ![CNN_3_Loss](../assets/pictures/CNN_3_Loss.png)
  ![CNN_3_Accuracy](../assets/pictures/CNN_3_Accuracy.png)
  ![CNN_3_ConfusionMatrix](../assets/pictures/CNN_3_ConfusionMatrix.png)

# 8. 训练数据为vibration/pressure/strain的EMD-LSTM模型

> [相关代码；](./110spm3emdlstm.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/85876/EMDLSTM3.h5?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240731%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240731T112716Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=9ce83150ddfa64e6049c127fd9e2135db129be2f0ef0bf4ba60f643e3a558c62deb04c8e1b744362bc95485a552dda3ee49c6ec3cc017c3761727de7100ac588752fa703fb688d4ca684fca63b35c450539cb00fde2a933ee21a46fc12dd940d591b4fe239f75035da56147103eedb7aa5ba9d14df5dbe1496b89774c2237ce3457645536bd38e072faf1837b2478ba65f9ede1e4c82dc497badd22e984504e3399b8d3ef39eb81babe58c80e6a99349c5fa5d847ce9a28c24b699467a40e35dfdb58289efe4a24a8620afe55e7c2216cd87abc78fbdd833fe3fc338819fcecd8f1ea31348b0d6cde1f3d471b3ce43c2a1de3316e5be6307b4d8b587d3f82327)

- 准确率为98%,损失函数为0.0443；混淆矩阵效果好，训练中的accuracy和loss效果好
- 依然可以改进，只对vibration做EMD降噪，pressure和strain不处理更好；

 ![EMDLSTM_3_Loss](../assets/pictures/EMDLSTM_3_Loss.png)
 ![EMDLSTM_3_Accuracy](../assets/pictures/EMDLSTM_3_Accuracy.png)
 ![EMDLSTM_3_ConfusionMatrix](../assets/pictures/EMDLSTM_3_ConfusionMatrix.png)

 # 9. 训练数据为vibration/pressure/strain的DWTCNN-LSTM模型

> [相关代码；](./110spmdwtcnnlstm.ipynb)
> [模型下载；](https://storage.googleapis.com/kagglesdsdata/models/72145/91098/DWTCNNLSTM.pth?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=gcp-kaggle-com%40kaggle-161607.iam.gserviceaccount.com%2F20240808%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20240808T070347Z&X-Goog-Expires=259200&X-Goog-SignedHeaders=host&X-Goog-Signature=0f1a4bfb336ac3bdcf86280b86635deada25a25fb74a287e1beb849dabab18c20497bba079a2e0f0541f0ab24b20308cfa740caceea023164250319429405486858f34036bf71fe6044d2651dc643081d160e8ee26d24bb22f8be4d9f47b329ebb8264a26805710ae665f8e5f127cd2cc08468277f40b9730c1671e1f6d58471e8055afe5a1d88faab2fd576398d928c9fbb1fd6d3596aafeaf0023e2135dd8b233f08666a74542ead39c46679d9dd3ebbef508fdf3096eb7be0627c4233ce9877266534592807ebce5d31086c88a4117aac4da4af2995b31787af537e006d74e81d6eda427c66182ed7805c53c47b998609bad5d83374d04a05f92a54bfe582)

- 准确率为88.5%,损失函数为(0.31；混淆矩阵效果好，训练中的accuracy以及接近瓶颈和loss波动太多了。

- 依然可以改进:
- - DWTCNN中只使用了高通滤波器和低通滤波器作为了卷积核，存在滤波器的窗口太小增加估计频率的不确定性；
- - 同时未更精细化判别噪音，运用更适合的滤波器(如陷波滤波器等)；
- - 可增加DWTCNN的降采样的迭代次数提取更多信息；

 ![DWTCNNLSTM_Strain_Loss](../assets/pictures/DWTCNNLSTM_Strain_Loss.png)
 ![DWTCNNLSTM_Strain_Accuracy](../assets/pictures/DWTCNNLSTM_Strain_Accuracy.png)
 ![DWTCNNLSTM_Strain_ConfusionMatrix](../assets/pictures/DWTCNNLSTM_Strain_ConfusionMatrix.png)