---
title: TASK_STATE_FAULTED alanı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d659d31de221d7a08ee85bee6350ade5c5a95808
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176721"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED Alanı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İşlenmemiş bir özel durum nedeniyle görev tamamlandı.  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyeye .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## <a name="remarks"></a>Açıklamalar  
 [M_stateFlags](../../extensibility/debugger/m-stateflags-field.md) alan bu değeri içeriyorsa, <xref:System.Threading.Tasks.Task.Status%2A> özelliği döndürür <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Task Sınıfı](../../extensibility/debugger/task-class-internal-members.md)
