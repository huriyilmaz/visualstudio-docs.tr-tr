---
title: GetTaskSchedulersForDebugger yöntemi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152724"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger Metodu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Şu anda etkin olan tüm nesnelerin bir dizisini alır <xref:System.Threading.Tasks.TaskScheduler> .  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyeye .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Threading.Tasks.TaskScheduler>Bu, şu anda etkin olan tüm nesneler dizisi <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem iş parçacığı açısından güvenli değildir ve diğer örnekleri ile aynı anda kullanılmamalıdır <xref:System.Threading.Tasks.TaskScheduler> . Yalnızca hata ayıklayıcı diğer tüm iş parçacıklarını askıya aldığında hata ayıklayıcı 'dan çağrılmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TaskScheduler Sınıfı](../../extensibility/debugger/taskscheduler-class-internal-members.md)
