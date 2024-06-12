# 基於單張靜態影像偵測水質RPI值

這個專案旨在開發一個程式，該程式能夠從單張靜態影像中偵測水質的 RPI（Remote Pixel Index）值。RPI 是一種用於評估水質的指標，可以通過分析水體中的色彩來推斷水質的清潔程度。

## 組員
* 409410094 陳翰儒 (組長) [Future-Outlier](https://github.com/Future-Outlier)
* 409335047 江若綾 [Zoey](https://github.com/zoey0106)
* 409410049 黃子祥 [Hsiang916](https://github.com/Hsiang916)
* 409510049 孫渝鈞 [Yu-Jun Sun](https://github.com/SunYujun0725)
* 410410020 楊其龍 [ben99933](https://github.com/ben99933)
* 410410064 蘇靖淵 [jamessu1201](https://github.com/jamessu1201)

## 使用方法

1. git clone 這個專案

```git clone https://github.com/CCUDL/DL2024_Team5_Image_RPI_Prediction.git```

2. 安裝必要的套件

```pip install -r requirements.txt```

3. 執行model_train.ipynb 以訓練模型
4. 如需要現成的模型，可以直接到google drive這邊下載[這個檔案](https://drive.google.com/file/d/1qK3SpwMvajhWQjhCCl_oHOZLKKIbU5hV/view?usp=sharing)


## 檔案說明

1. requirements.txt: 用於安裝必要套件的檔案
2. model_evalu_big.ipynb: 訓練+評估的原始模型 (1,391,387 params)
3. model_small_3_Kfold.ipynb: 使用小模型(45,233 params)加上kfold預測
4. model_DO_eval.ipynb: 使用照片預測DO溶氧量值 (失敗) (會在報告時補上原因)
5. ./水質檢測/ : 包含了訓練模型所需的資料集 (請參考下方的資料集說明)

## 資料集

由於本資料集屬於非公開的資料集，如有需要請聯絡[熊博安](mailto:pahsiung@cs.ccu.edu.tw)老師(pahsiung@cs.ccu.edu.tw)

## 專案說明

由於我們資料集只有六個影片，
影片內容為無人機空拍河流之圖片，
以及配合該次空拍所測得的水質數據，
包含酸鹼值、DO、COD、BOD、SS、NH3-N、TP、TN等數據，
我們將這些數據轉換成RPI值，
根據[全國環境水質監測資訊網](https://wq.moenv.gov.tw/EWQP/zh/Encyclopedia/NounDefinition/Pedia_37.aspx)對於RPI值的定義:
RPI值為DO（mg/L）、BOD5（mg/L）、NH3-N（mg/L）、SS（mg/L）共4項指標的點數取平均值。

此專案將影片的每一幀切割成圖片作為資料集，並將次空拍所測得的RPI值作為標籤，
利用CNN模型來預測該張圖片的RPI值。

## License

[MIT](https://github.com/CCUDL/DL2024_Team5_Image_RPI_Prediction?tab=MIT-1-ov-file#readme)
