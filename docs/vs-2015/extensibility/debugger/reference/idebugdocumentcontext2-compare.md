---
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f09684c5e9587c6e3bb631674e009d0b36f4fc5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189407"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu belge bağlamını, belirli bir belge bağlamı dizisiyle karşılaştırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `compare`  
 'ndaki [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) numaralandırmasından karşılaştırma türünü belirten bir değer.  
  
 `rgpDocContextSet`  
 'ndaki Karşılaştırılan belge bağlamlarını temsil eden bir [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesneleri dizisi.  
  
 `dwDocContextSetLen`  
 'ndaki Karşılaştırılacak belge bağlamlarının dizisi uzunluğu.  
  
 `pdwDocContext`  
 dışı `rgpDocContextSet` Karşılaştırmayı karşılayan ilk belge bağlamının dizisine dizini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `S_OK`Bir eşleşme bulunursa döndürür. `S_FALSE`Eşleşme bulunmazsa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizide geçirilen [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnelerinin, üzerinde çağrılan nesneyi uygulayan aynı hata ayıklama altyapısı tarafından uygulanması gerekir `IDebugDocumentContext2` ; Aksi takdirde, karşılaştırma geçerli değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
