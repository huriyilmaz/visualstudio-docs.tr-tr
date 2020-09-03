---
title: 'IDebugDocumentContext2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0e46f765c8e4c0e12c3bb9447e0713919fae7b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731888"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Bu belge bağlamını, belirli bir belge bağlamı dizisiyle karşılaştırır.

## <a name="syntax"></a>Söz dizimi

```cpp
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

## <a name="parameters"></a>Parametreler
`compare`\
'ndaki [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) numaralandırmasından karşılaştırma türünü belirten bir değer.

`rgpDocContextSet`\
'ndaki Karşılaştırılan belge bağlamlarını temsil eden bir [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesneleri dizisi.

`dwDocContextSetLen`\
'ndaki Karşılaştırılacak belge bağlamlarının dizisi uzunluğu.

`pdwDocContext`\
dışı `rgpDocContextSet` Karşılaştırmayı karşılayan ilk belge bağlamının dizisine dizini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 `S_OK`Bir eşleşme bulunursa döndürür. `S_FALSE`Eşleşme bulunmazsa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dizide geçirilen [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnelerinin, üzerinde çağrılan nesneyi uygulayan aynı hata ayıklama altyapısı tarafından uygulanması gerekir `IDebugDocumentContext2` ; Aksi takdirde, karşılaştırma geçerli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
