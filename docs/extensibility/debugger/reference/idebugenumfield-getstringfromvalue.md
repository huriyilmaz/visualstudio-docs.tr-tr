---
description: Bu yöntem, değerine göre sabit değerinin adını elde ediyor.
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692d5fd16912be8645e99fd2b54a8fbb4871b007
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126727008"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Bu yöntem, değerine göre sabit değerinin adını elde ediyor.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parametreler
`value`\
[in] Sabit sabiti için sabit sabitin adını almak için değer.

`pbstrValue`\
[out] Sabit sabiti sabiti adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde `S_FALSE` değerin ilişkili adı yoksa döndürür veya bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Aynı değerle ilişkili birden fazla ad varsa, numaralamada tanımlanan ad döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
