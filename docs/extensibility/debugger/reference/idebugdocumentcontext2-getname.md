---
title: IDebugDocumentContext2::GetName | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 253ef509a60e8bb2ce177235f4b93b370e66f484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731815"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Bu belge bağlamını içeren belgenin görüntülenebilir adını alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>Parametreler
`gnType`\
[içinde] GETNAME_TYPE numaralandırmadan döndürülecek ad türünü belirten bir değer. [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)

`pbstrFileName`\
[çıkış] Dosyanın adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
Belge bağlamı belge adının kendisini depolamak için yazılmamışsa (Örnek'te gösterin) çağrıyı genellikle [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) yöntemine iletir.

## <a name="example"></a>Örnek
Aşağıdaki örnek, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) `CDebugContext` arabirimini ortaya çıkaran basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
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
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
