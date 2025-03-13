# Flink检查点机制10问10答  

### Q1：检查点（Checkpoint）和保存点（Savepoint）有什么区别？  
**答案**：  
- **检查点**：定期自动触发，用于故障恢复，**轻量级**，生成后自动删除旧数据。  
- **保存点**：手动触发，用于版本升级/作业暂停，**持久化存储**，需指定路径保存。  

**面试技巧**：  
- 如果面试官问区别，反问：“贵司的实时任务一般多久做一次Savepoint？”（展示业务思维）  

---  

### Q2：如何配置Flink检查点间隔？  
**答案**：  
在`flink-conf.yaml`中设置：  
```yaml  
execution.checkpointing.interval: 60000  # 单位毫秒  
execution.checkpointing.mode: EXACTLY_ONCE  
