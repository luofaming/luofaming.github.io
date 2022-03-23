---
layout: default
---

[返回主页](https://luofaming.github.io/)

关于CERN ROOT的一些学习笔记
* 推荐up主：https://space.bilibili.com/30515356
* 推荐up主：https://space.bilibili.com/237339480/?spm_id_from=333.999.0.0
* 官方指南：https://root.cern/manual/

* 创建文件
``` c++
TFile *opf=new TFile("tree.root","recreate");//新文件tree.root，指针 *opf
```


* 如何保存文件

``` c++
TFile* f = TFile::Open("myfile.root","NEW");
TH1D* h1 = new TH1D("h1","h1",100,-5.,5.);
h1->FillRandom("gaus");  // fill histogram with random data
h1->Write();
delete f;
```

* 从已知tree里截取数据创建root文件

``` c++
TFile *infile  = new TFile("input.root");
TFile *fout = new TFile("output.root","recreate");
((TTree*)infile->Get("tree"))->CopyTree("aoq<3.5&&aoq>3&&zet>49&&zet<51")
fout->Write();
fout->Close();
```

* 数学运算
``` bash
TMath::Sqrt() #开根号
TMath::Exp() #指数
```

* 产生随机数
``` c++
TRandom3 class
Uniform(Double_t x1, Double_t x2);
Gaus(Double_t mean, Double_t sigma)；
/***************************************/
TRandom3 *gr = new TRandom3(0); //声明随机数
Double_t Dr = gr->Uniform(-0.5,0.5); //产生-0.5到0.5的随机数
/***************************************/
TRandom r;
Double_t  x1 = r.Gaus(0,1);//高斯分布mean=0，sigma=1
/**************************************/
TF1 *f1 = new TF1("f1", "x", 0, 10);
//"x"为一次线性，"x*x"为二次，系数无效
Double_t  r = f1->GetRandom(); 
```

* 更改坐标轴形式
``` c++
c1->SetLogy();//y坐标为log形式
c1->SetLogy(0);//y坐标为线性形式
```




