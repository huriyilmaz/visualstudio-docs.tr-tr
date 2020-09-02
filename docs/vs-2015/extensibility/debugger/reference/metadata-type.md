---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546830"
---
# <a name="metadata_type"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yapı, meta verilerden alınan bir alan türü hakkında bilgi belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 Ulappdomainıd  
 Simgenin geldiği uygulamanın KIMLIĞI. Bu, uygulamanın bir örneğini benzersiz bir şekilde tanımlamak için kullanılır.  
  
 guidModule  
 Bu alanı içeren modülün GUID 'ı.  
  
 tokClass  
 Bu türün meta veri belirteci KIMLIĞI.  
  
 [C++] `_mdToken` , `typedef` 32 bitlik bir içindir `int` .  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) `dwKind` `TYPE_INFO` yapı alanı `TYPE_KIND_METADATA` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından bir değer) olarak ayarlandığında TYPE_INFO yapısındaki birleşimin bir parçası olarak görüntülenir.  
  
 `tokClass`Değer, bir türü benzersiz bir şekilde tanımlayan bir meta veri belirtecidir. Meta veri belirteci KIMLIĞININ üst bitlerini yorumlama hakkında daha fazla bilgi için `CorTokenType` SDK 'daki CorHdr. h dosyasındaki sabit listesine bakın [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
