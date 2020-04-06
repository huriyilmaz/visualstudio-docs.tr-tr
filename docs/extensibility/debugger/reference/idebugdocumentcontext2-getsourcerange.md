---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731794"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Bu belge bağlamının kaynak kod aralığını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametreler
`pBegPosition`\
[içinde, dışarı] Başlangıç pozisyonuyla doldurulmuş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapı. Bu bilgiler gerekli değilse, bu bağımsız değişkeni null değere ayarlayın.

`pEndPosition`\
[içinde, dışarı] Bitiş pozisyonuyla doldurulmuş [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapı. Bu bilgiler gerekli değilse, bu bağımsız değişkeni null değere ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Kaynak aralığı, geçerli deyimden koda katkıda bulunan önceki deyimden hemen sonrasına kadar tüm kaynak kodu aralığıdır. Kaynak aralığı genellikle, açıklamalar da dahil olmak üzere kaynak deyimleri sökme penceresindekodla karıştırmak için kullanılır.

 Bu belge bağlamında yer alan kod ekstreleri aralığını almak için [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) yöntemini arayın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
