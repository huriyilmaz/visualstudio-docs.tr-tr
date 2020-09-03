---
title: .NET Framework için paralel uzantı Iç Işlevleri | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738266"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework için paralel uzantı iç işlevleri
Bu bölüm, .NET Framework paralel uzantıları için özel bir hata ayıklayıcı uygulamanıza yardımcı olan sınıfların iç türlerini, yöntemlerini ve alanlarını açıklamaktadır.

## <a name="in-this-section"></a>Bu bölümde
 [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md) Sınıfının iç veri üyelerini açıklar <xref:System.Threading.Tasks.Task?displayProperty=fullName> .

 [TaskScheduler sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md) Sınıfının iç veri üyelerini açıklar <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> .

 [Kıgentproperties sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md) Sınıfının iç veri üyelerini açıklar `System.Threading.Tasks.ContingentProperties` .

 [AsyncTaskMethodBuilder yapısı](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Yapının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> .

 [AsyncTaskMethodBuilder \<TResult> yapısı](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) , yapının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> .

 [AsyncVoidMethodBuilder yapısı](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Yapının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> .

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Paralel programlama](/dotnet/standard/parallel-programming/index)
