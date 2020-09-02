---
title: .NET Framework için paralel uzantı Iç Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42c472190469e7d008fa8c525f50eabfaf37053f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65680933"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework için Paralel Uzantı Dahili Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu bölüm, .NET Framework paralel uzantıları için özel bir hata ayıklayıcı uygulamanıza yardımcı olan sınıfların iç türlerini, yöntemlerini ve alanlarını açıklamaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Task Sınıfı](../../extensibility/debugger/task-class-internal-members.md)  
 Sınıfının iç veri üyelerini açıklar <xref:System.Threading.Tasks.Task?displayProperty=fullName> .  
  
 [TaskScheduler Sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Sınıfının iç veri üyelerini açıklar <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> .  
  
 [ContingentProperties Sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Sınıfının iç veri üyelerini açıklar `System.Threading.Tasks.ContingentProperties` .  
  
 [AsyncTaskMethodBuilder Yapısı](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Yapının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> .  
  
 [AsyncTaskMethodBuilder\<TResult> Yapısı](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Yapının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> .  
  
 [AsyncVoidMethodBuilder Yapısı](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Yapının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio hata ayıklayıcı genişletilebilirliği](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Paralel programlama](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
