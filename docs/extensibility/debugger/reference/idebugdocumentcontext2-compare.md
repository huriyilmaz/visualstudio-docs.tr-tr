---
description: Bu belge bağlamını, belge bağlamlarının verilen bir dizisiyle karşılar.
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 320dd75e43f9c2fd9cfc7b81cba4e6f89407acf6e61d36edbc018f7c3e9e8278
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121292695"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Bu belge bağlamını, belge bağlamlarının verilen bir dizisiyle karşılar.

## <a name="syntax"></a>Sözdizimi

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
[in] Karşılaştırma türünü [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) bir değer.

`rgpDocContextSet`\
[in] Karşılaştırmakta olan belge bağlamlarını temsil eden bir [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesneleri dizisi.

`dwDocContextSetLen`\
[in] Karşılaştırıla belge bağlamları dizisinin uzunluğu.

`pdwDocContext`\
[out] Dizini, `rgpDocContextSet` karşılaştırmayı yerine getiren ilk belge bağlamı dizisine döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Bir `S_OK` eşleşme bulunursa döndürür. Eşleşme `S_FALSE` bulunamasa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dizide [geçirilen IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnelerinin çağrılan nesneyi uygulayan aynı hata ayıklama altyapısı tarafından uygulanması gerekir; aksi takdirde `IDebugDocumentContext2` karşılaştırma geçerli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
