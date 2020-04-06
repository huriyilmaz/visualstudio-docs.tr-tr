---
title: IDebugEnumField::GetStringFromValue | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730291"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Bu yöntem değeri göz önüne alındığında numaralandırma sabitinin adını alır.

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
[içinde] Numaralandırma sabitinin adını almak için gereken değer.

`pbstrValue`\
[çıkış] Numaralandırma sabitinin adını verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, `S_FALSE` değerilişkili bir adı yoksa veya bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Aynı değerle ilişkili birden fazla ad varsa, numaralandırmada tanımlanan ilk ad döndürülür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
