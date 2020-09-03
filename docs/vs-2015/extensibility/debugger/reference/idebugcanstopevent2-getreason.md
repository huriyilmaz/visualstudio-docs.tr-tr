---
title: 'IDebugCanStopEvent2:: GetReason | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191145"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama altyapısının (DE) durdurulması nedenini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pcr`  
 dışı Bu olayın nedenini açıklayan [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) numaralandırmasından bir değer döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem genellikle [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) yönteminden önce çağrılır, böylece çağıranın sıfır olmayan () yönteme geçirilip geçemeyeceğini belirleyebilmesini sağlayabilirsiniz `TRUE` `IDebugCanStopEvent2::CanStop` .  
  
 Durdurma nedeni, ya da bir `CANSTOP_ENTRYPOINT` giriş noktasına eriştiği anlamına gelir, yanı `CANSTOP_STEPIN` de bir işlev olarak da çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
