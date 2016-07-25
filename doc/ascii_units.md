# 単位のASCII文字変換
更新日: 2016/07/22
## 変換の趣旨
JAHIS 臨床検査データ交換規約 Ver.3.1では、OBX-6（単位）を以下のように記載することとしている。

    < 単位(ASCII)(ST) > ^ < 単位名称(漢字可)(ST) > ^ < コード体系名(ID) >

本事業では、先頭成分をHL7 標準 ver.2.5の表7-9 共通ISO単位 & ISO+拡張に倣い、ASCII文字で記載することを求めている。
事業参加病院で利用されている画面表示用単位とそのASCII表記を以下に示す。表示用単位のうち『,』を含むものは『""』で囲っている。
なお、『μ』のようにASCII表記が特定出来ないものは別表に特記情報を示している。

|ASCII単位|表示用単位の例|ISO|備考|
|----|----|----|----|
|%|%, ％, %(15min., %/6h, %CUA/CCr, ％阻止率, K, 活性%, 陽性％, 抑制率%|+||
|(arb\_u)/mL|AU/ml, AU／mL, AU/mL|+||
|(beth\_u)/mL|B.E/ml, B.U/ml, BU/ml, BU／mL, BU/mL, ﾍﾞｾｽﾀﾞU/, ﾍﾞｾｽﾀﾞU/ml, ベセスダU/mL, ﾍﾞｾｽﾀﾞU/ML, ﾍﾞｾｽﾀﾞU/mL, ﾍﾟｾｽﾀﾞU/ml|||
|(bsa)|cm2|+||
|(cf\_u)/mL|CFU/ml|+||
|(end\_u)/mL|EU, EU/ml, EU/mL|||
|(hb)|bpm|+||
|(jdf\_u)|JDF UNIT, JDF UNITS, JDFU, JDFunits|||
|(knk\_u)|K.U, K.U., KU, K-U, U(Kunkel)|+|【特記事項あり】|
|(mpa.sec)|mPa.s|||
|(ppb)|ppb|+||
|(rpr\_u)|R.U, R.U., RU|||
|(tit\_u)|T.U, T.U., TITER, titer, TU|||
|(u)|unit, UNIT, Unit, Units, UNITS||JLAC10が3F170000002327101(LCAT)の場合のみ『(u)』とする。|
|.|ﾊﾞｲ, 倍|+||
|.(10\*2)|×100倍, ２乗倍|+||
|.10\*2/uL|×10^2, ×10^2/, ×10^2/ul, ×10^2/uL, ×10^2/μl, ×10^2/μL, ×百/μl, 10\*2/mm\*3, 10^2/ul, 10^2/μl, 10＾2/μl, 100/μＬ, x10 2/ul, x10^2, x10^2/ul, x10＾2/μl, x10^2/μL, X10^2/μl, X10^2/μL|+|【特記事項あり】|
|.10\*2copies/mL|×100 ｺﾋ|||
|.10\*3/uL|\*10^3/μl, ×10^3, ×10^3/, ×10＾3/μl, ×10^3/μl, 10^3/μL, 10＾3/μl, 10^3/μｌ, 10^3/μl, X10\*3/μl, x10^3, X10^3/μ, x10＾3/μｌ, x10^3/μl, 干/μl|+|【特記事項あり】|
|.10\*4/mL|×10^4個/ml, 万/ml|+||
|.10\*4/uL|\*10^4/μl, ×10\*4/μL, ×10^4, ×10^4/, ×10^4/ul, ×10^4/uL, ×10＾4/μl, ×10^4/μl, ×10^4/μL, ×万/μl, 10\*4/mm\*3, 10^4/μl, 10^4/μｌ, 10＾4/μl, 10^4/μL, 10^4μｌ, 10000/μＬ, 10x4/μl, x10 4/ul, X10\*4/μＬ, x10^4, x10^4/ul, X10^4/μ, x10＾4/μl, x10^4/μL, x10＾4/μｌ, X10^4/μl, X10000/MCL, 万/μl|+|【特記事項あり】|
|.10\*5/mL|×10＾5/ｍL, ×100万/, 10^5/ml, X100000/|+||
|.10\*6/bag|10^6/bag|||
|.10\*6/kg|10^6/kg|+||
|.10\*6/mL|\*10^6/ml, ×10^6, ×10^6/m, ×10＾6/ｍ, ×10＾6/ｍｌ, ×10^6/ml, ×10^6個/ml, 10^6, 10^6/mL, 10＾6/ｍｌ, 10^6/ml, X10\*6/ml, x10^6/mL, X10^6/ml|+|【特記事項あり】|
|.10\*6/uL|\*10^6/μl, ×10＾6/μl, ×10^6/μl, 10^6/μl, 10＾6/μl, 10^6/μL, X10^6/μ, x10＾6/μｌ, x10^6/μl, 百万/μl|+||
|.10\*8/kg|10^8/kg|+||
|.10\*9/bag|10^9/bag|||
|.10\*9/mL|10^9/mｌ|+||
|.10copies/mL|×10 ｺﾋﾟ|||
|/(15.10\*4(wbc))|個/1.5X10の5乗WBC, 個/15万W||JLAC10が5F194142201917451(pp65抗原(C7ＨＲＰ)[サイトメガロウイルス])の場合のみ『/(15.10\*4(wbc))』とする。|
|/(hpf)|/1HPF, /HPF, /ＨＰＦ, /HPF(×400), HPF, 個/HPF, /1-5個/H, /ＨPF, /1-5HPF, /6-9HPF|+||
|/(lpf)|/1LPF, /LPF, /LPF(×100), LPF, /100LPF, /100, 個/LPF, 個/10LPF|||
|/(wf)|/ＷF, WF, 個/WF|||
|/3uL|/3, /3　μｌ, /3/mm^3, /3/μl, /3/μL, /3μl, /3μL, 個/3|||
|/mL|/1mL, /ml|+||
|/uL|/MCL, /mm^3, /mm3, /ul, /μl, /μｌ, /μL, 1/mm3, Leu/μl, mm^3, μＬ, μl, 個/mm3, 個/uL, 個/μl, 個／μL|+||
|age|才|||
|bag|bag|||
|cel|℃, 度|+||
|ch50/mL|CH50/mL, CH50／mL, CH50/ml, CH50U/ml|||
|class|ｸﾗｽ, クラス, ｸﾗｽ0|||
|cm|cm, ｃｍ|+||
|cm/s|cm/s|||
|COI|(-)．C.O, C.O.I, C.O.Ｉ, C.O.I., CO.Index, COI, ＣＯＩ, COl, Cut off, Cut off Index, CutOffInde|||
|copies/10\*4cells|ｺﾋﾟｰ/1万|||
|copies/10\*6cells|10^6cell, ｺﾋﾟｰ/10^6cells, コピー/10^6cells, ｺﾋﾟｰ/106ce, ｺﾋﾟｰ/106cells||【特記事項あり】|
|copies/assay|ｺﾋﾟ-/ｱﾂｾ, ｺﾋﾟ-/ｱﾂｾｲ, ｺﾋﾟｰ/assay, ｺﾋﾟｰ/ｱｯｾ, ｺﾋﾟｰ/ｱｯｾｲ|||
|copies/mL|copy/ML, copy/mL, CP/ml, CP／mL, cp/mL, ｺﾋﾟ-/mL, ｺﾋﾟ-/ml, コピー/ml, ｺﾋﾟｰ/ml, コピｰ/ml, ｺﾋﾟｰ/mL, コピー/mL|||
|copies/ug|ｺﾋﾟ-/ﾃｽﾄ, ｺﾋﾟｰ/ﾃｽﾄ, コピー, コピー/μg RNA||【特記事項あり】|
|cp|CP|||
|cpm|CPM, ＣＰＭ|||
|delta(ph)|ΔpH|||
|eiu|EIU|||
|EV|EV|||
|fL|fl, ｆｌ, fＬ, FL|+||
|fmol/(mg(prot).hr)|fmol/mg･pr, fmol/mgP, fmol/mg-p|||
|fmol/L|f mol/l, fmol/l, FMOL/L, FMOL/l, fﾓﾙ/l, fﾓﾙ/L|+||
|fmol/mL|fmol/mL|+||
|Fu/mL|FU/mL, ＦU/mL, FU／mL, FU/ml|||
|g|g|+||
|g/(24.hr)|g/24h|+||
|g/(5.hr)|g/5時間|+||
|g/d|g/day, ｇ/day, G/DAY, g／日|+||
|g/dL|g/dl, g/ｄｌ, g／dL, g/ｄL, g/dＬ|+||
|g/g(creat)|G/G CREA, g/g.Cr, g/g・Cr, g/g･Cr, ｇ/ｇ・CRE, g/g・CRE, g/gCre|+||
|g/kg|g/kg|+||
|g/L|g/l|+||
|group|ｸﾞﾙｰﾌﾟ, グループ, ｸﾞﾙ-ﾌﾟ||【特記事項あり】|
|hr|hours, 時間|+||
|hr min|時　分, 時、分|||
|index|G.I, GI, INDEX, Index, INDEX値, index値, INDX, M.I, MI, ndex|||
|inh%|%INH, IH%, INH%, ＩＮＨ％|||
|iu/d|IU/day|+||
|iu/dL|IU/dl, IU/dL|+||
|iu/g(hgb)|IU/g･Hb, IU/gHb|+||
|iu/hr|IU/h|+||
|iu/L|IU/l, IU/ｌ, IU／L, IU/L, IU/l/37, IU/L/37, IU/L/37 ℃, IU/L/37℃, IU/l/37℃, IU/L･37℃, IU/l37℃, IU/L37ﾟC, lU/Ｌ|+||
|iu/mL|IU/ml, IU/ｍL, ＩＵ/ｍＬ, IU／mL, IU/mL, IU/mＬ|+||
|kg|kg, ｋｇ, Kg|+||
|kiu/mL|KIU/ml, KIU/mL|+||
|L|L|+||
|L/d|L/day, ｌ/day, l/day|+||
|L/min|L/min|+||
|LC|×100LMC, 100LC, LC, LC(ﾙﾐｶｳﾝﾄ), ﾙﾐｶｳﾝﾄ|||
|LC(class)|100LC(ｸﾗｽ)|||
|logcopies/mL|CL/ml, LC/ml, LC/mL, Log ｺﾋﾟｰ/ml, Log/ml, LogCopy/ml, LogCopy/mL, Logcopy/ml, LogCP/mL, LOGｺﾋﾟ-/, logｺﾋﾟ-/, logｺﾋﾟ/m, LOGｺﾋﾟ-/mL, Logｺﾋﾟ-/mL, Logｺﾋﾟｰ/, Logコピー/m, LOGｺﾋﾟｰ/ml, Logｺﾋﾟｰ/mL, Logｺﾋﾟｰ/ml|||
|logeq/mL|LEG/mL, LGE/mL, LGE/ml|||
|logiu/mL|L.IU/ml, L.IU/mL, LIU/mL, LIU/ml, Log IU/m, Log IU/mL, Log IU/ｍL, LOG IU/mL, LOGIU/mL, LogIU/mL, LogIU/ml, LoglU/mL|||
|logu/mL|Log U/mL, LogU/ml, LOGU/ML, LogU/mL||【特記事項あり】|
|m|m|+||
|m(arb\_u)/mL|MAU/ML, mAU/ml, mAU/mL, mAu/ml|+||
|maeq/mL|Meq／mL, Meq/ml|+|【特記事項あり】|
|meq/d|mEq/day|+||
|meq/L|mEg/l, mEp/l, mEq/l, mEq／L, mEq/ｌ, mEq/L, mEq/Ｌ|+||
|mg/(24.hr)|mg/24H|+||
|mg/(kg.hr)|mg/kg/h, mg/kg/時|+||
|mg/d|mg/day, mg/DAY, mg／日, mg日|+||
|mg/dL|Eu/dl, Eu/dL, E単位/dl, md/dl, mg/dL, ｍｇ/ｄｌ, ｍｇ／ｄｌ, mg／dL, mg/dl, mg/dＬ, MG/DL, ㎎/dl, mg／dl|+||
|mg/g(creat)|mg/g ・CRE, mg/g Cr, mg/g.cr, mg/g.Cr, mg/g.Cre, mg/g.cre, mg/g.CRE, mg/g･Cr, mg/g・Cr, mg/g･cr, mg/g･CRE, mg/g・CRE, mg/g･cre, MG/G･CREA, mg/gCr, mg/g-Cr, mg/g-Cr., mg/gCRE|+||
|mg/kg|mg/kg|+||
|mg/L|mg/l, ｍg/l, ㎎／Ｌ, ｍｇ/L, mg／L, ｍg/L, MG/L, mg/L|+||
|mg/mL|mg/ml, MG/ML|+||
|mgA/L|mgA/L|||
|min|min, min., 分|+||
|min sec|分 秒, 分　秒, "分,秒", 分、秒, 分．秒, 分・秒, 分･秒, 分秒|||
|miu/L|mlu/l|+||
|miu/mL|m IU/ml, mIU/ml, ｍＩＵ/ml, ｍIU/ml, mIU／mL, mIU/mL, MIU/ml, mlU/ml, mlU/mL|+||
|mL|ml, ｍｌ, ｍＬ, mL|+||
|mL/d|mL/day|+||
|mL/dL|ml/dl|+||
|mL/min|ml/min, ｍL/min, mL/min, mL/分, ml/分|+|JLAC10が8A025000009891929、8A025000009827101(24時間クレアチニンクリアランス)の場合のみ『mL/min』とする。【特記事項あり】|
|mL/min(bsa)|mL/min/1, ml/min/1.7, ml/min/1.73m^2, mL/min/1.73m^2, mL/min/1.73m2, ml/分/1.73㎡, "ｍｌ/分・1,73㎡"|+|【特記事項あり】|
|mm|mm, ＭＭ, mm/1H, mm/h, mm/hr, mm/hr., mm/2h|+||
|mm(hg)|mmHg, Torr|+||
|mm\_h2o|mmH2O|+||
|mmol/L|m mol/L, mm/l, mmol/l, mmol／L|+||
|mmol/mol|mmol/mol, mmoｌ/moL|+|【特記事項あり】|
|mmol/mol(creat)|mmol/mol･CRE, Mﾓﾙ/ﾓﾙ.CRE, ｍﾓﾙ/ﾓﾙC|+||
|molecules/cell|molecules/, molecules/cell|||
|mosm/kg\_h2o|mOsm/kg, mosm/ｋg, mOsm/Kg, mOsm/Kg･, mOsm/Kg･H2O, mOsm/Kg・H2O, mOsm/kg･H2O, mOSM/KgH, mOsm/kgH20, mOsm/kgH2O, MOSM/KGH2O, mOsm/KgH2O|+|【特記事項あり】|
|mosm/L|mOms/L|+|【特記事項あり】|
|mu/dL|mU/dl, mU／dL, MU/DL, mU/dL|+||
|mu/mL|mU/ml, mU/mL|+||
|neq/L|nEq/l|+||
|ng/(24.hr)|ng/24h|+||
|ng/(mL.hr)|ng/ml/h, ng/mL/h, NG/ML/HR, ng/ml/hr, ng/mL/HR, ng/mL/hr|+||
|ng/10\*7cells|ng/10\*7c, ng/10\*7PLT, ng/10^7C, ng/10^7cells, ng/10^7P, ng/10^7PLT, ng/10MコPLT, ng/10M個, ng/10x7C, ng/千万|||
|ng/d|ng/day|+||
|ng/dL|ng/dl, ng／dL, ng/dＬ|+||
|ng/g|ng/g湿重|+||
|ng/g(creat)|ng/g.Cre, ng/g･Cr, ng/g・Cr, ng/g･CRE, NG/G･CREA, ng/gCRE|+||
|ng/L|ng/L, ng／L, ng/l|+||
|ng/mg(creat)|ng/mg.Cr, NG/MG.CRE, ng/mg･c, ng/mg・cr, ng/mg･Cr, ng/mg･CRE, ng/mg-Cr|+||
|ng/mL|ng./ml, ng/m, ng/ml, ｎg/ml, ng/mｌ, ng/ｍｌ, ｎｇ/ml, ｎｇ/ｍｌ, ng／mL, ng／ｍL, ng/mL, NG/ML, ng/mＬ, ｎｇ/ｍＬ, ng／ml, ng/ml以下|+||
|nmol/(L.hr)|nmol/l/h|||
|nmol/(mg(prot).hr)|nmol/mg　protein/時, nmol/mg protein/時間, nmol/mgp, NMOL/MGP/H, nmol/mgp/h, nmol/mgprotein/h|||
|nmol/(mL.hr)|nmol/mL/hr/37℃, nmol/mLh|||
|nmol/dL|nmol/dl|||
|nmol/L|nM/l, nM/L, nmol/l, ｎｍｏｌ／Ｌ, nmol／L, nmol/L, NMOL/L, nmoL/L, nﾓﾙ/l, ｎﾓﾙ/l, nﾓﾙ/L, Nﾓﾙ/L|+||
|nmol/mL|nmol/mL, nmol/ml, nmoL/mL, ｎﾓﾙ/ml|+||
|nmol/mmol(creat)|nM/mM Cr, nM/mM.Cr, nM/mM.CR, nM/mM･CR, nM/mM･Cr, nM/mMCr, nM/mMCRE, NM/MMCRE, nmol/mmo, nmol/mmol・CRE, nmol/mmol･CRE, nmol/mmolC, nmol/mnol･CRE, ｎﾓﾙ/ｍﾓ, ｎﾓﾙ/mﾓﾙ, Nﾓﾙ/MﾓﾙC, Nﾓﾙ/MﾓﾙCRE|+||
|nmol/nmol(creat)|nmol/nmol/・CRE|+||
|nmolBCeq/L|nM BCE, nM BCE/L, nMBCE/l, nMBCE/L, nmbde/l, nmol BCE/L, nmolBC/L, nMOLBCE/, nmolBCE/, NMOLBCE/L, nmolBCE/L, NﾓﾙBCE/L|||
|nmolBCeq/mmol(creat)|nM BCE/m, nM BCE/mM･Cre, nMBCE, NMBCE, nMBCE/mM, nMBCE/mM・Cre, nMBCE/mM･Cre, nMBCE/mMCr, NMBCE/MMCR, nmol BCE, nmol BCE/mmol･Cr, nmolBCE/mmol･CRE, nmolBCE/mmol・CRE|||
|nmolBCeq/nmol(creat)|nmbce/l|||
|nu/mL|nU/mL, ｎＵ/mL, nU/ml|+||
|pcs|ｺ, コ, 個|||
|pcs/10\*2(wbc)|/100, /100WBC, /100個, 100WBC, ｺ/100WBC, 個/WBC100|||
|permil|△13cパー, △13cﾊﾟｰﾐﾙ, ‰, ‰(ﾊﾟｰﾐﾙ, ‰(ﾊﾟｰﾐﾙ), 0/00, PER MIL, ﾊﾟｰﾐﾙ, パーミル, ﾊﾟｰﾐﾙ△1, ﾊﾟｰﾐﾙΔ1, ﾊﾟ-ﾐﾙ|||
|pg|pg|+||
|pg/dL|pg/dL|+||
|pg/mg(creat)|pg/mg cre, pg/mg.CR, pg/mg.Cre, PG/MG.CRE, pg/mg･Cr, pg/mg･CRE, pg/mg・Crn, pg/mgCr, pg/mg-Cr, pg/mgCr., pg/mgCRE, PG-MG.CR|+||
|pg/mL|pg/ml, pg/ｍｌ, ｐｇ／ｍｌ, ｐｇ/ml, pg／mL, PG/ML, pg/mL, pg/mＬ, PG/ml, Pg/mL, pg/mL(参考, pg/mL(参考値), pg/ml以下, ＰＧ／ＭＬ|+||
|ph|ｐｈ|+||
|pmol/dL|pmol/dL|+||
|pmol/L|pM, pmol/L, pmol/l, pMOL/l, Pﾓﾙ/L|+||
|pmol/mg(creat)|pmol/mg･Cr|+||
|pmol/mL|pmol/mL, pmol/ml, PMOL/ML, pﾓﾙ/ml, ｐﾓﾙ/ml|+||
|ratio|RATIO, Ratio|||
|RLU|RLU|||
|S/CO|S/CO, S/co, s/co, S/COﾐﾏﾝ, S/CO値, Sample/c, Sample/cut off(S/Co), S-CO|||
|S/N|S/N比|||
|scale|号|||
|score|SCORE, ｽｺｱ, 点|||
|sec|SEC, Sec, SEC., sec., SECOND, 秒, 秒|+||
|si%|S.I(%), S.I., SI|+||
|spot|ｽﾎﾟｯﾄ|||
|type|DQﾛｰｶｽ, ｶﾀ, ガタ, ﾀｲﾌﾟ, 型||【特記事項あり】|
|u/d|U/day, Ｕ/日|+||
|u/g(creat)|U/g.Cr, U/g・Cr, U／g・Cr, U/g･Cr, U/g・Cre, U/g･CRE|+||
|u/L|U/l, Ｕ／Ｌ, U/ｌ, U／L, U/L, U/l/37℃|+||
|u/mg(creat)|U/mg･Cr|+||
|u/mL|U/ml, Ｕ/ＭＬ, Ｕ／ｍｌ, U／mL, Ｕ／mL, U/ML, U/mL, Ｕ/ｍＬ, U/mＬ, μ/ml|+|【特記事項あり】|
|uA/mL|UA/ML, UA/ml, UA/mL, Ua/ml, Ua/mL|||
|ueq/L|uEq/L, μEq/L, μEq/l|+||
|ug|μg|+||
|ug/(24.hr)|μg/24h|+||
|ug/(dL.hr)|μg/dl/h|||
|ug/d|MCG/DAY, ug/day, μg/day, μｇ/day, μg/DAY, μg/日, μg／日|+||
|ug/dL|mcg/dl, MCG/DL, ug/dl, μg/dI, μg/dl, μｇ/ｄｌ, μｇ/dl, μg／dL, μg/ｄｌ, μg/dL, μg/dＬ|+||
|ug/dL(rbc)|MCG/DL RBC, μg/100m, μg/dL R, μg/dl R, μg/dL RBC, μg/dl･R, μg/dlRBC, μg/dLRBC, μg/dl赤|+||
|ug/g|μg/g|+||
|ug/g(creat)|MCG/G CRE, MCG/GCRE, ug/gCr, μg/g.CR, μg/g.Cre, μg/g・Cr, μｇ/ｇ・Cr, μg/g･CR, μg/g･CRE, μg/g・CRE, μg/g・Crn, μg/gC, μg/gCr, μｇ/ｇCr, μg/g-Cr, μg/gcre, μg/gCRE|+||
|ug/L|MCG/L, ug/l, ug/L, μg/l, μg/Ｌ, μｇ/L, μg／L, μg/L|+|【特記事項あり】|
|ug/mg(creat)|MCG/MG.CRE, μg/mg.C, μg/mg.Cr, μg/mg.CRE, μg/mg･C, μg/mg･Cr, μg/mg・Cr, μg/mg･CRE, μg/mgCr|+||
|ug/min|MCG/MIN, μg/分|+||
|ug/mL|MCG/ML, micg/ml, mlcg/ml, ug/mL, ug/ml, μg/ml, μg/ｍL, μｇ/ml, μｇ/ｍｌ, μg／mL, μg/mL, μg/mＬ|+||
|ug/mmol|μg/mmol|+||
|ug/mmol(creat)|MCG/MMOLCR, μg/mmol・CRE, μg/mﾓﾙC|+||
|uiu/mL|MCIU/ML, uIU/mL, ulU/mL, μIU/mL, μIU／mL, μIU/ml, μIU/mＬ, μlU/mL|+||
|umol/(24.hr)|μmol/24|+||
|umol/d|MCMOL/DAY, umol/day, μmol/da, μmol/day, μmol/日, μﾓﾙ/day|+||
|umol/g(creat)|umol/gCr, μmol/g・c, μmol/g･Cr, μmol/gc, μmol/gCRE|+||
|umol/L|MCMOL/L, umol/L, μＭ/l, μmol/L, μmol/Ｌ, μmol／Ｌ, μmol/l, μﾓﾙ/l|+||
|umol/mg(creat)|MCMOL/MGCR, μmol/mg, μmol/mg.C, μmol/mgCR, μmol/mgCr.|+||
|umol/mL|μＭ|+|【特記事項あり】|
|umol/mol(creat)|MCﾓﾙ/ﾓﾙ.CR, μmol/mo, μmol/mol･CRE|+||
|uu/10\*9(rbc)|μU/10億|+||
|uu/mL|μU/ml, μＵ/ｍｌ, μU／mL, μU/mL|+||
|vol%|Vol%|||
|単位なし|53, 54, 55, 56, 57, 58, 59, （比率）, ×31.2/, ■／■, aa, D, dils, EIAUnits, HPT, ＭＭＡＬ, NULL, SD, μs, ｺﾋﾟｰ\*, ｺﾋﾟｰ\*\*, ﾍﾝｲｽｳ, 以下, 咽頭, 個/mm2, 細胞数, 細胞数, 指数, 色, 定性, 定性, 比, 変異数, 未満, 無, 喀痰|||

### 特記事項

表記を省略し過ぎている、表記が誤っている、複数の意味がある等の理由で注意が必要な単位を以下に示す。個別に単位の意味を確認し、ASCII表記にすること。

|ASCII単位|表示用単位の例|備考|
|----|----|----|
|(knk\_u)|U, Ｕ|JLAC10が3A025000002329201(TTT)、 3A030000002329201(ZTT)の場合のみ『(knk\_u)』とする。|
|.10*2/uL|×10^2, ×10^2/, x10^2|病院によっては他の単位を意味する場合もあるので個別に確認すること。|
|.10*3/uL|×10^3, ×10^3/, x10^3|病院によっては他の単位を意味する場合もあるので個別に確認すること。|
|.10*4/uL|×10^4, ×10^4/, x10^4|病院によっては他の単位を意味する場合もあるので個別に確認すること。|
|.10*6/mL|×10^6, 10^6|病院によっては他の単位を意味する場合もあるので個別に確認すること。|
|copies/10\*6cells|copy, Kｺﾋﾟｰ/ml, ｺﾋﾟ-, ｺﾋﾟｰ|JLAC10が5F201144002386201、5F201144102386201(EBｳｲﾙｽDNA定量)の場合のみ『copies/10\*6cells』とする。病院によって『copies/ug』を意味する場合もあるので個別に確認すること。|
|copies/ug|ｺﾋﾟ-/ﾃｽﾄ, ｺﾋﾟｰ/ﾃｽﾄ, コピー|『ｺﾋﾟ-/ﾃｽﾄ』, 『ｺﾋﾟｰ/ﾃｽﾄ』はJLAC10が8C125996204687501(major bcr-abl定量:リアルタイムRT-PCR法)の場合のみ、『コピー』はJLAC10が5F194144009986201、5F194144109986201(CMV定量)、5F201144009986201、5F201144109986201(EBV定量)、5F190144009986201、5F190144109986201(HSV定量)、5F193144009986201、5F193144109986201(VZV定量)、5F212144009986201、5F212144109986201(HHV定量)、5F150144009986201、5F150144109986201(ADV定量)の場合のみ『copies/ug』とする。病院によって『copies/10\*6cells』を意味する場合もあるので個別に確認すること。|
|group|型|JLAC10が5F3601406023???14(HCV血清型)の場合のみ『group』とする。|
|logu/mL|Log|JLAC10が5F0181410023???01(B型肝炎ウイルスコア関連抗原定量)の場合のみ『logu/mL』とする。|
|maeq/mL|mEq/ml|JLAC10が5F0151440023???01、5F0151441023???01(HBV核酸定量：プローブ法)の場合のみ『maeq/mL』とする。|
|mL/min(bsa)|ML/MIN, ml/min/|JLAC10が8A066000002391901(推算GFRcys)の場合のみ『mL/min(bsa)』とする。|
|mmol/mol|mmol/mL|JLAC10が3D045000002220401、3D0450000022???01(HbA1c IFCC値) の場合のみ『mmol/mol』とする。|
|mosm/kg\_h2o|mOsm／L, mOsm/l, mOsm/L, mOSM/l, mOsm, mosm/l, mOsm/ｌ|JLAC10が3H045000002390201、3H045000000190201(浸透圧) の場合のみ『mosm/kg\_h2o』とする。|
|u/mL|M|JLAC10が5G5310000022???01(HIT-IgG抗体)の場合のみ『u/mL』とする。|
|ug/L|μ|JLAC10が5C120000002305301(Ⅰ型プロコラーゲン-N末端プロペプチド)の場合のみ『ug/L』とする。|
|umol/mL|μＭ|JLAC10が3M7250000023???01(メトトレキサート)の場合のみ『umol/mL』とする。|
