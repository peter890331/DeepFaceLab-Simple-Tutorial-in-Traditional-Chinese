# DeepFaceLab-Simple-Tutorial-in-Traditional-Chinese
關於 DeepFaceLab 的繁體中文簡易教學。

## 💢請勿使用在非法或可能傷害他人權益的用途。💢

參考自 YouTube 影片：    
[deepfacelab模型训练，换脸教程，绝对是全网最详细的！#deepface #Ai换脸#chatgpt #midjourney #deepfacelab #deepfacelive #直播换脸][1]

在此只介紹最簡易的功能，詳細可以直接觀看影片，例如修正人臉辨識錯誤的功能。

[1]: https://youtu.be/6-KPIXEajk8

![image](https://github.com/user-attachments/assets/f6d7f3bc-697a-4af4-bc5e-82f8398e0a48)

## [DeepFaceLab][2]
Releases：[Windows (Mega.nz)][3].    
DeepFaceLab_NVIDIA_RTX3000_series_build_11_20_2021.exe 適合 RTX3060 以上的顯卡；    
DeepFaceLab_NVIDIA_up_to_RTX2080Ti_build_11_20_2021.exe 適合 RTX3060 以下的顯卡。 

其 [GitHub][2] 中還有其他下載連結。

在此以 DeepFaceLab_NVIDIA_RTX3000_series_build_11_20_2021.exe 為例，下載後解壓縮成資料夾，    
![image](https://github.com/user-attachments/assets/0a2d30a8-88f7-4c44-bfb2-a98f308e683d)

---

在解壓縮後的資料夾中，**workspace** 是工作區域，儲存要摳臉的影片和要換臉的影片，以及其他結果。    

將要摳臉的影片存入 workspace 並命名為 **data_src.mp4**；    
將要換臉的影片存入 workspace 並命名為 **data_dst.mp4**。      
![image](https://github.com/user-attachments/assets/e1621411-bfb4-45f3-9914-4127c370d437)


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
- [n] Write debug images to aligned_debug? ( y/n ) : 選擇是否要生成一份 debug 文件，默認為 n。

完成後可以查看 workspace/data_src/aligned，會看到摳臉圖片中的人臉再切出來的圖片。

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

- [new] No saved models found. Enter a name of a new model : 在沒有預設模型的情況下，命名新模型，隨意命名即可。
- [CPU] : CPU    
   [0] : NVIDIA GeForce RTX XXXX    
 [0] Which GPU indexes to choose? : 選擇使用 CPU 還是使用顯卡，一定要使用顯卡，默認為 0。

開始運行後，會跳出可提供預覽的窗口，    
![image](https://github.com/user-attachments/assets/90d14538-26ac-483a-8135-88471766fd2a)

以英文輸入法對預覽窗口按下 p 鍵，可以更新預覽窗口，      
觀察最右行可以得知目前模型的訓練結果，上面也會顯示目前的 Iter(迭代次數)。    
![image](https://github.com/user-attachments/assets/26ce75cb-3ec0-4bd9-8531-3e746f6aa979)






[2]: https://github.com/iperov/DeepFaceLab
[3]: https://mega.nz/folder/Po0nGQrA#dbbttiNWojCt8jzD4xYaPw
