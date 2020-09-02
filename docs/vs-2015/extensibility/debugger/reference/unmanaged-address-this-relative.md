---
title: UNMANAGED_ADDRESS_THIS_RELATIVE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE
helpviewer_keywords:
- UNMANAGED_ADDRESS_THIS_RELATIVE structure
ms.assetid: e6a91ace-2d47-4ff9-aefb-8d8b68eab0b2
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aaed99b669946f4d2885009ff328ce4e2e62fcae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204754"
---
# <a name="unmanaged_address_this_relative"></a>UNMANAGED_ADDRESS_THIS_RELATIVE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yapı, bir `this` işaretçiye (Visual Basic) göre bir adresi temsil eder `Me` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagUNMANAGED_THIS_RELATIVE {  
   DWORD dwOffset;  
   DWORD dwBitOffset;  
   DWORD dwBitLength;  
} UNMANAGED_ADDRESS_THIS_RELATIVE;  
```  
  
```csharp  
public struct UNMANAGED_THIS_RELATIVE {  
   public uint dwOffset;  
   public uint dwBitOffset;  
   public uint dwBitLength;  
}  
```  
  
## <a name="terms"></a>Terimler  
 Dwsapmayı  
 Taban konumundan bayt konumu (örneğin, bir sınıf vtable 'u başlangıcı).  
  
 dwBitOffset  
 Taban konumundan bit cinsinden konum (bir bit alanına başvurmadığı takdirde daima 0).  
  
 Dwbituzunluğu  
 Adresi temsil eden bit sayısı (bir bit alanına başvurmadığı müddetçe daima 0).  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapı, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) `dwKind` `DEBUG_ADDRESS_UNION` yapı alanı `ADDRESS_KIND_UNMANAGED_THIS_RELATIVE` ( [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) numaralandırmasından bir değer) olarak ayarlandığında DEBUG_ADDRESS_UNION yapısındaki birleşimin bir parçasıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: SH. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar ve birleşimler](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
