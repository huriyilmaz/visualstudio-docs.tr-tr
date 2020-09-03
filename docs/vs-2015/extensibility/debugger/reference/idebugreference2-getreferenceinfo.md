---
title: 'IDebugReference2:: Getreferenceınfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77cccb562db79d9f6a53113bda0c4434e19c6813
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155823"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir başvuruyu açıklayan [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısını alır. Daha sonraki kullanımlar için ayrılmıştır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFields`  
 'ndaki [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısında doldurulacak alanları belirleme [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) numaralandırmasındaki bayrakların birleşimi.  
  
 `nRadix`  
 'ndaki Herhangi bir sayısal bilgiyi biçimlendirmede kullanılacak taban tabanı.  
  
 `dwTimeout`  
 'ndaki Bu yöntemden dönmeden önce beklenecek en uzun süre (milisaniye cinsinden). `INFINITE`Sonsuza kadar beklemek için kullanın.  
  
 `rgpArgs`  
 'ndaki [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) nesnelerinden oluşan bir dizi. Gelecekte kullanılmak üzere ayrılmıştır; null değere ayarlayın.  
  
 `dwArgCount`  
 'ndaki Dizideki başvuru bağımsız değişkenlerinin sayısı `rgpArgs` . Gelecekte kullanılmak üzere ayrılmıştır; 0 olarak ayarlayın.  
  
 `pReferenceInfo`  
 dışı Özelliğin açıklamasıyla doldurulmuş [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Her zaman `E_NOTIMPL` döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
