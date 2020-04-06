---
title: IDebugÖzellik3::GetStringChars | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721085"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Bu özellik ile ilişkili dize alır ve kullanıcı tarafından sağlanan arabellekte depolar.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Parametreler
`buflen`\
[içinde] Kullanıcı tarafından sağlanan arabellek tetbit edebileceği maksimum karakter sayısı.

`rgString`\
[çıkış] Dizeyi döndürür.

 [Yalnızca `rgString` C++, dize Tekkod karakterleri alan bir arabellek için bir işaretçidir. Bu arabellek boyutu `buflen` en az karakter (bayt değil) olmalıdır.

`pceltFetched`\
[çıkış] Arabellekte depolanan karakter sayısının döndürüldüğü yer. (C++'da olabilir.) `NULL`

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
C++'da arabellek en azından `buflen` Unicode karakterleri uzun olduğundan emin olmak için dikkatli olunmalıdır. Unicode karakterinin 2 bayt uzunluğunda olduğunu unutmayın.

> [!NOTE]
> C++'da döndürülen dize sonlandırıcı null karakterini içermez. Verilirse, `pceltFetched` dizedeki karakter sayısını belirtir.

## <a name="example"></a>Örnek

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
