# ShapeNet 

- homepage : https://www.shapenet.org/
- paper : [ShapeNet: An Information-Rich 3D Model Repository](http://shapenet.cs.stanford.edu/shapenet/obj-zip/ShapeNetCore.v2-old/shapenet/tex/TechnicalReport/main.pdf)

by : Princeton, Stanford, TTIC

---

## 데이터셋 

download : `wget https://shapenet.cs.stanford.edu/ericyi/shapenetcore_partanno_segmentation_benchmark_v0.zip`


├── 02691156
│   ├── points : `*.pts`  pcd의 헤더 부분을 제거한 x,y,z값
│   ├── points_label : `*.png` : 생성된 pts의 이미지 변환 파일, 사용안함 (points_label)
│   └── seg_img 
├── 02773838
│   ├── points
│   ├── points_label
│   └── seg_img
├── 02954340
│   ├── points
│   ├── points_label
│   └── seg_img
└── train_test_split
│
└──synsetoffset2category.txt 



###### 02691156/points/cf71f5442c4120db37678474be485ca.pts

uniformly sampled points from ShapeNetCore models

```
0.17597 0.10668 -0.17203
-0.17051 -0.12873 0.17203
0.28055 0.11397 -0.15397
0.23845 0.11397 -0.11219
0.24040 0.11397 -0.07258
0.24254 0.11397 -0.17366
0.24648 0.11397 0.03471
-0.01466 -0.02107 0.06386
0.05794 -0.00043 0.16675
```

###### 02691156/points_label/cf71f5442c4120db37678474be485ca.seg

per-point segmentation labels

```
1
1
1
1
1
2
2
```

###### 02691156/seg_img/cf71f5442c4120db37678474be485ca.png

a visualization of labeling

![](https://i.imgur.com/LJy8Gvs.png)


###### synsetoffset2category.txt

An mapping from synsetoffset to category name

```
Airplane	02691156
Bag	02773838
Cap	02954340
Car	02958343
Chair	03001627
Earphone	03261776
Guitar	03467517
Knife	03624134
Lamp	03636649
Laptop	03642806
Motorbike	03790512
Mug	03797390
Pistol	03948459
Rocket	04099429
Skateboard	04225987
Table	04379243

```

###### train_test_split

lists of training/test/validation shapes shuffled across all categories (from the official train/test split of ShapeNet)

```
shuffled_test_file_list.json  
shuffled_train_file_list.json  
shuffled_val_file_list.json
```

---

## 학습 
```
$ train_gan.py 
# print('[%d: %d/%d] train lossD: %f lossG: %f' %(epoch, i, num_batch, lossD.data[0], lossG.data[0])) #필요시 L136 주석 처리 
```

./gan폴더 생성후 `gan/modelD_*.pth`와 `gan/modelG_*.pth` 생성 


##

---

ShapeNet consists of several subsets:


- ShapeNetCore : full ShapeNet dataset, 55  categories, 51,300 models

  ![image](https://user-images.githubusercontent.com/28984716/49871420-12c6b180-fdcb-11e8-84fa-c7d78896cff1.png)


- ShapeNetSem : smaller, 270 categories, 12,000 models


  ![image](https://user-images.githubusercontent.com/28984716/49871446-2540eb00-fdcb-11e8-8f85-28e856f84cb6.png)

```
@article{yi2016scalable,
  title={A scalable active framework for region annotation in 3d shape collections},
  author={Yi, Li and Kim, Vladimir G and Ceylan, Duygu and Shen, I and Yan, Mengyan and Su, Hao and Lu, ARCewu and Huang, Qixing and Sheffer, Alla and Guibas, Leonidas and others},
  journal={ACM Transactions on Graphics (TOG)},
  volume={35},
  number={6},
  pages={210},
  year={2016},
  publisher={ACM}
}
```
