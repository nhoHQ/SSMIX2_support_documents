# 単位のASCII文字変換
更新日: 2015/07/24
## 変換の趣旨
JAHIS 臨床検査データ交換規約 Ver.3.1では、OBX-6（単位）を以下のように記載することとしている。

    < 単位(ASCII)(ST) > ^ < 単位名称(漢字可)(ST) > ^ < コード体系名(ID) >

本事業では、先頭成分をHL7 標準 ver.2.5の表7-9 共通ISO単位 & ISO+拡張に倣い、ASCII文字で記載することを求めている。
変換例を以下に示す。なお『/S/』はHL7の表記で『^』を表現する際に使用する文字列である。

|ASCII単位|表示用単位の例|ISO|
|----|-----|-----|
|%|％, %, 100WBC, %ソガイリツ|+|
|si%|S.I(%), SI|+|
|inh%|Inh%, %INH|+|
|.10*2/uL|X10＾2/μl, x10 2/ul, X10 2, ×10^2/μL, ×10\S\2/, x10\S\2, x10\S\2/μL|+|
|.10*3/uL|10\S\3/μl, ×10\S\3/μl, X10 3, ×10\S\3/|+|
|.10*4/uL|X10＾4/μl, 10＾4/μl, x10 4/ul, 10\S\4/μl, ×10^4/μL, ×10\S\4/, x10\S\4, x10\S\4/μL|+|
|.10*6/uL|10\S\6/μl, ×10\S\6/μl, X10 6|+|
|/(hpf)|/HPF, HPF|+|
|/(lpf)|/LPF, LPF|+|
|/mL|/ml, /1mL|+|
|ch50/mL|CH50/ml, CH50U/ml||
|/uL|/μl, /ul, /μL|+|
|iu/L|IU/ｌ, IU/l/37℃, IU/L, IU/l, IU/L/37, IU/L/37゜, IU/L/37゜|+|
|u/L|U/l, U/ｌ, U/l/37℃, U/L|+|
|iu/mL|IU/ml, IU/mL, ＩＵ/ｍＬ|+|
|u/mL|U/ml, U/ｍｌ, U/mL, Ｕ/ｍＬ|+|
|miu/mL|mIU/ml, mlU/ml, m IU/ml, mIU/mL|+|
|uiu/mL|μIU/ml, μlU/mL|+|
|uu/mL|μU/ml, μU/mL|+|
|mu/dL|MU/DL, mU/dL, mU/ml|+|
|ua/mL|UA/ml, UA/ML, UA/mL, UA/ｍL||
|(arb_u)/mL|AU/ml, AU/mL|+|
|m(arb_u)/mL|mAU/ml, mAU/mL|+|
|(end_u)/mL|EU, EU/mL, EU/ml||
|FU/mL|FU/ml||
|L/d|l/day, L/day|+|
|g/d|g/day|+|
|mg/d|mg/day|+|
|ug/d|μｇ/day, μg/day, MCG/DAY|+|
|u/d|U/day|+|
|g/L|g/L, g/l|+|
|mg/L|mg/L, ｍｇ/L, mg/l, ｍg/L|+|
|ug/L|MCG/L, μｇ/L, μg/l, μg/L|+|
|g/dL|g/dl, g/dL|+|
|mL/dL|mL/dL, ml/dL|+|
|mg/dL|mg/dl, mg/dL|+|
|ug/dL|MCG/DL, μg/dl, μg/dL, μg/ｄｌ|+|
|ug/dL(rbc)|μg/dlRBC|+|
|ng/dL|ng/dl, ng/dL|+|
|mg/mL|mg/ml, mg/mL,|+|
|ug/mL|MCG/ML, μg/ml, μｇ/ml, μｇ/ｍｌ, μg/mL, ug/ml, μg/ｍL, ug/ml|+|
|ng/mL|ng/ml, ｎｇ/ｍｌ, ng/ml以下, ng/mL|+|
|pg/mL|pg/ml, ｐｇ/ml, pg/mL|+|
|meq/L|mEq/l, mEq/ｌ, mEq/L|+|
|ueq/L|μEq/l|+|
|mol/L|mol/l|+|
|mmol/L|mmol/L, mmol/l, m mol/L|+|
|umol/L|μmol/l, μMOL/L, μモル/l, umol/L|+|
|nmol/L|NMOL/L, nmol/l, nmol/L|+|
|pmol/L|pmol/l|+|
|fmol/L|f mol/l, fモル/l, FMOL/L|+|
|nmol/mL|nmol/ml, nmol/mL|+|
|pmol/dL|pmol/dl|+|
|pmol/mL|pmol/ml|+|
|umol/d|μmol/day|+|
|ng/(mL.hr)|ng/ml/hr, ng/ml/h, ng/mL/h|+|
|nmol/(mg(prot).h)|NMOL/MGP/H, nmol/mg　protein/時|+|
|g/g(creat)|ｇ/ｇ・CRE, g/gC, g/gcre|+|
|mg/g(creat)|mg/g・CRE, mg/g・Crn, mg/g.Cre, mg/g/Cr, mg/g-Cr, mg/g-Cr., mg/g Cr, mg/g・Cr, MG/G・CREA, mg/gCr|+|
|ug/g(creat)|MG/G.CRE, μｇ/ｇ・Cr, μg/gCr, μg/g・Crn, μg/g.Cre|+|
|ug/mg(creat)|μg/mg・Cr, μg/mg.Cr|+|
|ng/g(creat)|ng/g/Cr|+|
|pg/mg(creat)|pg/mgCRE, pg/mg・Crn|+|
|umol/g(creat)|μmol/g・Cr|+|
|nmol/mmol(creat)|nmol/mmolC, nM/mMCr, nM/l, nM/mM.Cr, Nモル/MモルC, nM/mM Cr|+|
|nmolBCeq/mmol(creat)|nMBCE/mMCr, nmolBCE/, nMBCE, BCE/mMCr, nMBCE/L, nmolBCE/L, nmol BCE/L, nM BCE, nM BCE/L, nmol BCE||
|mosm/kg_h2o|mOsm/KgH2O, MOSM/KGH, mOsm/kg, mOsm/Kg, mOsm/l, mOsm/L|+|
|L/min|L/min|+|
|mL/min|ml/min|+|
|ｍL/min(bsa)|ml/min, ml/分, ｍｌ/分・1,73㎡, ml/min/, ｍｌ/分・1,73㎡|+|
|logiu/mL|LogIU/ml, LogIU/mL, Log IU/mL, Log IU/m, L.IU/ml, LOGU/ML||
|logcopies/mL|Logコピー/m, Logコヒ゜ー/, Log/ml, LC/ml, Lgコピ/mL||
|LGeq/mL|LGE/ml, LGE/mL||
|copies/mL|コピー/ml, cp/mL||
|copies/ug|コピ-/μg, コピー/μg, /μgRNA, c/μgRNA, copy/μgR, コヒ゜ー/μgRNA||
|ng/10*7cells|ng/10\S\7Cel, ng/10\S\7cells, ng/10\S\7, ng/10^7PLT, ng/10*7PLT||
|copies/assay|コピー/アッセイ, コピ-/アツセ, コヒ゜-/アツセイ||
|kg|Kg, ｋｇ, kg|+|
|mL|ml, ｍＬ, mL|+|
|uL|μl|+|
|m|m|+|
|cm|cm, ｃｍ|+|
|mm|ｍｍ, mm|+|
|S/CO|S/CO, S/COミマン, S/co||
|C.O.I|C.O.I, COI, C.O.I., CO.Index||
|class|クラス||
|cpm|CPM, cpm||
|EV|EV||
|fl|fl, μm3|+|
|pg|pg|+|
|hr min|時　分, 時、分||
|min sec|分　秒, 分、秒, 分,秒, 分 秒||
|hr|時間|+|
|min|分|+|
|sec|秒, SEC., SEC|+|
|index|INDEX, index値, Index||
|(knk_u)|Ｕ, 単位, U, K-U, KU|+|
|(u)|U||
|LC|100LC, LC||
|mm/hr|mm/1H|+|
|mm(hg)|mmHg|+|
|pcs|個, 個/WBC100, /100WBC, /100個, コ/100WBC||
|permil|‰, △13cパーミル, バーミル, ハ゜-ミル||
|(rpr_u)|R.U., RU||
|(tit_u)|T.U., TU||
|(beth_u)/mL|ベセスダU/ml, ヘ゛セスタ゛U/, BU/mL||
|type|型, TYPE||
|group|グループ, グル-プ||
|score|スコア||
|(hb)|bpm|+|
|S/N|S/N比||
|(ppb)|ppb|+|
|(ph)|pH|+|
|cel|℃|+|
|.|バイ, 倍, ハ゛イ|+|
|.10*6/mL|10\S\6/mL, x10^6/mL||
|eiu|EIU||
|kiu/mL|KIU/ml|+|
|mL/d|mL/day|+|
|nu/mL|nU/mL|+|
|vol%|Vol%||
|.10*5/mL|X100000/|+|
|nil(spot)|スポット||
|/(5.10*4(wbc))|個/15万W||
