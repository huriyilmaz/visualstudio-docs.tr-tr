---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831173"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bir sunucu için makine yardımcı programlarını alır.  
  
> [!NOTE]
> Bu yöntem artık kullanılmıyor: kullanmayın ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] `E_NOTIMPL` Bu yöntem çağrılırsa her zaman döner). Bu, geçmiş nedenlerle tutulur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppUtil`  
 dışı `IDebugMDMUtil2_V7` Makine yardımcı programları bilgilerini temsil eden bir arabirim döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Her zaman `E_NOTIMPL` , yöntemin uygulanmadığını belirten ' i döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]`E_NOTIMPL`Bu yöntem çağrılırsa her zaman döndürülür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
