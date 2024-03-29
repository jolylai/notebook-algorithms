---
title: 哈希表
order: 50
---

`哈希表(hash table 或hash map)` 是一种实现 关联数组(associative array) 的抽象数据；类型, 该结构可以将 键映射到值。

哈希表使用 哈希函数/散列函数 来计算一个值在数组或桶(buckets)中或槽(slots)中对应的索引,可使用该索引找到所需的值。

理想情况下,散列函数将为每个键分配给一个唯一的桶(bucket),但是大多数哈希表设计采用不完美的散列函数,这可能会导致"哈希冲突(hash collisions)",也就是散列函数为多个键(key)生成了相同的索引,这种碰撞必须以某种方式进行处理。

![](https://cy-picgo.oss-cn-hangzhou.aliyuncs.com/hash-table.svg)

## 哈希值

```js
/**
 * Converts key string to hash number.
 *
 * @param {string} key
 * @return {number}
 */
function hash(key) {
  const hash = Array.from(key).reduce(
    (hashAccumulator, keySymbol) => hashAccumulator + keySymbol.charCodeAt(0),
    0,
  );

  // Reduce hash number so it would fit hash table size.
  return hash % this.buckets.length;
}
```
