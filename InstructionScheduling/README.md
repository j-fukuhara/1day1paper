# Graph Transformations for Register-Pressure-Aware Instruction Scheduling
  * G. Shobaki et al.
  * [ACM Compiler Construction 2022 (CC 2022)](https://doi.org/10.1145/3497776.3517771)

## Abstract
  * レジスタ圧力を考慮した命令スケジューリングのためのグラフ変換を行うアルゴリズムを提案．
  * **データ依存グラフ**（Data Depandence Graph, **DDG**）に対して変換を行い，冗長もしくは局所解を除去する．
  * レジスタ圧力（RP）は考えず命令レベル並列性（ILP）を最大化するグラフ変換[10](https://doi.org/10.1007/s10951-005-2862-8)は，これまでに提案されているが，実践的には問題があった．
  * 本論文では，実践的に重要であるRPを最小化するグラフ変換を提案する．
  * RPを評価する様々なコスト関数に対して，提案手法は最適である．
  * 最適解を求めるB&Bアルゴリズムを適用する前に提案手法を適用することで，解の探索空間のサイズを低減できる．
  * 提案手法をLLVM上に実装し，CPU（SPEC CPU2017 floating-pointベンチマーク）とGPU（PlaidMLベンチマーク）に対して実験を行った．
  * 実験では，ほぼ同じ実行時間のパフォーマンスで，コンパイル時間を大幅に短縮できたことを示した．

---

# Exploring an Alternative Cost Function for Combinatorial Register-Pressure-Aware Instruction Scheduling
  * G. Shobaki et al.
  * [ACM TACO 2019](https://doi.org/10.1145/3301489)
  
## Abstract
  * レジスタ割付け前に，**レジスタ圧力**（register pressure, **RP**）を最小化する，もしくはレジスタ圧力と**命令レベル並列性**（instruction-level parallelism, **ILP**）のバランスを取る目的のアルゴリズムが多数提案されている．
  * 本論文では，**Sum of Live Interval Lengths** (**SLIL**)というレジスタ圧力コスト関数を提案する．
  * 従来のピークコスト関数は，スケジューリングの中でレジスタ圧力が最も高いプログラム点を考える．
  * SLILコスト関数は，従来とは異なり，スケジューリングの中で全てのプログラム点を考える．
  * 本論文では，SLILコスト関数を最小化する**Branch-and-Bound** (**B&B**)アルゴリズムを提案する．
  * アルゴリズムは，先行研究で提案されたhistory utilization techniqueと同様に，２つの動的な下限(dynamic lower bound)に基づいている．
  * LLVMに実装し，先行研究のB&Bアルゴリズムと比較して，スピルコードを減らすことができた．
  * 実行速度の比較はCPU2006ベンチマークで行い，LLVMのデフォルトスケジューラと比較，FP2006に対するスピードアップは幾何平均で4.22%．
