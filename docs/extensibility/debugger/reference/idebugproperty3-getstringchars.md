---
description: Bu özellikle ilişkili dizeyi alır ve Kullanıcı tarafından sağlanan arabellekte depolar.
title: 'IDebugProperty3:: GetStringChars | Microsoft Docs'
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
ms.openlocfilehash: 8056b6ebcbb9d6758c05d482b02f0cac584d4a3e7a21974562b7e83658d32308
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402421"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Bu özellikle ilişkili dizeyi alır ve Kullanıcı tarafından sağlanan arabellekte depolar.

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
'ndaki Kullanıcı tarafından sağlanan arabelleğin tutabilecek en fazla karakter sayısı.

`rgString`\
dışı Dizeyi döndürür.

 [Yalnızca C++], `rgString` dizenin Unicode karakterlerini alan arabelleğin bir işaretçisidir. Bu arabellek en az `buflen` karakter (bayt değil) boyutunda olmalıdır.

`pceltFetched`\
dışı Aslında arabellekte depolanan karakterlerin sayısı döndürülür. ( `NULL` C++ ' da olabilir.)

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
C++ ' da, arabelleğin en az Unicode karakter uzunluğunda olduğundan emin olmak için dikkatli olunmalıdır `buflen` . Unicode karakterinin 2 bayt uzunluğunda olduğunu unutmayın.

> [!NOTE]
> C++ ' da, döndürülen dize bir Sonlandırıcı null karakteri içermez. Belirtilmişse `pceltFetched` dizedeki karakter sayısını belirtir.

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
