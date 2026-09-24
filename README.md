# OAE 实践成果（框架仓）

陨石合作社 · 组织化智能体生态（OAE）实践团队

## 简介

本仓收录组织化智能体生态（OAE）的**合成样例数据**，用于说明治理骨架中「派单—验收」层的数据形态与字段同构关系。

配套论文见 [论文仓](https://github.com/yyrps247/oae-paper)（CC BY 4.0）。

## synthetic/ 合成样例库

原则一句话：**分布真实、内容虚构**。

- **计数分布真实**：来自生产派工库的**只读纯计数导出**（440 单，导出时刻 2026-09-21T20:28:52+08:00，零内容字段），按样例单上限 200 做比例缩放（最大余数法，非零桶保底 1；口径见 `corpus/distribution.json` 的 `meta.scaling`）。
- **内容字段全为虚构**：种子化伪随机生成（`seed=42`）——任务文本取自固定模板、角色为 `DECIDE`/`EXEC`/`VERIFY` 等代号、编号为 `order-NNNN` 与 `chain-NNNN` 占位、时间戳由种子决定。与生产库任何真实工单**无一一对应关系**，亦不可反推出任何真实个体表现。
- **单号说明**：真实单号形态受脱敏闸拦截（对外件要求 0 命中），故以 `order-NNNN` 占位表达「字段同构」；派发方缩写为匿名样例（分布对齐、映射不公开）。

### 文件

| 文件 | 说明 |
|---|---|
| `synthetic/corpus/manifest.json` | 清单与各件 sha256，可用于完整性核对 |
| `synthetic/corpus/distribution.json` | 真实分布计数与缩放口径（`meta` 段说明导出与缩放方法） |
| `synthetic/corpus/data/orders.jsonl` | 派单样例（每行一单） |
| `synthetic/corpus/data/chains.jsonl` | 链样例 |
| `synthetic/corpus/registry_sample.md` | 注册表样例 |
| `synthetic/corpus/DECLARATION.md` | 「分布真实、内容虚构」声明全文 |

### 核对方式

```
# 按 manifest.json 逐件核对 sha256
sha256sum synthetic/corpus/DECLARATION.md synthetic/corpus/data/*.jsonl ...
```

## 关于生成器与校验脚本

`generate_synthetic.py`（复现，同种子同输出）与 `verify_synthetic.py`（自证分布一致且内容无一生于真库）属工具脚本，需经脱敏闸复核后另行发布，**当前不随本仓发布**。样例数据本身的完整性可由 `manifest.json` 的 sha256 独立核对，不依赖脚本。

## 许可

- 本仓代码与数据采用 [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) 许可。
- 论文与文档见论文仓，采用 CC BY 4.0。

## 引用格式

```
陨石合作社. 组织化智能体生态 (OAE) 实践团队. 2026.
```

## 权利保留

- 本仓以 Apache-2.0 发布；作者保留另仓闭源商业版的权利。
- 本作品按「现状」提供，不提供任何明示或默示的保证。

## 贡献

- 本仓暂不接收外部贡献。
- 若后续引入，须签署 Developer Certificate of Origin (DCO)，提交含 `Signed-off-by` 行。

## 勘误

勘误只在仓库修订并打新 tag（如 v1.0 → v1.0.1），**不在任何平台回改已发布文本**。引用时请锁定具体 tag。
