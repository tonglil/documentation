---
title: 監視範囲
kind: ガイド
---
## 概要

特定の値が特定のしきい値を上回ったり下回ったりしたときにモニターがアラートをサポートしている場合、特定の値が範囲内または範囲外であるかどうかを通知することができます。

## 例
### メトリクス

メトリクス `a` は、ステータスを表す `0` から `10` までの離散値を報告し、メトリクスが `4` と `8` の間にない場合に通知が必要です。
数学的には、メトリクスと範囲の中心 (6) の差が 2 を超えてはなりません。

```
8 > a > 4 <=> abs(6-a) < 2 <=> abs(6-a) - 2 < 0
```

- 値が範囲外にある場合に通知を受けるには、モニター条件は `abs(6-a) - 2 > 0` である必要があります。
- 値が範囲内にある場合に通知を受けるには、モニター条件は `2 - abs(6-a) > 0` である必要があります。

{{< img src="monitors/faq/monitor_range.png" alt="範囲のメトリクスモニター"  >}}

### 理論

範囲は `x > a > y` で定義され、`a` が問題のメトリクスです。

- 値が範囲内にある場合に通知を受けるには、モニター条件は `abs((x-y/2) - a) - (x-y)/2 > 0` である必要があります。
- 値が範囲外にある場合に通知を受けるには、モニター条件は `(x-y)/2 - abs((x-y/2) - a) > 0` である必要があります。

## トラブルシューティング

ご不明な点は、[Datadog のサポートチーム][1]までお問合せください。

[1]: /ja/help/