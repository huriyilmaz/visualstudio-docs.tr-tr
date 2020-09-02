---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9cf283cf7239b5ed74e38ca534538a286a477c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179964"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

İki bellek bağlamlarını karşılaştırma ölçütlerini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```csharp  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## <a name="members"></a>Üyeler  
 CONTEXT_EQUAL  
 Listedeki hedef bellek bağlamına eşit olan ilk bellek bağlamını bulun.  
  
 CONTEXT_LESS_THAN  
 Listede hedef bellek bağlamından daha az olan ilk bellek bağlamını bulun.  
  
 CONTEXT_GREATER_THAN  
 Listede hedef bellek bağlamından daha büyük olan ilk bellek bağlamını bulun.  
  
 CONTEXT_LESS_THAN_OR_EQUAL  
 Listede, hedef bellek bağlamından daha küçük veya ona eşit olan ilk bellek bağlamını bulun.  
  
 CONTEXT_GREATER_THAN_OR_EQUAL  
 Listede, hedef bellek bağlamından daha büyük veya ona eşit olan ilk bellek bağlamını bulun.  
  
 CONTEXT_SAME_SCOPE  
 Hedef bellek bağlamıyla aynı kapsamdaki listede bulunan ilk bellek bağlamını bulun.  
  
 CONTEXT_SAME_FUNCTION  
 Hedef bellek kapsamıyla aynı işlevde bulunan listedeki ilk bellek bağlamını bulun.  
  
 CONTEXT_SAME_MODULE  
 Listede, hedef bellek içeriğiyle aynı modülde olan ilk bellek bağlamını bulun.  
  
 CONTEXT_SAME_PROCESS  
 Listede, hedef bellek içeriğiyle aynı işlemde olan ilk bellek bağlamını bulun.  
  
## <a name="remarks"></a>Açıklamalar  
 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) metoduna bir bağımsız değişken olarak geçirilir.  
  
 Bu değerler, belirtilen karşılaştırma ölçütlerini karşılayan bir listedeki ilk bellek bağlamını bulmak için kullanılır. Bellek bağlamına, yöntemi aracılığıyla kendisini karşılaştırmak için bellek bağlamlarının bir listesi verilir `IDebugMemoryContext2::Compare` . Karşılaştırma işlecinin daha sonra döndürüldüğü listedeki ilk bellek bağlamı `true` döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Karşılaştır](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
