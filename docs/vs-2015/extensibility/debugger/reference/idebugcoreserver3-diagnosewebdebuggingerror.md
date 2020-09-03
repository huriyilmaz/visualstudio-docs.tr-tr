---
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24f142a631df25cfbff8ed795736c0cbf4e59eaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205273"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Otomatik iliştirme neden başarısız olduğunu saptamaya çalışır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszUrl`  
 'ndaki Şu anda kullanılmıyor; her zaman bir null değer olarak ayarlanmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Diğer tipik dönüş kodları aşağıda verilmiştir:  
  
|Kod|Açıklama|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Uzak sunucunun neden hata ayıklamaya başlayamadığını belirleyemiyor.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Büyük olasılıkla yetersiz izinler nedeniyle veya hata ayıklama fiili etkinleştirilmediğinden, uzak sunucuda hata ayıklama yapılamıyor.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web sunucusu kilitlenmiş ve hata ayıklamayı etkinleştirmek için gereken hata ayıklama fiilini engelliyor.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
