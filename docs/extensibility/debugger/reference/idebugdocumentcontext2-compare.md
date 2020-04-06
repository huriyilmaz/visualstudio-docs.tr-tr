---
title: IDebugDocumentContext2::Karşılaştır | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731888"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Bu belge bağlamını belirli bir belge bağlamı dizisiyle karşılaştırır.

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
[içinde] Karşılaştırma türünü belirten [numaralandırma DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) bir değer.

`rgpDocContextSet`\
[içinde] Karşılaştırılan belge bağlamlarını temsil eden bir dizi [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesnesi.

`dwDocContextSetLen`\
[içinde] Karşılaştırılacak belge bağlamları dizisinin uzunluğu.

`pdwDocContext`\
[çıkış] Dizin, karşılaştırmayı tatmin eden ilk belge bağlamının `rgpDocContextSet` dizilimine döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Eşleşme `S_OK` bulunursa döndürür. Eşleşme `S_FALSE` bulunamadıysa döndürür. Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dizide geçirilen [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) nesneleri, çağrılan `IDebugDocumentContext2` nesneyi uygulayan aynı hata ayıklama altyapısı tarafından uygulanmalıdır; aksi takdirde, karşılaştırma geçerli değildir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
