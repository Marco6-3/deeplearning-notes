# 2026-02-28 调参记录

## 📝 实验背景
- **前次结果**：`train_acc=0.85` / `valid_acc=0.54`
- **主要问题**：严重过拟合（Overfitting）

## 🛠️ 本次改动
1. **模型架构**：修改全连接层（Fully Connected）为 `256 -> 256 -> 11`。
2. **正则化**：
   - Dropout 率调至 `0.3`。
   - 引入权重衰减 `weight_decay = 1e-5`。
3. **学习率策略**：
   - 引入 **Cosine Annealing Scheduler**（余弦退火）。
   - 周期：`60 epochs`。
   - 最低学习率 (eta_min)：`1e-6`。

---
> **预期目标**：通过降低模型复杂度、增加随机性和动态调整学习率，压低训练集准确率，提升验证集准确率。

 <img width="1189" height="390" alt="下载" src="https://github.com/user-attachments/assets/e41aa13a-59d2-4686-b08f-8d0f12d43dc4" />

 `private score=0.60968`
 
` public score=0.62066`
