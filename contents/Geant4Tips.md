---
layout: default
---

[返回主页](https://luofaming.github.io/)



* 定义材料

``` c++
void MyDetectorConstruction::DefineMaterials()
{ 
    // Lead material defined using NIST Manager
    auto nistManager1 = G4NistManager::Instance();
    nistManager1->FindOrBuildMaterial("G4_WATER");
    auto nistManager2 = G4NistManager::Instance();
    nistManager2->FindOrBuildMaterial("G4_AIR");

    //在这里先定义所有可能用到的材料Get nist material manager
    G4NistManager* nist = G4NistManager::Instance();
    //调用G4自身定义好的材料 (Material Database) 
    //官网https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Appendix/materialNames.html#g4matrdb
    nist->FindOrBuildMaterial("G4_Ge");//1-98号元素都有
    nist->FindOrBuildMaterial("G4_lH2");//液氢
    nist->FindOrBuildMaterial("G4_lN2");//液氮
    nist->FindOrBuildMaterial("G4_lO2");//液氧
    nist->FindOrBuildMaterial("G4_lAr");//Liquid argon液氩
    nist->FindOrBuildMaterial("G4_Galactic");//太空环境
    nist->FindOrBuildMaterial("G4_AIR");
    nist->FindOrBuildMaterial("G4_WATER");
    nist->FindOrBuildMaterial("G4_WATER_VAPOR");//水蒸气
    nist->FindOrBuildMaterial("G4_POLYETHYLENE");//聚乙烯 (PE)
    nist->FindOrBuildMaterial("G4_BGO");//锗酸铋闪烁体
    nist->FindOrBuildMaterial("G4_CARBON_DIOXIDE");//二氧化碳
    nist->FindOrBuildMaterial("G4_LEAD_OXIDE");//氧化铅
    nist->FindOrBuildMaterial("G4_MYLAR");//mylar膜 坚韧聚脂类高分子物
    nist->FindOrBuildMaterial("G4_PLEXIGLASS");//有机玻璃
    nist->FindOrBuildMaterial("G4_STAINLESS-STEEL");//不锈钢
    nist->FindOrBuildMaterial("G4_LUCITE");//透明合成树脂(有机玻璃)
    nist->FindOrBuildMaterial("G4_CONCRETE");//混凝土
    nist->FindOrBuildMaterial("G4_GRAPHITE");//石墨
    nist->FindOrBuildMaterial("G4_SILICON_DIOXIDE");//二氧化硅
    nist->FindOrBuildMaterial("G4_RUBBER_NATURAL");//天然橡胶
    nist->FindOrBuildMaterial("G4_PbWO4");//钨酸铅晶体
    nist->FindOrBuildMaterial("G4_URANIUM_OXIDE");//氧化铀
    nist->FindOrBuildMaterial("G4_URANIUM_MONOCARBIDE");//碳化铀
    nist->FindOrBuildMaterial("G4_URANIUM_DICARBIDE");//二碳化铀
    nist->FindOrBuildMaterial("G4_A-150_TISSUE");//组织
    nist->FindOrBuildMaterial("G4_ACETONE");//丙酮
    nist->FindOrBuildMaterial("G4_ACETYLENE");//乙炔(电石气)
    nist->FindOrBuildMaterial("G4_ADENINE");//腺嘌呤
    nist->FindOrBuildMaterial("G4_ADIPOSE_TISSUE_ICRP");//ICRP脂肪组织
    nist->FindOrBuildMaterial("G4_ALANINE");//丙氨酸
    nist->FindOrBuildMaterial("G4_ALUMINUM_OXIDE");//氧化铝
    nist->FindOrBuildMaterial("G4_AMBER");//琥珀
    nist->FindOrBuildMaterial("G4_AMMONIA");//氨气
    nist->FindOrBuildMaterial("G4_ANILINE");//苯胺
    nist->FindOrBuildMaterial("G4_ANTHRACENE");//蒽 并三苯
    nist->FindOrBuildMaterial("G4_B-100_BONE");//骨头
    nist->FindOrBuildMaterial("G4_BAKELITE");//酚醛树脂,人造树胶
    nist->FindOrBuildMaterial("G4_BARIUM_FLUORIDE");//氟化钡
    nist->FindOrBuildMaterial("G4_BARIUM_SULFATE");//硫酸钡
    nist->FindOrBuildMaterial("G4_BENZENE");//苯
    nist->FindOrBuildMaterial("G4_BERYLLIUM_OXIDE");//氧化铍
    nist->FindOrBuildMaterial("G4_BLOOD_ICRP");//ICRP血液
    nist->FindOrBuildMaterial("G4_BONE_COMPACT_ICRU");//ICRU致密骨头
    nist->FindOrBuildMaterial("G4_BONE_CORTICAL_ICRP");//ICRP致密骨头
    nist->FindOrBuildMaterial("G4_BORON_CARBIDE");//碳化硼
    nist->FindOrBuildMaterial("G4_BORON_OXIDE");//氧化硼
    nist->FindOrBuildMaterial("G4_BRAIN_ICRP");//ICRP大脑
    nist->FindOrBuildMaterial("G4_BUTANE");//（异）丁烷
    nist->FindOrBuildMaterial("G4_N-BUTYL_ALCOHOL");//正丁醇
    nist->FindOrBuildMaterial("G4_C-552");//
    nist->FindOrBuildMaterial("G4_CADMIUM_TELLURIDE");//碲化镉
    nist->FindOrBuildMaterial("G4_GRAPHITE_POROUS");//多孔石墨
    nist->FindOrBuildMaterial("G4_LUCITE");//有机玻璃 透明合成树脂
    nist->FindOrBuildMaterial("G4_BRASS");//黄铜
    nist->FindOrBuildMaterial("G4_BRONZE");//青铜
    nist->FindOrBuildMaterial("G4_CR39");//碳本酸丙烯乙酸
    nist->FindOrBuildMaterial("G4_OCTADECANOL");//十八醇 硬脂醇
    //注册G4自身定义好的元素elements，采用天然丰度
    G4Element* H = nist->FindOrBuildElement("H",false);//1
    G4Element* Li = nist->FindOrBuildElement("Li",false);//3
    G4Element* C = nist->FindOrBuildElement("C",false);//6
    G4Element* N = nist->FindOrBuildElement("N",false);//7
    G4Element* O = nist->FindOrBuildElement("O",false);//8
    G4Element* Mg = nist->FindOrBuildElement("Mg",false);//12
    G4Element* Al = nist->FindOrBuildElement("Al",false);//13
    G4Element* Si = nist->FindOrBuildElement("Si",false);//14
    G4Element* P = nist->FindOrBuildElement("P",false);//15
    G4Element* S =  nist->FindOrBuildElement("S",false);//16
    G4Element* Cr = nist->FindOrBuildElement("Cr",false);//24
    G4Element* Mn = nist->FindOrBuildElement("Mn",false);//25
    G4Element* Fe = nist->FindOrBuildElement("Fe",false);//26
    G4Element* Ni = nist->FindOrBuildElement("Ni",false);//28
    G4Element* I = nist->FindOrBuildElement("I",false);//53
    G4Element* Cs = nist->FindOrBuildElement("Cs",false);//55
    G4Element* Ce = nist->FindOrBuildElement("Ce",false);//58
    //同位素构建元素，用来调整材料丰度
    G4Isotope* U4 = new G4Isotope("U234",92,234,234.02*g/mole);
    G4Isotope* U5 = new G4Isotope("U235",92,235,235.01*g/mole);
    G4Isotope* U6 = new G4Isotope("U236",92,236,236.04*g/mole);
    G4Isotope* U8 = new G4Isotope("U238",92,238,238.03*g/mole);
    //向元素添加同位素
    G4Element* HEU58 = new G4Element("Highly-enriched Uranium 58", "HEU58", 2);
    HEU58->AddIsotope(U5, 0.93);
    HEU58->AddIsotope(U8, 0.07);
    G4Element* HEU4568 = new G4Element("Highly-enriched Uranium 4568","HEU4568",4);
    HEU4568->AddIsotope(U4,0.0097);
    HEU4568->AddIsotope(U5,0.9315);
    HEU4568->AddIsotope(U6,0.0024);
    HEU4568->AddIsotope(U8,0.0564);
    
    //---------------------------------------------------------------------------------

    //Scintillator(BC408) 塑闪 
    G4Material* BC408 = new G4Material("BC408", 1.032*g/cm3, 2);
    BC408->AddElement(H, 11);BC408->AddElement(C, 10);
    BC408->AddElement(H, 10);BC408->AddElement(C, 9);
    // LiquidScint(NE213) 液闪 
    G4Material* NE213 = new G4Material("NE213",0.874*g/cm3,2);
    NE213->AddElement(H,1212);
    NE213->AddElement(C,1000);
    // He-3 detector materials
    G4Material* matHe3  = new G4Material("He3",  2., 3.*g/mole, 0.00049*g/cm3, kStateGas);
    // Uranium material定义铀
    G4Material* matHEU58 = new G4Material("HEU58", 19.1*g/cm3, 1, kStateSolid);
    matHEU58->AddElement(HEU58, 1.00);
    G4Material* matHEU4568 = new G4Material("HEU4568",18.75*g/cm3,1);
    matHEU4568->AddElement(HEU4568, 1.0);
    //定义钢材料
    G4Material* matSteel = new G4Material("Steel",7.788*g/cm3,9);
    matSteel->AddElement(Fe,62.1805*perCent);
    matSteel->AddElement(Cr,20.26*perCent);
    matSteel->AddElement(Mn,9.37*perCent);
    matSteel->AddElement(Ni,7.5*perCent);
    matSteel->AddElement(Si,0.34*perCent);
    matSteel->AddElement(N,0.29*perCent);
    matSteel->AddElement(C,0.04*perCent);
    matSteel->AddElement(P,0.018*perCent);
    matSteel->AddElement(S,0.0015*perCent);

    // Print materials
    G4cout << *(G4Material::GetMaterialTable()) << G4endl;
}
```

