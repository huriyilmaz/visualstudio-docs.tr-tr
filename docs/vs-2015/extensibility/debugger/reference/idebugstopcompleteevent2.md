---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546929"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE), bir program durdurulduğunda bu isteğe bağlı olayı oturum hata ayıklama Yöneticisi 'ne (SDM) gönderebilir.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu yeni bir arabirimdir [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Önceki yayınlar zaman uyumsuz durdurmayı desteklemiyor.  
  
 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) , çok işlem veya çok program senaryolarında SDM tarafından çağırılır. Bir program SDM 'ye durdurma olayı gönderdiğinde, SDM diğer programları da durdurur.  
  
 Bir programın durdurduğu SDM 'yi zaman uyumsuz olarak bildirmek için kullanılır. Bu, bir yorumlayıcı hata ayıklama altyapısı için yararlıdır; burada bazen hata ayıklanan programın içinde hiçbir kod çalışmıyorsa, [durdurma](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) zaman uyumlu olarak tamamlanamaz. Bir hata ayıklama altyapısı bu zaman uyumsuz bildirimi kullanmak isterse, `S_ASYNC_STOP` [stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)'tan dönmesi gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
