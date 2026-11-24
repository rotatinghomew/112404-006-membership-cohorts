# 美术馆会员续费观察与权益成本分层

本项目保存视觉艺术机构日常业务分析使用的合成演练资料，样例不代表真实机构、作品、交易或研究结论。

## 资料

- `memberships.csv`：会籍及家庭关系样例。字段为 `member_id, household_id, tier, valid_from, valid_to, renewal_state, joined_at`。
- `benefit_rules.csv`：不同期限的权益定义和服务容量。字段为 `rule_id, tier, benefit, valid_from, valid_to, unit_cost, capacity_limit, sharing`。
- `benefit_events.csv`：预约、核销、候补和退款事实。字段为 `event_id, member_id, benefit, event_date, event_type, quantity, venue`。
- `renewal_history.csv`：往期续费、降级和退出记录。字段为 `member_id, period_end, outcome, offer_id, offer_state, source`。

记录之间通过 `*_id`、`*_key` 或 `*_ref` 字段关联。日期采用 ISO 格式；空值表示来源未提供该事实，不代表数值为零。不同来源的统计范围和状态以 `docs/data-contract.md` 为准。样例中保留了待确认、取消、缺失和版本变化等原始情况，不包含预先计算的分析结论。

## 运行

需要 Python 3.11 或更高版本，无第三方依赖。运行 `python3 -m unittest discover -s tests -v` 可检查资料编码、字段和记录结构。
