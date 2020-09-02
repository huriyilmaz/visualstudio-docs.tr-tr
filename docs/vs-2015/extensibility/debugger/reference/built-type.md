---
title: BUILT_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BUILT_TYPE
helpviewer_keywords:
- BUILT_TYPE structure
ms.assetid: cc02c32c-0f65-4210-ad25-a9b1899066e8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6becf886d361e203dca313a7aa1dfdf166aa4614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153172"
---
# <a name="built_type"></a>BUILT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yapı, meta verilerden alınan bir alan türü hakkında bilgi belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
typedef struct _tagTYPE_BUILT {  
   ULONG32      ulAppDomainID;  
   GUID         guidModule;  
   IDebugField* pUnderlyingField;  
} BUILT_TYPE;  
```  
  
```csharp  
public struct BUILT_TYPE {  
   public uint        ulAppDomainID;  
   public Guid        guidModule;  
   public IDebugField pUnderlyingField;  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 Ulappdomainıd  
 Simgenin geldiği uygulamanın KIMLIĞI. Bu, uygulamanın bir örneğini benzersiz bir şekilde tanımlamak için kullanılır.  
  
 guidModule  
 Bu alanı içeren modülün GUID 'ı.  
  
 pUnderlyingField  
 Bu yerleşik alanla ilişkili temel alanı tanımlayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) `dwKind` `TYPE_INFO` yapı alanı `TYPE_KIND_BUILT` ( [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) numaralandırmasından bir değer) olarak ayarlandığında TYPE_INFO yapısındaki birleşimin bir parçası olarak görüntülenir.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
