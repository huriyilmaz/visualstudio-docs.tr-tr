---
title: IDebugEnumField::GetValueFromStringCaseDuyarsız | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730244"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Bu yöntem, numaralandırma sabiti adı ile ilişkili değeri döndürmek için büyük/küçük bir durum duyarsız arama kullanır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
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
 Bu yöntem büyük/küçük harf duyarsız. Büyük/küçük harf duyarlı bir arama gerekiyorsa (örneğin, adların büyük/küçük harf duyarlı olduğu C++ gibi bir dilde), [GetValueFromString'i](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
