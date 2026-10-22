---
type: idea
title: "卒論作業計画: 真値既知の四層疑似データで接地の効果と非同定性を測る"
description: "親 idea（四層疑似データで接地の効果と非同定性を測る）を学部 4 年の卒論として回すための作業計画。問いを 3 つ（外挿での増殖予測の改善・同等性能モデル間の中間層のばらつき・中間層を経由しているか）に絞り、中間発表 11 月上旬・提出 1 月中旬・最終発表 2 月中旬の日程、本人と指導側の分担、既存研究との再現・借用・差分を定める。"
hypothesis: "e_coli_core から作った四層疑似データ上で、直結・配線のみ・接地 joint・MOMA 型（迂回経路あり）・ridge の 4＋1 モデルを比べれば、約 14 週で RQ1〜3 の数字と検証手続きのチェックリストを卒論として出せる。"
stage: seed
confidence: medium
status: draft
tags: [thesis-plan, synthetic-data, identifiability, leakage, schedule]
addresses: [problems/latent-representation-nonidentifiability, problems/concept-layer-leakage]
related_ideas: [ideas/idea-multilayer-phenotype-grounding, ideas/idea-intervention-leakage-test, ideas/idea-grounding-external-validation]
sources:
  - { id: memo20260909subtheme4, resource: ../sources/memo20260909subtheme4.md, title: "研究テーマ記述（卒論テーマ集 v5 のサブテーマ4）", relation: inspired-by }
  - { id: kim2016moma, resource: ../sources/kim2016moma.md, title: "MOMA — 主たる先行研究（実データ側。同じ大腸菌・ほぼ同じ層構成）。構造を MOMA 型として比較に入れる", relation: builds-on }
  - { id: kontolati2026binnomics, resource: ../sources/kontolati2026binnomics.md, title: "Kontolati 2026 — 主たる先行研究（真値既知の合成データ側）。自前の生成器で追認する", relation: builds-on }
  - { id: caranzano2026binnillusion, resource: ../sources/caranzano2026binnillusion.md, title: "解釈性の幻想 — 動機・指標の出典・再現の練習台", relation: builds-on }
  - { id: margeloiu2021cbm, resource: ../sources/margeloiu2021cbm.md, title: "CBM の leakage — oracle 比較・介入の手順", relation: builds-on }
  - { id: shin2023intervention, resource: ../sources/shin2023intervention.md, title: "介入テストの手順", relation: builds-on }
  - { id: kumar2021mlfluxomics, resource: ../sources/kumar2021mlfluxomics.md, title: "FBA による人工教師データ", relation: builds-on }
  - { id: sheth2023coopcbm, resource: ../sources/sheth2023coopcbm.md, title: "シフトの型", relation: adjacent }
  - { id: esserskala2023reliable, resource: ../sources/esserskala2023reliable.md, title: "シャッフル対照", relation: builds-on }
  - { id: davidi2016kapp, resource: ../sources/davidi2016kapp.md, title: "生成器の真の k_app", relation: adjacent }
  - { id: steven2026einn, resource: ../sources/steven2026einn.md, title: "制約のみの対照（伸びしろ）", relation: adjacent }
  - { id: sastry2019imodulon, resource: ../sources/sastry2019imodulon.md, title: "iModulon — 発現を少数の疎なモジュールの和で作る仮定の実データ上の根拠", relation: builds-on }
  - { id: sanchez2017gecko, resource: ../sources/sanchez2017gecko.md, title: "GECKO 原典 — v ≤ kcat·e とプロテオーム予算の定式化", relation: builds-on }
  - { id: mao2022ecmpy, resource: ../sources/mao2022ecmpy.md, title: "ECMpy / eciML1515 — 大腸菌の酵素制約モデルと kcat 表", relation: builds-on }
  - { id: obrien2013mememodel, resource: ../sources/obrien2013mememodel.md, title: "大腸菌 ME-model — 既存の 4 層直列の機構モデル（差別化の相手）", relation: departs-from }
  - { id: lloyd2018cobrame, resource: ../sources/lloyd2018cobrame.md, title: "COBRAme / iJL1678b-ME — 第 2 の生成器の候補", relation: adjacent }
  - { id: karr2012wholecell, resource: "https://doi.org/10.1016/j.cell.2012.05.044", title: "Karr 2012 — whole-cell model の原典（未取り込み、PDF は手動配置待ち）" }
  - { id: macklin2020wholecell, resource: "https://doi.org/10.1126/science.aav3751", title: "Macklin 2020 — 大腸菌の whole-cell model（未取り込み、PDF は手動配置待ち）" }
  - { id: schaffter2011genenetweaver, resource: "https://doi.org/10.1093/bioinformatics/btr373", title: "GeneNetWeaver — 正解つきの発現シミュレータによる制御網推定の採点（DREAM）" }
  - { id: dibaeinia2020sergio, resource: "https://pubmed.ncbi.nlm.nih.gov/32871105/", title: "SERGIO — 制御網に基づく単一細胞の発現シミュレータ（Cell Systems 11:252）" }
  - { id: machado2014systematic, resource: ../sources/machado2014systematic.md, title: "Machado 2014 — 発現→フラックス手法の実データでの横並び比較（真値つき合成データは使わない）", relation: departs-from }
created: 2026-10-08
generated: { by: claude-code/claude-opus-5-5, at: 2026-10-21T06:15:42Z }
root: research_synlayer
---

# 卒論作業計画: 真値既知の四層疑似データで接地の効果と非同定性を測る

> **注記:** [idea-multilayer-phenotype-grounding](./idea-multilayer-phenotype-grounding.md)（親 idea）の作業計画だけを分離したページ（2026-10-08、人間の依頼）。研究の設計と根拠は親 idea に、卒論として何をいつ誰がやるかはこのページに置く。人間と相談して直す前提の**たたき台**なので `status: draft`。


> **注記:** 学部 4 年の卒論として本テーマを回すためのたたき台。[親 idea](./idea-multilayer-phenotype-grounding.md) のスケッチとネクストアクションは研究テーマ全体の設計で、卒論の期間には収まらない（モデル 9 種・シフト 3 型・理論の条件 6 つ）。ここでは**問いを 3 つに絞り、残りを「伸びしろ」に回した**。日程は **中間発表 11 月上旬・卒論提出 1 月中旬・最終発表 2 月中旬**（2026-10-08 に人間が指定）。着手から中間発表まで約 4 週、提出まで約 14 週（年末年始を含む）しかないので、(1) 決めごとを最初の 1 週で固める、(2) 実験は 12/20 で凍結する、(3) 序論と関連研究は 11 月中に並行して書く、の 3 つを前提に組んだ。

## 卒論で答える問い（3 つに絞る）

| | 問い | 測る量 | 対応する反証条件（親 idea） |
|---|---|---|---|
| **RQ1** | 中間層（$e$・$v$）を真値で教師づけると、**学習に使っていない炭素源**での $\mu$ の予測は、同じネットワークで教師を外したモデルより良くなるか | 外挿型の分割での $\mu$ の誤差 | 1 |
| **RQ2** | $\mu$ の性能が同等なモデルどうしで、中間層 $v$ はどれだけ散るか。教師づけでどれだけ減るか | 20 シード間の $v$ のばらつき、$v$ の真値との $R^2$ | 2・6 |
| **RQ3（最小版）** | 教師づけたモデルの $\mu$ は、本当に $v$ を経由しているか | テスト時に予測 $\hat v$ を真値に差し替えたときの $\mu$ の改善（分布内と分布外）と、真値の $v$ だけで学習した下流（oracle）との差。MOMA 型では、差し替えで変わるのは $v$ のヘッドの項だけなので、$\mu$ がどれだけ動くかと各ヘッドの重みが、迂回経路への依存度を直接示す | 8 |

RQ3 は追加の学習がほぼ要らない（学習済みモデルの $\hat v$ を差し替えて推論し直すだけで、oracle は $v \to \mu$ の小さなモデル 1 つ）ので残した。

**全体像（生成器・共通のネットワーク・比較するモデル・問いの対応）**

![卒論計画の全体像](../assets/plan-multilayer-phenotype-grounding-models.svg)

図の原本は [`../assets/plan-multilayer-phenotype-grounding-models.dot`](../assets/plan-multilayer-phenotype-grounding-models.dot)（Graphviz）。`dot -Tsvg` で SVG を作り直せる。モデルの定義と学習手順は下の「日程と成果物」内の「モデル」と疑似コードを参照。

**卒論の主成果は「数字」と「手続き」の 2 つ**とする。数字は RQ1〜3 の結果で、肯定でも否定でも成果になる（真値が既知なので必ず出る）。手続きは、実データで「中間層を接地できた」と主張するときに何をどの順で確かめるかのチェックリストで、[idea-grounding-external-validation](./idea-grounding-external-validation.md) と [idea-intervention-leakage-test](./idea-intervention-leakage-test.md) に渡す。

## 既存研究との関係：再現・借用・差分

### 主たる先行研究は 2 本、Caranzano は動機

| 研究 | 役割 | 卒論との近さ |
|---|---|---|
| **[kim2016moma](../sources/kim2016moma.md)（MOMA）** | **実データ側の主たる先行研究。** 同じ大腸菌・ほぼ同じ層構成（転写 → タンパク質 → 代謝物 → フラックス → 増殖）で、層ごとに実測値で学習し、未観測条件（LOCO）で増殖を予測した | 生物と問題設定が最も近い |
| **[kontolati2026binnomics](../sources/kontolati2026binnomics.md)** | **合成データ側の主たる先行研究。** 真値既知の ODE データで、中間層の教師あり／なしとラベル量を比べた（親 idea でも「最も直接の先行研究」） | 実験の型が最も近い |
| [caranzano2026binnillusion](../sources/caranzano2026binnillusion.md) | **動機。** テーマ集の原文が引く「中間層は何も意味していない」という問題提起。コードが公開されているので、指標の出典と再現の練習台にする | 問題提起 |

**序論の軸は MOMA との対比に置く。** MOMA は実データで「層を入れると増殖の予測が少し良くなる」ところまでを示した（条件の記述だけからの予測が PCC 約 0.60、5 層の統合で 0.65。前者は図5f からの目視の概値）。MOMA の中間層は上流から順に推定されるが、増殖は入力層を含む各層のヘッドの重み付き和で、中間層を通らなくても予測できる構造になっている。実データには中間層の真値が無いので、**そのとき中間層が正しいのか、本当に使われているのかは測れていない。** 卒論はこの問いを真値既知の疑似データで答え（RQ2・RQ3）、MOMA と同じ構造のモデル（MOMA 型）を並べて、迂回経路の有無で答えが変わるかを示す。

### 要素ごとの扱い

| 要素 | 出典 | 卒論での扱い |
|---|---|---|
| 同じ大腸菌・ほぼ同じ層構成で、層ごとに実測値で学習し未観測条件で増殖を予測する | [kim2016moma](../sources/kim2016moma.md) | **主たる先行研究として位置づけ、その構造（independent 学習の中間層カスケード＋入力層を含む各層の増殖ヘッドの重み付き和）を疑似データ上に移した「MOMA 型」を比較モデルに入れる**（2026-10-08、人間の指示）。各層のモデル（RNN・LASSO・FBA）は移さず、他のモデルと同じネットワークの部品で組むので、MOMA そのものの再現ではない。実データでの再現は [idea-ecomics-grounding-benchmark](./idea-ecomics-grounding-benchmark.md) の範囲。中間層の上乗せ（PCC 約 0.60 → 0.65）を RQ1 の実データでの参照値として引く |
| teacher-student の統制実験、20 個の初期値、指標（cosine 類似度・相対 L2・中間層活性の $R^2$） | [caranzano2026binnillusion](../sources/caranzano2026binnillusion.md) | **再現**（公開コードで回帰タスクを 1 設定。「cosine 0.05–0.20」の帯に入るかを確かめる。**3 日で打ち切る時間箱**とし、動かなければ再現は諦めて指標だけ借りる）→ 指標と実験の型をそのまま**借用** |
| 真値既知の合成データで中間層の教師あり／なしを比べる、教師なしでは出力への感度が大きい中間量だけが回復する | [kontolati2026binnomics](../sources/kontolati2026binnomics.md) | **自前の生成器で追認**（感度が大きい反応ほど配線のみモデルでも回復する、が再現されるか）。RQ2 の図から追加の実験なしに読める。期待どおりの結果が出るべき箇所で、生成器とモデルの実装の検査を兼ねる |
| フラックスを FBA で作って人工の教師データにする | [kumar2021mlfluxomics](../sources/kumar2021mlfluxomics.md) | **借用**（生成器の作り方） |
| 中間層を真値に差し替える oracle 比較と介入テスト | [margeloiu2021cbm](../sources/margeloiu2021cbm.md)・[shin2023intervention](../sources/shin2023intervention.md) | **手順を借用**（元論文の画像データでの再現はしない） |
| シフトを型で作り分け、型ごとに判定する | [sheth2023coopcbm](../sources/sheth2023coopcbm.md) | **考え方だけ借用**。卒論では外挿型だけを扱い、ML 側に結果が無いこの型が差分になる |
| シャッフル対照と並べてばらつきを読む | [esserskala2023reliable](../sources/esserskala2023reliable.md) | **借用**（ラベルを壊したモデルの複製間のばらつきを基準線にする） |
| **teacher を代謝モデル（機構シミュレータ）にする** | — | **差分（新規）**。Caranzano の teacher は任意の NN、Kontolati は植物ホルモンの 4 変数 ODE |
| **四層直列（発現 → 酵素量 → フラックス → 増殖）を end-to-end で学習し、増殖はフラックスからだけ出す** | — | **差分**。直列の構造そのものは新しくない: MOMA も中間層を上流から順に推定するカスケードである。違いは 2 点で、(1) MOMA は各モジュールを独立に学習し（CBM の用語で independent 型）、増殖の損失が上流に届かない。(2) MOMA の増殖は入力層を含む各層のヘッドの重み付き和で、入力層から増殖への迂回経路がある。卒論のモデルは増殖をフラックスからだけ出すので、迂回経路が無い。**MOMA 型を比較に入れ、この 2 点の効果を実験で分ける**（下の「モデル」）。Kontolati は遺伝型 → 代謝物 → 表現型の 1 段 |
| **環境軸の外挿（未知の炭素源）での評価** | — | **差分（新規）**。MOMA の LOCO は属性の組み合わせが未観測なだけで、株・培地の値はどれかの訓練データに含まれる。Kontolati・Caranzano は分布内か系統の hold-out |
| **中間層の正しさ（真値との一致・$\mu$ の性能が同等なモデル間のばらつき・真値への差し替え）を、接地の有無で比べる** | — | **差分（新規）**。MOMA は実データなので中間層の正しさを測れず、層を足したときの予測の改善だけで効果を見た。Caranzano は教師なしのみ、Kontolati は複製間のばらつきを主結果にしていない |
| **相関ではなく値（単位つきのフラックス）での一致** | — | **差分**。Kontolati の損失は Pearson 相関で、値の損失は改善しなかったと報告している。同じ比較を代謝で行うと、それ自体が結果になる |

### 生成器の位置づけ：部品は借りもの、新しいのは使い方（2026-10-21 追記）

**生成器は「答えが分かっている練習問題を作る装置」である。** 実データ（[kim2016moma](../sources/kim2016moma.md) の Ecomics）では、モデルの中間層（酵素量やフラックスの予測）が当たっているかを確かめる正解が無い。生成器で作ったデータなら、発現・酵素量・フラックス・増殖のどの層にも正解が付いている。

**部品はどれも既存の研究から借りる。** 卒論で部品の新しさは主張しない。

| 生成器の部品 | 何をするか | 借りる先 |
|---|---|---|
| 発現 $X$ | 少数の「制御のスイッチ」の組み合わせで作る（低ランク） | [sastry2019imodulon](../sources/sastry2019imodulon.md): 大腸菌の 278 プロファイル・3,923 遺伝子の発現変動の 68% が、92 個の疎なモジュールで説明でき、うち 61 個が既知の転写制御因子に対応した |
| 酵素量 $e$ → フラックス $v$ | 酵素の量でフラックスに上限をかける（$v \le k_{app} e$） | [sanchez2017gecko](../sources/sanchez2017gecko.md)（GECKO の定式化）、[mao2022ecmpy](../sources/mao2022ecmpy.md)（大腸菌の eciML1515 と $k_{cat}$ 表）、[davidi2016kapp](../sources/davidi2016kapp.md)（$k_{app}$ の値） |
| フラックス $v$・増殖 $\mu$ | 代謝モデル（FBA）で計算して正解を作る | [kumar2021mlfluxomics](../sources/kumar2021mlfluxomics.md)・[faure2023amn](../sources/faure2023amn.md)・[culley2020mechanism](../sources/culley2020mechanism.md) |

**新しいのは次の 2 点である。**

1. **使う目的が逆。** 先行研究はこれらの部品を「現実の細胞を当てる」ために使う。GECKO は酵母の増殖速度や Crabtree 効果を当てるために酵素制約を入れ、[machado2014systematic](../sources/machado2014systematic.md) は発現からフラックスを当てる手法を比べた。卒論は同じ部品を「機械学習モデルの答え合わせ用の正解を作る」ために使う。予測の道具としては酵素制約が現実からずれることは欠点だが、生成器では、ずれの大きさを自分で決められること自体が目的になる。
2. **現実とのずれ（非理想性）の大きさを、実データで測られた値に合わせて振れる。** 現実の細胞は理想どおりには動かない。
   - mRNA とタンパク質が比例しない（[mRNA とタンパク質の乖離](../problems/mrna-protein-decoupling.md)）。
   - 酵素は満杯では働いておらず、酵素量で説明できるフラックス変化は 7〜18% しかない（[kochanowski2021global](../sources/kochanowski2021global.md)）。
   - 試験管の中と細胞の中で触媒速度が違う（log スケールで $r^{2}$ 0.62、[davidi2016kapp](../sources/davidi2016kapp.md)）。
   - 発現の変動の約 3 割は、モジュールでは説明できない（[sastry2019imodulon](../sources/sastry2019imodulon.md)）。

   これらを生成器の「つまみ」にして、文献の値の範囲で強弱を振る。すると結論を「酵素の飽和度のばらつきがこの程度までなら、中間層の教師は効く」のように、生物学の言葉で書ける。[caranzano2026binnillusion](../sources/caranzano2026binnillusion.md) のように任意のニューラルネットを教師にしたり、[kontolati2026binnomics](../sources/kontolati2026binnomics.md) のように 4 変数の ODE を教師にしたりすると、つまみが現実の何に当たるかを言えない。

**先行例との距離（2026-10-21 改訂: 当初は Machado 2014 を最も近い先行例としていたが、比べる軸ごとに近い先行例が違う）。**

| 比べる軸 | 近い先行例 | 本研究との違い |
|---|---|---|
| 4 層を直列につないだ機構モデル | ME-model（[obrien2013mememodel](../sources/obrien2013mememodel.md)、実装 [lloyd2018cobrame](../sources/lloyd2018cobrame.md)）、whole-cell model（Karr 2012[^karr2012wholecell]、大腸菌は Macklin 2020[^macklin2020wholecell]） | どれも現実の細胞を当てるためのモデルで、本研究の生成器より機構的に詳しい。ME-model は発現量も最適化の解として決まる決定論的なモデルで、乖離・飽和度などのずれを独立に振るつまみが無い。縮約した iJL1678b-ME でも 1 条件 10 分未満（FBA は 100 ms 程度）。なお ME-model の単一遺伝子の発現変化は実測と r = 0.14 しか合わず、実データの発現には最適性で説明できない成分が大きい。これは発現 $X$ を最適化の出力ではなく、ノイズを持つ外生の層として与える本研究の設計を支持する |
| 正解つきシミュレータで手法を採点する | GeneNetWeaver（DREAM の制御網推定コンテスト）[^schaffter2011genenetweaver]、SERGIO（単一細胞の発現）[^dibaeinia2020sergio] | 「機構シミュレータで正解を作り、手法を採点する」という使い方そのものの先例。ただし発現だけで代謝・増殖の層が無く、採点の対象は制御網の推定である。本研究が採点するのは、層を持つ予測モデルの中間層（正しさ・モデル間の食い違い・正解への差し替え） |
| 発現 → フラックスの手法を同じ土俵で比べる | [machado2014systematic](../sources/machado2014systematic.md) | 実測データ 3 件だけで、正解は 13C 標識からの推定値、評価は中心炭素代謝の出力だけ。結果は「どの手法も発現を使わない pFBA を安定して上回らない」で、実データでは写像を確かめにくいという本研究の動機を補強する |

したがって、**新しい 4 層の機構モデルを作ったとも、シミュレータで手法を採点したのが初めてとも主張しない。** 主張するのは「代謝の 4 層について、機械学習モデルの中間層の正しさを採点できる正解つきの土台を、ずれを独立に振れる形で作った」ことである。2026-10-21 の Web 検索でも、代謝の機構モデルから 4 層を正解つきで作り、機械学習の中間層を採点した例は見つからなかったが、これは「無い」ことの証明ではないので、卒論では「調べた範囲では」と限定する。詳しい機構モデルは競合ではなく、**結論が生成器の粗さに依存しないかを確かめる第 2 の生成器**として使える（伸びしろ 8）。

**卒論に書く一文の例**: 「層構造をもつ細胞の機構モデル（ME-model や whole-cell model）や、正解つきシミュレータによる手法の採点（GeneNetWeaver）は既にある。本研究はそれらを新しくするのではなく、既存の部品（FBA・酵素制約・発現のモジュール構造）を組み合わせて、代謝の 4 層について機械学習モデルの中間層の正しさを採点できる正解つきの疑似データを作る。現実とのずれの大きさを文献の実測値の範囲で独立に振れるよう、あえて粗い生成器を用いた点が本研究の工夫である。」

新規性の主張は「**MOMA が実データで示した層構成の予測について、代謝の機構モデルを teacher にした疑似データで、接地の効果と非同定性の大きさを定量した**」までに留める。手法の新規性は主張しない。

## 役割分担

| 担当 | 中身 |
|---|---|
| **本人** | 生成器・モデル・評価の実装、全実験、図、卒論の執筆。加えて、**本人が根拠を持って決めるべき研究上の選択**が 4 つある：(1) 生成器の非理想性（測定ノイズ・mRNA→タンパク質の乖離・$k_{app}$ の誤差）の大きさ、(2) 外挿型の分割（どの炭素源を抜くか）、(3)「$\mu$ の性能が同等」の判定基準（同等性検定 TOST の許容幅など）、(4) ばらつきの指標（分散・pairwise 距離のどちらを主にするか）。**時間が無いので、最初の週は下の既定値で走り出し、根拠は 11 月中に本人が文献で裏づけて（必要なら変えて）卒論に書く。** この 4 つの判断と根拠が卒論の「自分の仕事」の中心になる |
| **指導側** | **最初の週に**：3 つの問いへの絞り込みと既定値の承認。以後、週 1 回の進捗確認、10/29 の生成器の妥当性レビュー（下の確認項目）、12/20 の実験凍結の判断、1 月上旬の原稿の確認 |
| **既に用意済み（本Wiki）** | 先行研究の調査と設計の根拠（このページ、[系譜の総説](../topics/intermediate-layer-grounding.md)、source 34 本）。**本人は文献調査をやり直さず、下の必読 4 本と本ページから入る**。卒論の序論・関連研究の章は、このページの「既存研究との関係」の表と総説を下敷きにして書ける。新しい文献が要れば `/web-survey`・`/ingest` で足す |

**最初に総説で全体像をつかむ**（半日）: [中間層の接地と非同定性の系譜](../topics/intermediate-layer-grounding.md) の「主要な系譜・流派」と「タイムライン」を読み、配線だけ生物学的な BINN から中間層を実測で教師づける設計までの流れと、各論文の位置を把握する。「未解決の論点」は RQ の根拠なので、序論を書くときに読み直す。機械学習側の用語（independent／sequential／joint、leakage）は [Concept bottleneck model と leakage](../concepts/concept-bottleneck-model.md) で補う。

**必読 4 本**（総説のあとに、この順で）: [kim2016moma](../sources/kim2016moma.md)（実データ側の主たる先行研究。序論の軸）、[kontolati2026binnomics](../sources/kontolati2026binnomics.md)（合成データ側の主たる先行研究）、[caranzano2026binnillusion](../sources/caranzano2026binnillusion.md)（動機と指標）、[margeloiu2021cbm](../sources/margeloiu2021cbm.md)（leakage と RQ3 の手順）。FBA は論文ではなく COBRApy のチュートリアルで入る（[iML1515](../entities/iml1515.md) のページは後で読めばよい）。

**最初の週に走り出すための既定値**: (1) 非理想性は「発現の測定ノイズ 10%・乖離ノイズ 0.3（log 空間の標準偏差）・$k_{app}$ の誤差なし」の 1 設定、(2) 抜く炭素源は 2 種（例: 生成器で $\mu$ が中間程度のもの）を 1 つずつ抜く、(3) 同等の判定はテスト $\mu$ の RMSE が最良モデルから 5% 以内、(4) ばらつきは $\hat v$ の反応ごとのシード間標準偏差を、反応の真値の標準偏差で割った値。いずれも仮の値で、根拠づけは本人の仕事である。

## 日程と成果物

| 期間 | 本人の作業 | 成果物・確認の場 |
|---|---|---|
| **10/9–10/15**（1 週） | 総説と必読 4 本。COBRApy で e_coli_core の FBA を炭素源ごとに回す。指導側と範囲・既定値を確定 | 炭素源ごとの最大増殖速度の表 |
| **10/13–10/18**（並行、3 日の時間箱） | Caranzano の公開コードで回帰タスクを 1 設定再現 | 再現の 1 枚レポート（元論文の値と自分の値を並べる） |
| **10/16–10/29**（2 週） | 生成器 v1（下の仕様、最小構成）を実装し、確認項目 1〜3 を出す | **10/29 生成器レビュー**（指導側） |
| **10/30–中間発表**（約 1 週） | 発表準備。間に合えば ridge と直結（全結合）だけで RQ1 の予備の図を 1 枚 | **中間発表（11 月上旬）**: 問い・既存研究との関係の表・再現結果・生成器と確認項目・計画。予備の図は任意 |
| **中間発表後–11/29**（約 3.5 週） | モデル 4＋1 を実装し、ランダム分割と炭素源を抜く分割で 5 シードずつ比較（RQ1）。**並行して序論・関連研究の章を書く** | RQ1 の図、序論・関連研究の原稿 |
| **11/30–12/20**（3 週） | 20 シード × モデル 4 でばらつき（RQ2）、ラベルをシャッフルした対照、$\hat v$ の差し替えと oracle（RQ3）。**12/20 で実験を凍結** | RQ2・RQ3 の図 |
| **12/21–1/10**（年末年始を含む約 3 週） | 方法・結果・考察を書き、全章をつなぐ。検証手続きのチェックリストを付録にする。1/4 ごろに原稿を指導側へ | 卒論の完成稿（1/4 ごろ指導側へ） |
| **1/11–1 月中旬** | 指導側のコメントを反映して提出 | **卒論提出** |
| **提出後–2 月中旬** | 最終発表の準備。余力があれば伸びしろ 1（下）を発表の追加結果として足す | **最終発表** |

**生成器 v1 の仕様（最小構成）**
- 環境 $E$: 炭素源（e_coli_core で取り込める 8 種前後: グルコース・フルクトース・ピルビン酸・コハク酸・リンゴ酸・酢酸・乳酸・2-オキソグルタル酸など）× 取り込み上限の強さ（数段階）。酸素（好気・嫌気）の軸は時間があれば足す。
- 発現 $X$: $E$ から低ランクの制御プログラム（数個の潜在因子 × 遺伝子の負荷。負荷はランダムに固定）で作り、測定ノイズを足す。低ランクの根拠は [sastry2019imodulon](../sources/sastry2019imodulon.md)（上の「生成器の位置づけ」）。
- 酵素量 $e$: $X$ に遺伝子ごとの翻訳効率を掛け、乖離のノイズを足す（[mRNA とタンパク質の乖離](../problems/mrna-protein-decoupling.md)）。
- フラックス $v$: pFBA に $v_j \le k_{app,j}\, e_j$ を上限として課して解く。真の $k_{app}$ は [davidi2016kapp](../sources/davidi2016kapp.md) の大腸菌の値を使い、値の無い反応は分布から引いて補う（どの反応を補ったかを記録する）。上限の定式化は GECKO（[sanchez2017gecko](../sources/sanchez2017gecko.md)）に従う。ただし GECKO は酵素使用量を最適化の変数にするが、生成器では $e$ を外から与えて各反応の上限 $k_{app,j} e_j$ に置くだけでよい。補う値は分布から引く前に、eciML1515 の $k_{cat}$ 表（[mao2022ecmpy](../sources/mao2022ecmpy.md)）を候補にする。
- 増殖 $\mu$: バイオマス反応のフラックス。**中間層 $v$ からはバイオマス反応を除く**（含めたまま $v$ に教師をかけると、$\mu$ の教師を $v$ の 1 座標として直接与えることになる）。除いても $\mu$ は $Sv = 0$ を通じて他の反応の線形結合で決まるので、$v \to \mu$ の段は線形で足りる。これは「最後の段は機構で決まる」という設計どおりである。

**生成器の確認項目**（10/29 に指導側と見る）
1. **酵素の上限が実際に効いているか。** $v_j \le k_{app,j} e_j$ が効いている（等号で止まる）反応が条件ごとに何本あるか数える。ほとんど効いていないと、$v$ は $E$ の取り込み上限だけで決まり、$X \to e \to v$ の経路に情報が流れない。そうなると RQ1 は自明に「効かない」になる。**最大のリスクなので最初に確かめる。**
2. $\mu$ が炭素源の間で十分に散るか（全条件で同じ値だと外挿を測れない）。
3. 外挿型の分割で、抜いた炭素源の $v$ が訓練の値域の外に出るか（出なければ外挿型になっていない）。

**モデル（4＋1、2026-10-08 訂正・MOMA 型を追加）**: 4 つのモデルは、遺伝子 → 酵素 → 反応 → 増殖の 3 段を直列につないだ**同じ 1 つのネットワークの部品**で組み、マスクの有無・中間層の損失の重み $\lambda$・学習のしかた・増殖の出し方だけが違う（実装を 1 本にして時間を節約する）。

| モデル | 配線のマスク | 中間層の損失 | 何との差で何を測るか |
|---|---|---|---|
| **直結** | なし（同じ層数・同じ幅の全結合） | なし（$\lambda_{e} = \lambda_{v} = 0$） | 配線のみとの差 = 生物学的な配線の効果 |
| **配線のみ** | あり（GPR と酵素–反応の対応） | なし（$\lambda_{e} = \lambda_{v} = 0$） | **教師の効果を測る主たる対照**（接地・joint との違いは $\lambda$ だけ） |
| **接地・joint（提案）** | あり | あり（$\lambda_{e}, \lambda_{v} > 0$） | 配線のみとの差 = 中間層の教師の効果 |
| **MOMA 型（迂回経路あり）** | あり | あり（各段を自分の層の真値で独立に学習＝independent） | 増殖は入力 $X$・$\hat e$・$\hat v$ の各層に付けた線形ヘッドの重み付き和（重みは検証データでの成績に比例。[kim2016moma](../sources/kim2016moma.md) の Phenome layer と同じ）。**提案との差 = 学習法と迂回経路の効果の合計**。下のとおり同じ学習から 2 つに分けられる |
| ridge | — | — | 線形の $X \to \mu$。文献ベースライン |

> **注記（2026-10-08 訂正）:** 当初は直結を「接地モデルと同じネットワークで中間層の損失だけを外す」と書いていたが、接地モデルはマスクつきなので、それは配線のみと同一のモデルだった（親 idea §2.1 の時点からの重複）。直結はマスクを外した全結合とし、「教師だけを外した対照」の役は配線のみが担う。

**学習手順（大幅に簡略化した疑似コード）**

部品は共通で、どのモデルも次の 3 段から組む。

```python
f_e  : X -> e_hat     # 遺伝子 → 酵素（マスクつきなら GPR に沿った結合だけ）
f_v  : e -> v_hat     # 酵素 → 反応（バイオマス反応は v に含めない）
f_mu : v -> mu_hat    # 反応 → 増殖（線形）
```

**従来（MOMA 型、[kim2016moma](../sources/kim2016moma.md) の構造）**

```python
# ── 学習: 段ごとに別々に学習する。各段の入力には「真値」を使う ──
f_e.fit(X, e)                     # ① X → e        損失は e だけ
f_v.fit(e, v)                     # ② e（真値）→ v  損失は v だけ。μ の誤差は届かない
h_X = Ridge().fit(X, mu)          # ③ 各層から μ へのヘッドを別々に学習
h_e = Ridge().fit(e, mu)          #    （h_X は中間層を通らない＝迂回経路）
h_v = Ridge().fit(v, mu)
w = normalize(val_r2([h_X, h_e, h_v]))   # ④ 重みは検証データでの成績に比例

# ── 推論: 中間層は上流から順に推定するが、μ は各層ヘッドの重み付き和 ──
def predict(X):
    e_hat = f_e(X)
    v_hat = f_v(e_hat)
    return w[0]*h_X(X) + w[1]*h_e(e_hat) + w[2]*h_v(v_hat)
```

**提案（接地・joint）**

```python
# ── 学習: 全段を 1 つの損失で同時に学習する。各段の入力には上流の「予測」を使う ──
for X, e, v, mu in loader:
    e_hat  = f_e(X)
    v_hat  = f_v(e_hat)
    mu_hat = f_mu(v_hat)
    loss = mse(mu_hat, mu) + λe*mse(e_hat, e) + λv*mse(v_hat, v)
    loss.backward(); opt.step()   # μ の誤差が f_v・f_e まで逆伝播する

# ── 推論: μ は v_hat からだけ出す（迂回経路なし） ──
def predict(X):
    return f_mu(f_v(f_e(X)))
```

| | 従来（MOMA 型） | 提案（接地・joint） |
|---|---|---|
| 学習の単位 | 段ごとに別々（f_e・f_v・各ヘッド） | 全段を 1 つの損失で同時に |
| 学習時の各段の入力 | 上流の真値（$e$, $v$） | 上流の予測（$\hat e$, $\hat v$） |
| $\mu$ の誤差が上流の段に届くか | 届かない | 届く（$\lambda$ で中間層の教師と釣り合わせる） |
| $\mu$ の出し方 | $X$・$\hat e$・$\hat v$ の各ヘッドの重み付き和 | $\hat v$ からだけ |
| RQ3 で $\hat v$ を真値に替えると | $h_{v}$ の項（重み $w_{3}$）だけが変わる | $\mu$ の入力がすべて替わる |

**2 つの差を分けて読むための中間のモデル（追加の学習なし）**

```python
# 従来の学習済みの部品から、h_v の項だけを読む
def predict_independent_no_bypass(X):
    return h_v(f_v(f_e(X)))       # independent・迂回経路なし
# 提案 ↔ これ   = 学習法の効果
# これ ↔ 従来   = 迂回経路の効果
```

**対照・RQ3・伸びしろ**

```python
# 対照: 提案と同じコードで設定だけ変える
wiring_only = 提案(mask=GPR);  λe = λv = 0     # 配線のみ（提案との違いは λ だけ）
direct      = 提案(mask=None); λe = λv = 0     # 直結
ridge       = Ridge().fit(X, mu)

# RQ3: 学習し直さず、推論だけ差し替える
mu_int_prop = f_mu(v_true)                                           # 提案
mu_int_moma = w[0]*h_X(X) + w[1]*h_e(f_e(X)) + w[2]*h_v(v_true)      # 従来
mu_oracle   = Ridge().fit(v_true_train, mu_train).predict(v_true)    # 比べる上限

# 伸びしろ 1: sequential（上流の予測を固定して次の段の入力にする）
f_e.fit(X, e); e_hat = f_e(X).detach()
f_v.fit(e_hat, v); v_hat = f_v(e_hat).detach(); f_mu.fit(v_hat, mu)
```

**MOMA 型と MOMA の違い。** 構造（independent 学習の中間層カスケード、入力層を含む各層の増殖ヘッドの重み付き和）は MOMA に合わせたが、次の 3 点は合わせていない。卒論にはこの 3 点を明記する。
- 各層のモデル: MOMA は RNN・LASSO・FBA、MOMA 型は他のモデルと同じマスクつきの NN の部品（比較を学習法と迂回経路の違いに絞るため）。
- 入力層の中身: MOMA は条件の記述（株・培地など 612 特徴）、MOMA 型は他のモデルと同じ発現 $X$（入力をそろえるため）。条件の記述 $E$ を入れる版は、迂回経路をさらに強くする変種として伸びしろに回す。
- 代謝物層: 生成器に無いので持たない。

**学習法と迂回経路の 2×2。** 提案（joint・迂回経路なし）、independent・迂回経路なし（MOMA 型の $v$ ヘッドだけ）、MOMA 型（independent・迂回経路あり）の 3 つが中核で埋まる。残る 1 マス（joint・迂回経路あり＝親 idea の side-channel）は伸びしろ 2。

[親 idea](./idea-multilayer-phenotype-grounding.md) のスケッチ §2.1 の残りは伸びしろに回す。

## 伸びしろ（予定より早く進んだら、または提出後に最終発表向けに、上から順に）
1. 接地・sequential を足す（上流の予測を固定して次の段を学習。親 idea の反証条件 9、joint との比較で leakage を読む）。
2. joint・迂回経路ありを足す（提案のネットワークに $X \to \mu$ の枝を並べる。親 idea §2.1 の side-channel）。学習法と迂回経路の 2×2 の残り 1 マスが埋まる。あわせて MOMA 型の入力層を条件の記述 $E$ にした変種も試せる。
3. 制約のみ（$\lambda_{e} = 0$）を足す（親 idea の反証条件 7、[steven2026einn](../sources/steven2026einn.md)）。
4. 非理想性を 1 軸（乖離の強さ）だけ振って、効果が出る領域を図にする（親 idea の反証条件 3）。
5. 劣化型のシフト（テストでだけ $X$ のノイズを大きくする）を足す（親 idea §2.2）。
6. 観測する反応を間引いて completeness $C$ を下げ、leakage との関係を見る（親 idea §2.1）。
7. 生成器を [iML1515](../entities/iml1515.md) に拡張する、[Ishii 29 条件](../sources/ishii2007multiomics.md) の実データで追試する。
8. 第 2 の生成器で結論が保たれるかを見る（2026-10-21 追記）。ME-model（[lloyd2018cobrame](../sources/lloyd2018cobrame.md) の iJL1678b-ME）で条件を数十に絞って作り、$k_{eff}$ に対数正規の乗数をかけ、出力に v1 と同じノイズを後から被せる。RQ1・RQ2 のモデル間の順位と符号が v1 と同じかを見る。環境構築（4 倍精度の LP ソルバ qMINOS など）で詰まりやすいので、まず 1 条件の求解に半日を上限とし、本流には入れない。

**卒論の射程外**: [idea-grounded-shared-latent-space](./idea-grounded-shared-latent-space.md)（単一の潜在空間への着地）、[idea-ecomics-grounding-benchmark](./idea-ecomics-grounding-benchmark.md)（実データの大規模比較）、親 idea §2.4 の In-N-Out の理論の条件の検査。

## つまずきやすい点と代替案
- **10/29 の確認項目 1 で酵素の上限が効かない。** $k_{app}$ を一律に縮めて上限を効かせる、またはプロテオームの総量の制約（GECKO 型）を足す。どちらも生成器の仮定なので、卒論に明記する。直しに 1 週以上かかりそうなら、中間発表は「確認項目で見つかった問題と対処方針」を見せる回にする。
- **中間発表までに RQ1 の図が出ない。** 想定内。中間発表の必須は問い・既存研究との関係・再現・生成器までとした。
- **RQ1 で差が出ない。** 親 idea の反証条件 1 にあたる、正当な否定的結果である。RQ2・RQ3 は差の有無にかかわらず出るので、卒論は成立する。
- **12/20 までに RQ2 の 20 シードが回らない。** MOMA 型の追加で計算量は 3 モデルの約 4/3 倍になる。シード数を 10 に落とす（Caranzano は 20、Esser-Skala は 50）。e_coli_core の規模なら CPU で足りる見込みだが、11 月前半に 1 回あたりの学習時間を測って見積もり直す。
- **執筆が年末に集中する。** 序論・関連研究は 11 月中、方法は実験と並行して書き、12/21 以降は結果・考察に専念する。

## 反証条件 (Falsification)

この計画そのものが誤っていたと分かる条件（研究結果の反証条件は親 idea の 1〜9）。

1. **10/29 の確認項目 1 で、$k_{app}$ を縮めてもプロテオーム総量の制約を足しても酵素の上限が効かない。** e_coli_core の四層生成器では $X \to e \to v$ に情報が流れず、RQ1 は設計上答えられない。生成器の構成（モデル規模・制約の型）を見直す必要がある。
2. **11 月前半の見積もりで、20 シード × 4 モデル × 2 分割が 12/20 までに回らない。** シード数を 10 に落としても回らなければ、RQ2 をモデル 2 つ（配線のみと接地 joint。違いが $\lambda$ だけの組）に絞る。
3. **中間発表の時点で、Caranzano の再現も生成器の確認項目も出ていない。** 日程の前提（最初の 1 週で決めごとを固める）が崩れているので、伸びしろを全部捨て、RQ3 も外して RQ1・RQ2 だけの計画に組み直す。

## 関連ページ (Related)
- [idea-multilayer-phenotype-grounding](./idea-multilayer-phenotype-grounding.md) — 親 idea（研究の設計と根拠）
- [idea-intervention-leakage-test](./idea-intervention-leakage-test.md) — RQ3 の介入の手順
- [idea-grounding-external-validation](./idea-grounding-external-validation.md) — 卒論の手続き（チェックリスト）を受け取る側
- [内部表現の非同定性](../problems/latent-representation-nonidentifiability.md) / [leakage](../problems/concept-layer-leakage.md)
- [研究テーマ記述](../sources/memo20260909subtheme4.md) — 卒論テーマ集 v5 の原文

[^karr2012wholecell]: Karr J.R. et al. "A whole-cell computational model predicts phenotype from genotype." *Cell* 150:389–401 (2012).
[^macklin2020wholecell]: Macklin D.N. et al. "Simultaneous cross-evaluation of heterogeneous *E. coli* datasets via mechanistic simulation." *Science* 369:eaav3751 (2020).
[^schaffter2011genenetweaver]: Schaffter T., Marbach D., Floreano D. "GeneNetWeaver: in silico benchmark generation and performance profiling of network inference methods." *Bioinformatics* 27:2263–2270 (2011).
[^dibaeinia2020sergio]: Dibaeinia P., Sinha S. "SERGIO: a single-cell expression simulator guided by gene regulatory networks." *Cell Systems* 11:252–271 (2020).
