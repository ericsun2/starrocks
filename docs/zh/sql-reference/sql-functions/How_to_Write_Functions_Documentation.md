# CONVERT_TZ

> - *本文以 `CONVERT_TZ` 函数为例，说明函数文档的写作要求。*
> - *确保函数名称、语法、示例准确，是否有别名，是否补充了必要的注意事项和报错可能。*

## 功能

将给定的时间转化为另一个时区的时间。

> - *简要描述函数功能。*
> - *对于有业务场景的函数，需明确业务场景、比如，retention() 函数常用于计算一段时间内的用户留存情况。*
> - *如果有使用规则或注意事项，需要说明。*
> - *函数是否有能力边界，比如仅支持传入 xxx 个参数。*

## 语法

```Haskell
CONVERT_TZ(dt, from_tz, to_tz)
```

> *函数的语法结构，使用代码块包裹。检查语法的正确性，语法是否与代码实现一致。哪些参数是可选参数，使用 [] 包裹。*

## 参数说明

- `dt`：需要转化的时间。支持的数据类型为 DATETIME。
- `from_tz`：源时区名称。支持的数据类型为 VARCHAR。时区可以使用两种格式：时区信息数据库（Time Zone Database，比如 Asia/Shanghai），或 UTC 偏移量（例如+08: 00）。
- `to_tz`：目标时区名称。支持的数据类型为 VARCHAR。格式同 `from_tz`。

> - *参数说的格式为 `参数：含义+数据类型`（请列出所支持的全部数据类型）。*
> - *参数含义包括：参数解释、是否必选、取值类型、取值格式（if any）、取值范围（if any）、不同取值的含义、是否有单位、不同数据类型下的取值和单位差异等。*
> - *数据类型需要字母全大写，比如 DATETIME。*

## 返回值说明

返回 DATETIME 类型的值。

返回值的数据类型为 DATETIME。

> - *不同的入参类型对应的输出类型，返回值的含义。*
> - *各类可能的错误：输入值不满足数据类型要求时/null/空/超限时，返回的结果，比如返回 NULL，空，报错。*

## 注意事项 （可选）

各时区对应的时区信息数据库，请参见[时区数据库](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)（来源：维基百科）。

> *使用该函数时的注意事项或者限制，如果影响用户使用，必须说明。*

## 示例

示例一：将上海时间转化为洛杉矶时间。

```Plaintext
MySQL > select convert_tz('2019-08-01 13:21:03', 'Asia/Shanghai', 'America/Los_Angeles');
+---------------------------------------------------------------------------+
| convert_tz('2019-08-01 13:21:03', 'Asia/Shanghai', 'America/Los_Angeles') |
+---------------------------------------------------------------------------+
| 2019-07-31 22:21:03                                                       |
+---------------------------------------------------------------------------+
```

示例二：将东八区时间转化为洛杉矶时间。

```Plaintext
MySQL > select convert_tz('2019-08-01 13:21:03', '+08:00', 'America/Los_Angeles');
+--------------------------------------------------------------------+
| convert_tz('2019-08-01 13:21:03', '+08:00', 'America/Los_Angeles') |
+--------------------------------------------------------------------+
| 2019-07-31 22:21:03                                                |
+--------------------------------------------------------------------+
```

> - *尽量提供比较全的使用示例。
> - *尽量说明每个示例的作用和目的，让用户快速了解该示例场景。
> - *示例代码正确，能跑通。
> - *复杂函数需要对示例结果进行解释，帮助用户快速理解。
> - *示例代码需要做适当换行，不应太长。