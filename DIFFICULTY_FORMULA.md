# 题目难度重算公式说明

## 公式设计思路

根据两个AI（step-3.5-flash 和 kimi-k2.5）的实际表现来重新评估题目难度：

- **AI得分高** → 题目相对容易 → 难度应该降低
- **AI得分低** → 题目相对困难 → 难度应该提高
- **原始难度** → 作为参考基准，保留一定权重

## 可用公式

### 公式1：简单加权平均（Simple Weighted）

```
new_difficulty = 0.3 × original_difficulty + 0.7 × (10 - avg_ai_score)
```

**特点**：
- 简单直接，易于理解
- 70%权重给AI表现，30%给原始难度
- 适合AI表现比较一致的情况

**适用场景**：两个AI得分接近时

---

### 公式2：最差最好加权（Min-Max Weighted）

```
new_difficulty = 0.2 × original + 0.5 × (10 - min_score) + 0.3 × (10 - max_score)
```

**特点**：
- 同时考虑最差和最好AI的表现
- 更偏向最差AI（50%权重）
- 如果最差的AI都答得好，题目确实容易

**适用场景**：想更保守地评估难度

---

### 公式3：自适应调整（Adaptive，**推荐**）

```
weighted_avg = 0.6 × min_score + 0.4 × max_score
new_difficulty = 0.3 × original + 0.7 × (10 - weighted_avg)
```

**特点**：
- 更偏向较低的AI得分（60%权重）
- 如果两个AI都高分，题目容易；都低分，题目难
- 平衡了保守性和准确性

**适用场景**：通用场景，推荐使用

---

### 公式4：基于共识（Consensus-Based）

```
avg_score = (flash_score + kimi_score) / 2
score_diff = |flash_score - kimi_score|
variance_penalty = score_diff × 0.5
new_difficulty = 0.25 × original + 0.5 × (10 - avg_score) + 0.25 × variance_penalty
```

**特点**：
- 考虑两个AI得分的差异
- 如果差异大，可能题目有歧义，适当提高难度
- 更细致地反映题目特性

**适用场景**：想识别可能有歧义的题目

---

### 公式5：悲观估计（Pessimistic）

```
new_difficulty = 0.2 × original + 0.8 × (10 - min_score)
```

**特点**：
- 完全由最差的AI表现决定（80%权重）
- 最保守的评估方式
- 如果最差的AI都答得好，题目才容易

**适用场景**：想设置较高的难度门槛

---

## 使用示例

### 查看公式对比

```bash
cd /data/swe-agents
python3 scripts/recalculate_difficulty.py
```

### 使用指定公式重新计算难度

```bash
# 使用公式3（推荐）
python3 scripts/recalculate_difficulty.py formula_3

# 使用公式1
python3 scripts/recalculate_difficulty.py formula_1

# 使用公式5（最保守）
python3 scripts/recalculate_difficulty.py formula_5
```

### 输出文件

结果会保存到：`ruozhiba_scores_step-3.5-flash_recalculated.json`

新文件会包含：
- `original_difficulty_score`: 原始难度
- `difficulty_score`: 重新计算后的难度

---

## 公式选择建议

根据你的需求选择：

1. **想要平衡的评估** → 使用 **公式3（自适应）**
2. **想要保守的评估** → 使用 **公式5（悲观估计）**
3. **想识别歧义题目** → 使用 **公式4（基于共识）**
4. **想要简单直接** → 使用 **公式1（简单加权）**

---

## 公式效果分析

从实际数据看：
- 两个AI平均分都很高（flash: 8.62, kimi: 8.83）
- 大部分题目原始难度在5-6分
- 重新计算后，难度普遍会降低2-4分

这说明：
- 原始难度评估可能偏高
- 两个AI都能很好地回答这些题目
- 重新计算后的难度更符合AI的实际表现

---

## 自定义公式

如果需要调整公式参数，可以修改 `scripts/recalculate_difficulty.py` 中的函数。

例如，如果想更偏向原始难度，可以调整权重：

```python
# 在 formula_3_adaptive 中
alpha = 0.5  # 增加到0.5，更偏向原始难度
```
