---
title: IDebugEnumField::GetValueFromString | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730265"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Bu yöntem, numaralandırma sabiti adı ile ilişkili değeri döndürür.

## <a name="syntax"></a>Sözdizimi

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
[içinde] Değeri almak için adı belirten bir dize. C++'da bunun geniş bir karakter dizesi olduğunu unutmayın.

`pValue`\
[çıkış] İlişkili sayısal değeri verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, ad numaralandırmanın veya bir hata kodunun parçası değilse, döndürür. `S_FALSE`

## <a name="remarks"></a>Açıklamalar
 Bu yöntem büyük/küçük harf duyarlıdır. Büyük/küçük harf duyarlı bir arama gerekiyorsa (örneğin, isimlerin büyük/küçük harf duyarlı olmadığı Visual Basic gibi bir dilde), [GetValueFromStringCaseInsensitive'i](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
