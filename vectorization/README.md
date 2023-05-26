# Combining Run-time Checks and Compile-time Analysis to Improve Control Flow Auto-Vectorization
  * B. Liu et al.
  * [PACT 2022](https://doi.org/10.1145/3559009.3569663)

## Abstract
  * コンパイラは**自動ベクトル化**する際には，SIMD命令を利用するようにコード変換を行う．
  * コンパイラは条件分岐が**発散**していると**保守的**に仮定するので，自動ベクトル化するときは制御フローが問題になる．
  * しかし，実行時に全てのSIMDレーンが同じ実行経路に従うことがよくある．
  * この性質を，**dynamic uniformity**と呼ぶ．
  * 本論文では，**VecRC**を提案する．
  * VecRCは，動的に制御フローがuniformしているか検査する実行時チェックを用いる新たなコンパイル時の手法である．
  * 動的にuniformしているとの仮定の元で，最新の手法よりも制御フロー自動ベクトル化を改善するコンパイル時解析を行う．
  * VecRCは，制御依存しているループ繰越し依存があるループをベクトル化するためにdynamic uniformityを利用する．
  * 既存手法は，楽観的にベクタコードを実行するために投機実行を行い，実行時の仮定が破られた場合には，正しくない計算を正さなければならない．
  * VecRCはそのような依存を投機実行のオーバヘッドなしにサポートするために，uniformityに基づくコンパイル時解析を行う．
  * 実行時チェックのprofitabilityを予測し，特定のプロファイリングの必要性や既存手法で必要とされる時間のかかる自動チューニングをなくすために，確率に基づくコストモデルを提案する．
  * VecRCはLLVM上で，SPEC2017, NPB, Parboil, TSVC, Rodiniaのベンチマークについて，Intel SkylakeとIBM Power 9マシンで評価された．
  * Skylakeマシンでは，幾何平均で，Region Vectorizer, GCC, Clang, ICC対して1.31x, 1.20x, 1.19x, 1.06xのスピードアップを得た．