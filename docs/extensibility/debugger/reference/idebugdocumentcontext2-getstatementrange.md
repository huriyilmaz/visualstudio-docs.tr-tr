---
title: IDebugDocumentContext2::GetStatementRange | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731774"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Belge bağlamının dosya ekstre aralığını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
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
İfade aralığı, bu belge bağlamının ifade ettiği koda katkıda bulunan satırların aralığıdır.

Bu belge bağlamında kaynak kodu (açıklamalar dahil) aralığını elde etmek için [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) yöntemini arayın.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) `CDebugContext` arabirimini ortaya çıkaran basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir. Bu örnek, yalnızca başlangıç konumu null değeri değilse bitiş konumunu doldurur.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
