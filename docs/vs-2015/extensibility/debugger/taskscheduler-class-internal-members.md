---
title: TaskScheduler sınıfı-Iç Üyeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427a84b3dcda0471f5ec9d71883a5a8e859bb92d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176695"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler Sınıfı - Dahili Üyeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu konu, <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> özel bir hata ayıklayıcı uygulamanıza yardımcı olan sınıfın iç üyelerini açıklar. Bu sınıf hakkında genel bilgi için <xref:System.Threading.Tasks.TaskScheduler> başvuru konusuna bakın.  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Üyeler  
  
### <a name="methods"></a>Yöntemler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Tüm zamanlanmış görevlerin bir dizisini alır.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Şu anda etkin olan tüm nesnelerin bir dizisini alır <xref:System.Threading.Tasks.TaskScheduler> .|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [.NET Framework için Paralel Uzantı Dahili Bileşenleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
