---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4e8c1b438cd2fa2721e81f055695e5836c26d12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179946"
---
# <a name="context_info"></a>CONTEXT_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yapı bir bellek bağlamını veya kod bağlamını açıklar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Üyeler  
 dwFields  
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Numaralandırmadaki, doldurulacak alanları belirten bayrakların bir birleşimi<strong>.</strong>  
  
 bstrModuleUrl 'Si  
 Bağlamın bulunduğu modülün adı.  
  
 bstrFunction Işlevi  
 Bağlamın bulunduğu işlevin adı.  
  
 Posfunctionkayması  
 Kod bağlamı ile ilişkili işlevin satır ve sütun sapmasını tanımlayan [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı.  
  
 bstrAddress  
 Verilen bağlamın bulunduğu koddaki adres.  
  
 bstrAddressOffset  
 Verilen bağlamın bulunduğu koddaki adresin konumu.  
  
 bstrAddressAbsolute  
 Belirtilen bağlamın bulunduğu bellekteki mutlak adres.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) yöntemine yapılan çağrıdan döndürülür.  
  
 Bu yapının tipik kullanımı, **bellek** hata ayıklama penceresi desteğidir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
