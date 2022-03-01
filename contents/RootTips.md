---
layout: default
---

[返回主页](https://luofaming.github.io/)

关于CERN ROOT的一些学习笔记

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
TRandom3 *gr = new TRandom3(0); //声明随机数
Double_t Dr = gr->Uniform(-0.5,0.5); //产生-0.5到0.5的随机数
```

