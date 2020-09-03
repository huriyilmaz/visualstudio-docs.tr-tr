---
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 476ffb2901dfe6a8d09ca707fc47089f4d99d97d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162493"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu modülle ilgili bilgileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFields`  
 'ndaki [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların birleşimi `pInfo` .  
  
 `pInfo`  
 [in, out] Modülün açıklamasıyla doldurulmuş [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) yapısı, **modüller** penceresinde görüntülenen modülün adını içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
