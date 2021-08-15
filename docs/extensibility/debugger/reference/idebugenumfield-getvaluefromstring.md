---
description: Bu yöntem, bir sabit sabiti adı ile ilişkili değeri döndürür.
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3060fafd2c887dd79933bb1baa04644d77a1113a132c3d751b31332c7643d526
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360514"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Bu yöntem, bir sabit sabiti adı ile ilişkili değeri döndürür.

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
[in] Değerin elde etmek istediğiniz adı belirten bir dize. C++ için bunun geniş bir karakter dizesi olduğunu unutmayın.

`pValue`\
[out] İlişkili sayısal değeri döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde, ad, numaralamanın bir parçası değilse veya bir `S_FALSE` hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem büyük/büyük/büyük harfe duyarlıdır. Büyük/küçük harfe duyarlı olmayan bir arama gerekirse (örneğin, adların büyük/küçük harfe duyarlı Visual Basic gibi bir dilde), [GetValueFromStringCaseInsensitive kullanın.](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
