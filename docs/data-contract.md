# 合成资料约定

资料用于本地业务流程演练，字段仅记录事实来源，不预先裁定业务结果。

- `memberships.csv`：会籍及家庭关系样例。字段为 `member_id, household_id, tier, valid_from, valid_to, renewal_state, joined_at`。
- `benefit_rules.csv`：不同期限的权益定义和服务容量。字段为 `rule_id, tier, benefit, valid_from, valid_to, unit_cost, capacity_limit, sharing`。
- `benefit_events.csv`：预约、核销、候补和退款事实。字段为 `event_id, member_id, benefit, event_date, event_type, quantity, venue`。
- `renewal_history.csv`：往期续费、降级和退出记录。字段为 `member_id, household_id, period_end, outcome, offer_id, offer_state, source`。

空字段表示事实尚未提供，`pending`、`review`、`hold` 等状态表示来源记录尚未形成最终确认。不同来源以事件日期或有效期表达的时间含义不相同，调用方应结合表名和字段解释；不能仅因编号相同就假定两条记录可合并。金额以资料中记载的名义单位表示，没有统一换算或预先扣除退款。
