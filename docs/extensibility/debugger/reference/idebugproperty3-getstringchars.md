---
description: Bu özellikle ilişkili dizeyi alır ve kullanıcı tarafından sağlanan bir arabellekte depolar.
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c37f4a909596a88b42ce6432cef97d1202388667
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063869"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Bu özellikle ilişkili dizeyi alır ve kullanıcı tarafından sağlanan bir arabellekte depolar.

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
[in] Kullanıcı tarafından sağlanan arabelleğin tutacağı maksimum karakter sayısı.

`rgString`\
[out] Dizeyi döndürür.

 [Yalnızca C++ ], `rgString` dizenin Unicode karakterlerini alan bir arabelleğe işaretçidir. Bu arabelleğin boyutu `buflen` en az karakter (bayt değil) olmalıdır.

`pceltFetched`\
[out] Gerçekte arabellekte depolanan karakter sayısı döndürülür. `NULL`(C++ içinde olabilir.)

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
C++ içinde, arabelleğin en az Unicode karakter uzunluğunda olması için `buflen` özen göster göster gerekir. Bir Unicode karakterinin 2 bayt uzunluğunda olduğunu unutmayın.

> [!NOTE]
> C++ içinde, döndürülen dize sonlandırıcı bir null karakter içermez. `pceltFetched`Verilirse, dizedeki karakter sayısını belirtir.

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
