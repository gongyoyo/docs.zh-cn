---
title: 如何：解决不明确的时间
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 0b5b28c588237fb2f7f069aaef06f3f73d5268bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122252"
---
# <a name="how-to-resolve-ambiguous-times"></a>如何：解决不明确的时间

不明确时间是指映射到多个协调世界时 (UTC) 的时间。 在向后调整时钟时间时，例如从时区的夏令时调整到标准时间这段转换期间，便会出现不明确时间。 在处理不明确时间时，可执行以下任一操作：

- 假设一下时间如何映射到 UTC。 例如，可以假定不明确时间始终以时区的标准时间表示。

- 如果不明确时间是用户输入的数据项，则可以让用户自行解决。

本主题演示如何通过假定不明确时间表示时区的标准时间来解决它。

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>将不明确时间映射到时区的标准时间

1. 调用 <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> 方法来确定时间是否不明确。

2. 如果时间不明确，请从时区的 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 属性返回的 <xref:System.TimeSpan> 对象中减去时间。

3. 调用 `static` （Visual Basic .NET 中的`Shared`） <xref:System.DateTime.SpecifyKind%2A> 方法，将 UTC 日期和时间值的 <xref:System.DateTime.Kind%2A> 属性设置为 <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>。

## <a name="example"></a>示例

下面的示例演示了如何通过假设表示本地时区的标准时间，将不明确的时间转换为 UTC。

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

该示例包含一个名为 `ResolveAmbiguousTime` 的方法，该方法确定传递给它的 <xref:System.DateTime> 值是否不明确。 如果值不明确，则该方法将返回一个表示相应 UTC 时间的 <xref:System.DateTime> 值。 方法通过从本地时间减去本地时区的 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 属性的值来处理此转换。

通常，通过调用 <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> 方法来检索包含不明确时间的可能 UTC 偏移量的 <xref:System.TimeSpan> 对象的数组，处理不明确时间。 但是，本示例建立在一个大胆假设之上，即不明确时间始终映射到时区的标准时间。 <xref:System.TimeZoneInfo.BaseUtcOffset%2A> 属性返回 UTC 与时区的标准时间之间的偏移量。

在此示例中，对本地时区的所有引用都是通过 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 属性进行的;本地时区从不分配给对象变量。 这是建议的做法，因为调用 <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> 方法会使本地时区分配到的任何对象无效。

## <a name="compiling-the-code"></a>编译代码

此示例需要：

- 将 <xref:System> 命名空间与 `using` 语句一起导入（在代码C#中是必需的）。

## <a name="see-also"></a>请参阅

- [日期、时间和时区](../../../docs/standard/datetime/index.md)
- [如何：让用户解析不明确时间](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
