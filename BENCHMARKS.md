# Lightning mode benchmark / 小闪电性能记录

These are historical revision 73 measurements, not a performance guarantee for every task or a fresh benchmark of revision 79.

以下为修订 73 的历史实测，不是所有任务的性能保证，也不是修订 79 的新一轮压测。

## Setup / 测试条件

- Device / 设备：Xiaomi 2509FPN0BC, the same phone for both approaches.
- Model / 模型：DeepSeek Flash, max reasoning; real provider requests.
- Work / 工作：four independent generated-data tasks—ledger deduplication and integer statistics, DAG scheduling, interval union and peak concurrency, and a data-quality audit.
- Comparison / 对照：one agent processes all four tasks in a single batch, versus four preassigned tasks scheduled at a maximum of three concurrent subagents. Both use the same underlying agent loop and restricted compute tools, with fresh contexts. The single-agent baseline does not carry an existing personal chat history. This measures the compute batch, not additional main-model planning or final synthesis.
- 计时范围：预先安排的计算批次；三并发组由测试管理器调度四份任务，不包含主模型额外的拆解、规划和最终汇总时间。
- Validation / 验收：output files were checked against independently computed answers. A model saying “done” was not sufficient.
- Repeats / 次数：two runs per approach. Only the tested DeepSeek route is covered; no cross-provider speed claim is made.

## Results / 结果

| Approach / 方案 | Run 1 / 第一次 | Run 2 / 第二次 | Median / 中位数 |
| --- | ---: | ---: | ---: |
| Single-agent batch / 单 Agent 批处理 | 33.455 s | 45.061 s | 39.258 s |
| Three concurrent subagents / 三子 Agent 并发 | 29.272 s | 29.712 s | 29.492 s |

Both single-agent batches and all eight subagent task outputs passed validation. The median reduction in these samples is about 24.9%. Network/provider latency, task dependencies, context size, and device conditions can change the result. This is not a test of simultaneous mouse/keyboard control, battery life, or sustained thermal performance.

两次单 Agent 整包、两次并发组的八项子任务产出均通过核验。这组样本的中位耗时减少约 24.9%。网络和供应商延迟、任务依赖、上下文长度、设备状态都会改变结果；它不是多套键鼠并行操控、续航或持续温升测试。

The maintainers retain the original revision 73 receipts and independent output checks. Private device paths, raw conversations, and credentials are not included in this documentation repository.

原始回执与独立产出核验保留在维护者的修订 73 测试档案中；本说明仓库不上传私人设备路径、原始对话或凭据。
