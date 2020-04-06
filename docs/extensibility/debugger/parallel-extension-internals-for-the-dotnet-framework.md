---
title: .NET Framework için Paralel Uzantı İçI | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738266"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework için paralel uzantı dahili
Bu bölümde, .NET Framework'e paralel uzantılar için özel bir hata ayıklama uygulamanıza yardımcı olan iç sınıf türleri, yöntemleri ve alanları açıklanmaktadır.

## <a name="in-this-section"></a>Bu bölümde
 [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md) <xref:System.Threading.Tasks.Task?displayProperty=fullName> Sınıfın iç veri üyelerini açıklar.

 [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md) <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> Sınıfın iç veri üyelerini açıklar.

 [ContingentProperties sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md) `System.Threading.Tasks.ContingentProperties` Sınıfın iç veri üyelerini açıklar.

 [AsyncTaskMethodBuilder yapısı](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Yapının <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> iç üyelerini açıklar.

 [AsyncTaskMethodBuilder\<TResult>](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> yapısı Yapının iç üyelerini açıklar.

 [AsyncVoidMethodBuilder yapısı](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Yapının <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> iç üyelerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio hata ayıklama genişletilebilirlik](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Paralel programlama](/dotnet/standard/parallel-programming/index)
