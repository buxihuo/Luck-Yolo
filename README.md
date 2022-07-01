### 简介（Introduction）<br>
无代价涨点 + 检测未知物体<br>

<br>![image](https://user-images.githubusercontent.com/84908793/162931434-dc4da5c4-7916-4cee-af1c-a2f1037d1bf1.png)<br><br>

<details>
  <summary> 不同风格图像与视频对比展示</summary>

|Model                |Yolov5x |OW-yolov5x |
|---                  |---  |---  
|漫画                 |![图片 46](https://user-images.githubusercontent.com/84908793/167087540-c109830f-3a0c-42d6-8948-61c96a3925aa.png) |![图片 47](https://user-images.githubusercontent.com/84908793/167087925-5332b077-9481-44a4-af93-0c1c4e175ff1.png)
|电影                 |![图片 43](https://user-images.githubusercontent.com/84908793/167087873-bcba6a22-9798-4d51-b9f5-b610c8fe1a51.png) |![图片 37](https://user-images.githubusercontent.com/84908793/167087888-e4749d62-4bec-47ab-b235-9dcd45cd5440.png)
|游戏                 |![图片 2](https://user-images.githubusercontent.com/84908793/167087802-40ef99d0-2658-444a-b02f-df258e1538b1.png)  |![图片 1](https://user-images.githubusercontent.com/84908793/167087825-98c33a0c-4345-4f51-bb2e-6fe7bd96b182.png)
|动漫                 |![图片 4](https://user-images.githubusercontent.com/84908793/167087943-bd4179c6-0f24-4721-810d-deb3e17b8eed.png)  |![图片 3](https://user-images.githubusercontent.com/84908793/167087955-18f042b2-5658-40e6-99fb-f43562051ebe.png)
</details>

<details open>
  <summary> 推理示例</summary>

```bash
$ python detect.py --source data/images --conf 0.25 --weights model/OW_yolov5s.pt
'''
当前版本未知物体的分数中不包含背景信息，在非极大值抑制阶段，通过前景分数是否大于阈值conf过滤掉多余的未知物体，缺点是当阈值
过小（例如0.01）时会出现大量预测框，同时降低已知类别性能。
'''
```
</details>

<details>
<summary>正在测试的功能</summary>
 
-  将背景信息融入未知物体的分数中.
-  输出未知物体可能的父类信息，如将猴子预测为未知的动物。
-  分类标签使用IOU分数。
-  设计动态标签平滑（dls),提升检测器性能，同时减少未知类检测对已知类性能的影响。
</details>

### coco数据集
|Model |size<br><sup>(pixels) |batch |mAP<sup>val<br>0.5:0.95 |mAP<sup>val<br>0.5 |
|---                  |---  |---    |---    |---   
|yolov5s              |640  |128    |37.4   |56.8  
|OW-yolov5s      |640  |64     |37.5   |56.8
|yolov5x              |640  |64    |50.7   |68.9   
|OW-yolov5x      |640  |64     |50.9   |69.3     

### voc数据集
|Model |size<br><sup>(pixels) |mAP<sup>val<br>0.5:0.95 |mAP<sup>val<br>0.5 |pre(coco)
|---                        |---  |---    |---       |---   
|yolov5s                    |512  |62.4   |86.7      |5s
|OW-yolov5s            |512  |62.4   |86.8      |OW-5s 
|yolov5x                    |512  |74.6   |91.9/92.1 |5x
|OW-yolov5x            |512  |74.7   |92.2      |OW-5x

  

### 预训练模型
  [OW-yolov5s](https://github.com/buxihuo/unknown-yolo/releases/download/unknown-yolo/Luck-yolov5s.pt)<br>
  [OW-yolov5x](https://github.com/buxihuo/unknown-yolo/releases/download/unknown-yolo/Luck-yolov5x.pt)<br>
