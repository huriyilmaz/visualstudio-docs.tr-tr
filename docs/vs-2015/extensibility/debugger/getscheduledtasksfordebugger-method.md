---
title: GetScheduledTasksForDebugger yöntemi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b4ac6fa753be7672f1e698bda231bd11217c10d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152727"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger Metodu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tüm zamanlanmış görevlerin bir dizisini alır.  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyeye .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Zamanlanan tüm görevlerin dizisi. Her görev yürütülüyor veya yürütmeyi bitirdi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem iş parçacığı açısından güvenli değildir ve aynı anda diğer örneklerle kullanılmamalıdır <xref:System.Threading.Tasks.TaskScheduler> . yalnızca hata ayıklayıcı diğer iş parçacıklarını askıya aldığında hata ayıklayıcıdan çağrılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TaskScheduler Sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
