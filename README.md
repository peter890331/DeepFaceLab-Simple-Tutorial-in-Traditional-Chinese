# DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese
關於 DeepFaceLab 的繁體中文簡易教學。

## 💢請勿使用在非法或可能傷害他人權益的用途。💢

參考自 YouTube 影片：    
[deepfacelab模型训练，换脸教程，绝对是全网最详细的！#deepface #Ai换脸#chatgpt #midjourney #deepfacelab #deepfacelive #直播换脸][1]

在此只介紹最簡易的功能，詳細可以直接觀看影片，例如修正人臉辨識錯誤的功能。

[1]: https://youtu.be/6-KPIXEajk8

<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/404410172-f6d7f3bc-697a-4af4-bc5e-82f8398e0a48.png" width="1000px">

## [DeepFaceLab][2]
Releases：[Windows (Mega.nz)][3].    
DeepFaceLab_NVIDIA_RTX3000_series_build_11_20_2021.exe 適合 RTX3060 以上的顯卡；    
DeepFaceLab_NVIDIA_up_to_RTX2080Ti_build_11_20_2021.exe 適合 RTX3060 以下的顯卡。 

其 [GitHub][2] 中還有其他下載連結。

在此以 DeepFaceLab_NVIDIA_RTX3000_series_build_11_20_2021.exe 為例，下載後解壓縮成資料夾，    
<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/404389636-0a2d30a8-88f7-4c44-bfb2-a98f308e683d.png" width="500px">

---

在解壓縮後的資料夾中，**workspace** 是工作區域，儲存要摳臉的影片和要換臉的影片，以及其他結果。    

將要摳臉的影片存入 workspace 並命名為 **data_src.mp4**；    
將要換臉的影片存入 workspace 並命名為 **data_dst.mp4**。      
<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/404409391-e1621411-bfb4-45f3-9914-4127c370d437.png" width="150px">

---

在確認好兩者影片後，點擊 **2) extract images from video data_src.bat**，將要摳臉的影片一幀一幀切開。    

- [0] Enter FPS ( ?:help ) : 選擇幀率，默認為 0，可以依 data_src.mp4 的幀率調整。    
- [png] Output image format ( png/jpg ?:help ) : 切開的圖片格式，默認為 png。

完成後可以查看 workspace/data_src，會看到要摳臉的影片被一幀一幀切開的圖片。

---

接著點擊 **3) extract images from video data_dst FULL FPS.bat**，將要換臉的影片一幀一幀切開。    

- [png] Output image format ( png/jpg ?:help ) : 切開的圖片格式，默認為 png。    

完成後可以查看 workspace/data_dst，會看到要換臉的影片被一幀一幀切開的圖片。

---

接著點擊 **4) data_src faceset extract.bat**，將要摳臉圖片中的人臉再切出來。

- [CPU] : CPU    
  [0] : NVIDIA GeForce RTX XXXX    
  [0] Which GPU indexes to choose? : 選擇使用 CPU 還是使用顯卡，一定要使用顯卡，默認為 0。
- [wf] Face type ( f/wf/head ?:help ) : 選擇要切出來的人臉類型，f(臉)、wf(整張臉)、head(頭)，默認為 wf。
- [0] Max number of faces from image ( ?:help ) : 摳臉圖片中的人臉的最大數量，默認為 0。
- [512] Image size ( 256-2048 ?:help ) : 選擇要切出來的人臉大小，默認為 512，可以自行調整。
- [90] Jpeg quality ( 1-100 ?:help ) : 選擇要切出來的人臉品質，默認為 90。
- [n] Write debug images to aligned_debug? ( y/n ) : 選擇是否要生成一份 debug 文件，默認為 n，但建議生成，選擇 y。

完成後可以查看 workspace/data_src/aligned，會看到摳臉圖片中的人臉再切出來的圖片；    
和 workspace/data_src/aligned_debug，會看到 debug 文件。

---

再來，點擊 **4.2) data_src sort.bat**，排序 workspace/data_src/aligned 中的圖片，方便手動刪除不必要的人臉。

- Choose sorting method:    
  [0] blur    
  \[1] motion_blur    
  \[2] face yaw direction    
  \[3] face pitch direction    
  [4] face rect size in source image    
  [5] histogram similarity    
  [6] histogram dissimilarity    
  [7] brightness    
  [8] hue    
  [9] amount of black pixels    
  [10] original filename    
  [11] one face in image    
  [12] absolute pixel difference    
  [13] best faces    
  [14] best faces faster    
  [5] : 選擇需要的排序方法，默認為 5。

手動刪除 workspace/data_src/aligned 中不必要的人臉，包括不是要摳臉的對象、不相關、模糊、遭到遮擋的人臉。

---

接著點擊 **5) data_dst faceset extract.bat**，將要換臉圖片中的人臉再切出來。

- [CPU] : CPU    
  [0] : NVIDIA GeForce RTX XXXX    
  [0] Which GPU indexes to choose? : 選擇使用 CPU 還是使用顯卡，一定要使用顯卡，默認為 0。
- [wf] Face type ( f/wf/head ?:help ) : 選擇要切出來的人臉類型，f(臉)、wf(整張臉)、head(頭)，默認為 wf。
- [512] Image size ( 256-2048 ?:help ) : 選擇要切出來的人臉大小，默認為 512，可以自行調整。
- [90] Jpeg quality ( 1-100 ?:help ) : 選擇要切出來的人臉品質，默認為 90。

完成後可以查看 workspace/data_dst/aligned，會看到換臉圖片中的人臉再切出來的圖片。

---

再來，點擊 **5.2) data_dst sort.bat**，排序 workspace/data_dst/aligned 中的圖片，方便手動刪除不必要的人臉。

- Choose sorting method:    
  [0] blur    
  \[1] motion_blur    
  \[2] face yaw direction    
  \[3] face pitch direction    
  [4] face rect size in source image    
  [5] histogram similarity    
  [6] histogram dissimilarity    
  [7] brightness    
  [8] hue    
  [9] amount of black pixels    
  [10] original filename    
  [11] one face in image    
  [12] absolute pixel difference    
  [13] best faces    
  [14] best faces faster    
  [5] : 選擇需要的排序方法，默認為 5。

手動刪除 workspace/data_dst/aligned 中不必要的人臉，包括不是要換臉的對象。

---

接著即可開始訓練模型，    
點擊 6) train AMP SRC-SRC.bat、6) train AMP.bat、6) train Quick96.bat、6) train SAEHD.bat 皆可，    
建議選擇 **6) train Quick96.bat**，較快速且簡單。

1. 如果沒有預設模型（點擊任一種 bat 檔皆可）：
- [new] No saved models found. Enter a name of a new model : 在沒有預設模型的情況下，命名新模型，隨意命名即可。
- [CPU] : CPU    
  [0] : NVIDIA GeForce RTX XXXX    
  [0] Which GPU indexes to choose? : 選擇使用 CPU 還是使用顯卡，一定要使用顯卡，默認為 0。

2. 如果有預設模型（需點擊預設模型使用的對應 bat 檔）：
- Choose one of saved models, or enter a name to create a new model.    
  [r] : rename    
  [d] : delete    
  [0] : XXXX    
  \[1] : XXXX    
   : 若要選擇要再訓練的預設模型，輸入該預設模型名稱的對應數字；若要訓練一個新模型，輸入 r 命名新模型，隨意命名即可。
- [CPU] : CPU    
  [0] : NVIDIA GeForce RTX XXXX    
  [0] Which GPU indexes to choose? : 選擇使用 CPU 還是使用顯卡，一定要使用顯卡，默認為 0。
- Press enter in 2 seconds to override model settings.
- [6] Autobackup every N hour ( 0..24 ?:help ) : 直接按 enter 即可。
- [n] write preview history ( y/n ?:help ) : 直接按 enter 即可。
- [0] Target iteration : 直接按 enter 即可。
- [n] Flip SRC faces randomly ( y/n ?:help ) : 直接按 enter 即可。
- [n] Flip DST faces randomly ( y/n ?:help ) : 直接按 enter 即可。
- [12] Batch size ( ?:help ) : Batch size 的大小，根據電腦效能設定，可以選擇輸入小一點，默認為 12。
- 後續皆直接按 enter 即可。

開始運行後，會跳出可提供預覽的窗口，    
<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/404402099-90d14538-26ac-483a-8135-88471766fd2a.png" width="500px">

以英文輸入法對預覽窗口按下 p 鍵，可以更新預覽窗口，      
觀察最右行可以得知目前模型的訓練結果，上面也會顯示目前的 Iter(迭代次數)。    
<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/404402857-26ce75cb-3ec0-4bd9-8531-3e746f6aa979.png" width="500px">

訓練時間根據電腦效能有所不同，建議等待到讓 Iter(迭代次數) 達到百萬級別會有好一點的效果。      
當觀察最右行對目前模型的訓練結果滿意時，按 enter 鍵停止訓練。

---

再來進行畫面的調節，      
點擊 7) merge AMP.bat、7) merge Quick96.bat、7) merge SAEHD.bat 中，模型使用的對應 bat 檔。

- Choose one of saved models, or enter a name to create a new model.      
  [r] : rename      
  [d] : delete      
  [0] : XXXX - latest      
   : 選擇要調節畫面的模型，輸入該模型名稱的對應數字。
- [CPU] : CPU    
  [0] : NVIDIA GeForce RTX XXXX    
  [0] Which GPU indexes to choose? : 選擇使用 CPU 還是使用顯卡，一定要使用顯卡，默認為 0。
- [y] Use interactive merger? ( y/n ) : 選擇是否打開調節面板，一定要打開，默認為 y。
- 後續皆直接按 enter 即可。

運行過後，會看到調節面板出現，調節面板用來渲染換臉的效果，      
<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202025-01-18%20135017.png" width="500px">

按 tab 鍵可以切換調節面板和當前正在調節的換臉圖片，      
以英文輸入法，      
按 ` 鍵可以將換臉圖片切換回原始的臉進行觀察，按 1~6 鍵可以使用不同的換臉模式，建議按 1 鍵。      
按 w 鍵和 s 鍵調節侵蝕模式，讓換臉的遮罩自然一點。      
按 e 鍵和 d 鍵調節邊緣羽化模式，讓換臉的遮罩自然一點。   
調節面板上的其他按鍵對應不同的調節模式，可以自行嘗試調節。      

當調節好一張圖片時，按 > 鍵可以切換到下一張換臉圖片。      
當換臉圖片數量太多時，按 shift + > 鍵，可以以當前調節的設定自動調節後續換臉圖片。      

在自動調節的過程中，可以查看 workspace/data_dst/merged，觀察自動調節完成的換臉圖片。

當進度條達到百分之百，即自動調節完成，直接關閉視窗即可。      
<img src= "https://github.com/peter890331/DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese/blob/screenshots/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202025-01-18%20140648.png" width="1000px">

---

最後一步，將換臉完成的圖片合成影片，      
點擊 **8) merged to mp4.bat**。

- 後續皆直接按 enter 即可。

當 Done 出現時，即合成完成，可以查看 workspace/result.mp4，即最終換臉結果。

---

若點擊 **1) clear workspace.bat**，可清空 workspace。

---




[2]: https://github.com/iperov/DeepFaceLab
[3]: https://mega.nz/folder/Po0nGQrA#dbbttiNWojCt8jzD4xYaPw
