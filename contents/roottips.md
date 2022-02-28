---
layout: default
---

关于CERN ROOT的一些学习笔记



### 如何保存文件

```C++
TFile* f = TFile::Open("myfile.root","NEW");
TH1D* h1 = new TH1D("h1","h1",100,-5.,5.);
h1->FillRandom("gaus");  // fill histogram with random data
h1->Write();
delete f;
```

### Create new root file with cut from a existing tree

```C++
TFile *infile  = new TFile("input.root");
TFile *fout = new TFile("output.root","recreate");
((TTree*)infile->Get("tree"))->CopyTree("aoq<3.5&&aoq>3&&zet>49&&zet<51")
fout->Write();
fout->Close();
```





