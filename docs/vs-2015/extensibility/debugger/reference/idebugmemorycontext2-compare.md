---
title: 'IDebugMemoryContext2:: Compare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3eb48c324b5a1a918ab864c5eb4c4ca39eae41ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163438"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

, Eşleşen ilk bağlamın bir dizinini döndürürken, belirtilen dizide bulunan her bir bağlamla bellek bağlamını karşılaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `compare`  
 'ndaki [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) numaralandırmasından karşılaştırma türünü belirleyen bir değer.  
  
 `rgpMemoryContextSet`  
 'ndaki Karşılaştırılacak [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) nesnelerine başvuru dizisi.  
  
 `dwMemoryContextSetLen`  
 'ndaki Dizideki bağlamların sayısı `rgpMemoryContextSet` .  
  
 `pdwMemoryContext`  
 dışı Karşılaştırmayı karşılayan ilk bellek bağlamının dizinini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_COMPARE_CANNOT_COMPARE`İki bağlamlar karşılaştırılamamışsa döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hata ayıklama altyapısının (de) tüm karşılaştırma türlerini desteklemesi gerekmez, ancak en az `CONTEXT_EQUAL` , ve ' ı desteklemesi gerekir `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
