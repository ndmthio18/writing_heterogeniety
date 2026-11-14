# 物理量与符号书写规范

## 1. 适用范围与依据

本文件是本项目 LaTeX 稿件的符号 house style，供正文、补充材料、图注和表格统一使用。主要参考：

- Chen et al. (2026), *Quasi-Static Pore-Network Modeling for Evaporation-Driven Salt Transport and Precipitation in Porous Media*, *Water Resources Research*, 62, e2026WR043446，特别是 PDF 第 5--12、15--16 页。
- 本项目决定：**质量分数统一用大写 \(X\)**；参考论文中的小写 \(x\) 仅用于摩尔分数。

参考论文自身主要采用摩尔量表述，并未建立“大写 \(X\) 表示质量分数”的规则。因此，下文将“参考论文中可直接观察到的写法”和“本项目新增规则”明确区分。

## 2. 强制规则

### 2.1 分数、浓度与饱和度不得混用

| 物理量 | 统一符号 | 示例 | 说明 |
|---|---:|---|---|
| 质量分数 | \(X\) | \(X_{g,s}^{w,\mathrm{eq}}\)、\(X_{g,\mathrm{amb}}^{w}\) | 本项目规则；无量纲 |
| 摩尔分数 | \(x\) | \(x_{g,s}^{w,\mathrm{eq}}\) | 与参考论文一致；无量纲 |
| 物质的量浓度 | \(c\) | \(c_{\mathrm{sol}}^{\mathrm{Na}}\) | 必须给出单位，如 mol L\(^{-1}\) 或 mol m\(^{-3}\) |
| 饱和度 | \(S\) | \(S_{w,i}\) | 相占可用孔隙体积的比例；无量纲 |
| 体积分数 | \(\phi\) | \(\phi_{s,i}\) | 例如沉淀盐体积分数；无量纲 |

禁止事项：

- 不再用 \(Y\) 表示质量分数。
- 不用小写 \(x\) 表示质量分数。
- 不把质量分数、摩尔分数和有量纲浓度统称为同一个“concentration”而不说明具体定义。
- 同一符号在同一稿件中不得跨物理含义复用。

### 2.2 本稿蒸发边界的固定写法

当前正文采用：

~~~latex
\begin{equation}
j_{\mathrm{evap}} =
\frac{\rho_{g,f}D_g^{w,\mathrm{N_2}}}{\delta_g}
\left(X_{g,s}^{w,\mathrm{eq}}-X_{g,\mathrm{amb}}^{w}\right).
\end{equation}
~~~

其中，\(X_{g,s}^{w,\mathrm{eq}}\) 和 \(X_{g,\mathrm{amb}}^{w}\) 分别为界面平衡水蒸气质量分数和环境水蒸气质量分数；\(D_g^{w,\mathrm{N_2}}\) 为气相中水蒸气--氮气二元扩散系数。对应的界面水蒸气摩尔分数写成 \(x_{g,s}^{w,\mathrm{eq}}\)。本稿不引入或解释面积修正因子 \(\chi_A\)。如果未来模型确实重新使用该因子，必须先给出其定义、数值来源、量纲及其对面积/通量定义的影响，不能只把它作为未解释系数放入方程。

## 3. 上下标层级

### 3.1 参考论文的可复用逻辑

参考论文通过上下标区分物理角色，例如：

- \(x_{g,i}^{w}\)：孔体 \(i\) 中气相水蒸气摩尔分数；
- \(x_{w,i}^{\mathrm{salt}}\)：孔体 \(i\) 中液相盐摩尔分数；
- \(J_{\mathrm{diff},g,ij}^{w}\)：孔体 \(i\) 与 \(j\) 之间气相水蒸气扩散通量；
- \(\rho_{\mathrm{mol},g,i}\)：孔体 \(i\) 中气相摩尔密度；
- \(S_{w,i}\)、\(V_{w,i}\)、\(g_{w,ij}\)：液相饱和度、液体体积和液相导流系数。

其基本语义顺序是：

1. 主字母表示物理量类型；
2. 组分可放在上标；
3. 相、位置、孔体/喉道编号放在下标；
4. diff、mol、amb、sat、max、eq 等描述性标签用正体；
5. \(i,j,n\) 等可变索引用斜体。

### 3.2 本项目采用的 QSPNM 层级

本项目直接采用参考论文的层级，不再保留“组分放在第一个下标”的旧写法：

- **组分放上标**：\(w\)、\(\mathrm{Na}\)、\(\mathrm{NaCl}\)、\(\mathrm{salt}\)；
- **相放在第一个下标**：\(g\) 表示气相，\(w\) 表示液相（水相）；
- **位置或离散索引放在后续下标**：\(s\)（surface）、\(\mathrm{amb}\)（ambient）、\(i,j\)（孔体或连接单元）；
- **状态或过程限定与其语义层同列，并使用正体**：\(\mathrm{eq}\)、\(\mathrm{sat}\)、\(\mathrm{max}\)、\(\mathrm{diff}\)、\(\mathrm{mol}\)；
- 逗号用于分隔同一上下标层中的不同角色，例如 \(X_{g,s}^{w,\mathrm{eq}}\)；
- 无相或位置索引时，只保留必要层级，例如总 Na 物质的量写成 \(n^{\mathrm{Na}}\)，Na 溶液浓度写成 \(c_{\mathrm{sol}}^{\mathrm{Na}}\)；
- 同一稿件不得混用 \(X_{w,s}^{\mathrm{eq}}\) 与 \(X_{g,s}^{w,\mathrm{eq}}\) 这两套结构。

## 4. 字体与 LaTeX 写法

### 4.1 斜体与正体

- 物理变量和可变索引用数学斜体：\(p,T,t,i,j\)。
- 描述性文字下标/上标用 \(\mathrm{}\)：\(\mathrm{evap}\)、\(\mathrm{eq}\)、\(\mathrm{sat}\)、\(\mathrm{amb}\)、\(\mathrm{mol}\)、\(\mathrm{diff}\)、\(\mathrm{sol}\)、\(\mathrm{vol}\)。
- 化学式用正体：\(\mathrm{NaCl}\)、\(\mathrm{Na}\)、\(\mathrm{H_2O}\)、\(\mathrm{N_2}\)。
- 不直接使用正文斜体单词充当说明性标签。

### 4.2 推荐示例

~~~latex
j_{\mathrm{evap}}
X_{g,s}^{w,\mathrm{eq}}
X_{g,\mathrm{amb}}^{w}
x_{g,s}^{w,\mathrm{eq}}
D_g^{w,\mathrm{N_2}}
p_{\mathrm{sat}}
p_{\mathrm{atm}}
c_{\mathrm{vol}}^{\mathrm{Na}}
c_{\mathrm{sol}}^{\mathrm{Na}}
n^{\mathrm{Na}}
\rho_{\mathrm{sol}}
A_{\mathrm{evap}}
~~~

### 4.3 不推荐示例

~~~latex
Y_{w,s}                 % 质量分数不使用 Y
X_{w,s}^{\mathrm{eq}}   % 组分错误地放在下标，且未标明气相
x_{w,s}^{\mathrm{eq}}   % 组分错误地放在下标，且未标明气相
D_{w,g}                 % 组分与相的层级颠倒
p_{sat}                 % sat 应为正体
c_{NaVolume}            % 化学组分和描述词未分层
X_{wSurfaceEquilibrium} % 信息应通过分层上下标表达
~~~

## 5. 常用物理量表

| 物理量 | 推荐符号 | 典型单位/属性 |
|---|---:|---|
| 蒸发质量通量 | \(j_{\mathrm{evap}}\) | kg m\(^{-2}\) s\(^{-1}\) |
| 气体密度 | \(\rho_g\) 或带条件的 \(\rho_{g,f}\) | kg m\(^{-3}\) |
| 摩尔密度 | \(\rho_{\mathrm{mol},g}\) | mol m\(^{-3}\) |
| 扩散系数 | \(D_g^{w,\mathrm{N_2}}\) | m\(^2\) s\(^{-1}\) |
| 边界层厚度 | \(\delta_g\) | m |
| 压力 | \(p\) | Pa |
| 温度 | \(T\) | K；若用摄氏温度需显式标单位 |
| 水活度 | \(a_w\) | 无量纲 |
| 毛细压力 | \(p_c\) | Pa |
| 液相饱和度 | \(S_w\) | 无量纲 |
| 体积 | \(V\) | m\(^3\) |
| 表面积 | \(A\) | m\(^2\) |
| 时间 | \(t\)、\(\Delta t\) | s |

单位必须与量的定义一致。例如，若 \(j_{\mathrm{evap}}\) 是质量通量，则由 \(\rho D\Delta X/\delta\) 得到 kg m\(^{-2}\) s\(^{-1}\)；若改用摩尔密度和摩尔分数，则得到的是摩尔通量，符号和文字定义必须同步改变。

## 6. 首次出现与一致性检查

每个新物理量首次出现时应完成以下四件事：

1. 给出符号；
2. 给出清楚的物理定义；
3. 给出单位或说明为无量纲；
4. 说明下标/上标的含义，尤其是组分、相和位置。

提交前至少执行以下检索：

~~~powershell
rg -n "Y_\{|Y_[A-Za-z]|mass fraction|mole fraction" main.tex
rg -n "chi_A|\\chi_A" main.tex
rg -n "_[{]?(sat|eq|amb|diff|mol)" main.tex
~~~

人工检查检索结果，确认：

- 所有质量分数均为大写 \(X\)；
- 所有摩尔分数均为小写 \(x\)；
- \(\chi_A\) 未重新出现在正文；
- 描述性上下标使用正体；
- 方程量纲、正文定义、图表标签和补充材料一致。

## 7. 本轮已落实的决定

- 从蒸发通量方程及其解释中移除 \(\chi_A\)。
- 质量分数统一用大写 \(X\)，摩尔分数统一用小写 \(x\)。
- 按 QSPNM 论文将组分放上标、相和位置放下标：\(X_{g,s}^{w,\mathrm{eq}}\)、\(X_{g,\mathrm{amb}}^{w}\)、\(x_{g,s}^{w,\mathrm{eq}}\)。
- 水蒸气--氮气二元扩散系数写成 \(D_g^{w,\mathrm{N_2}}\)。
- Na 相关物质的量和浓度写成 \(n^{\mathrm{Na}}\)、\(c_{\mathrm{vol}}^{\mathrm{Na}}\) 和 \(c_{\mathrm{sol}}^{\mathrm{Na}}\)。

