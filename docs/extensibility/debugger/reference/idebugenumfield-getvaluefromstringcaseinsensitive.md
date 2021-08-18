---
description: Bu yöntem, bir numaralandırma sabiti adı ile ilişkili değeri döndürmek için büyük/küçük harf duyarsız bir arama kullanır.
title: 'Ihata ayıklama Genumfield:: Getvaluefromstringcaseduyarsız | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a39bb6ae031aac8ae9fb72134ff3744dacb59ece
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096212"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Bu yöntem, bir numaralandırma sabiti adı ile ilişkili değeri döndürmek için büyük/küçük harf duyarsız bir arama kullanır.

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
'ndaki Değerin alınacağı adı belirten bir dize. C++ için bu, geniş bir karakter dizesidir.

`pValue`\
dışı İlişkili sayısal değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` ad numaralandırmanın bir parçası değilse, veya bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, büyük/küçük harfe duyarlıdır. Büyük/küçük harfe duyarlı bir arama gerekiyorsa (örneğin, adların büyük/küçük harfe duyarlı olduğu C++ gibi bir dilde) [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)kullanın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
