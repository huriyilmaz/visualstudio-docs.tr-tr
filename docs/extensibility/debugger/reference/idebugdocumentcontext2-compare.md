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
ms.openlocfilehash: fa10a5dbaf141def906705dfb84dfa2b95f216e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089257"
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
