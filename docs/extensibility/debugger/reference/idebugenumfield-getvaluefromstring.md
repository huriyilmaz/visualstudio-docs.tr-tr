---
title: 'Ihata ayıklama Genumfield:: GetValueFromString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730265"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Bu yöntem, bir numaralandırma sabiti adı ile ilişkili değeri döndürür.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parametreler
`pszValue`\
'ndaki Değerin alınacağı adı belirten bir dize. C++ için bu, geniş bir karakter dizesidir.

`pValue`\
dışı İlişkili sayısal değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` ad numaralandırmanın bir parçası değilse, veya bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, büyük/küçük harfe duyarlıdır. Büyük/küçük harf duyarsız bir arama gerekliyse (örneğin, adların büyük/küçük harfe duyarlı olmadığı Visual Basic bir dilde), [Getvaluefromstringcaseduyarsız](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)' i kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
