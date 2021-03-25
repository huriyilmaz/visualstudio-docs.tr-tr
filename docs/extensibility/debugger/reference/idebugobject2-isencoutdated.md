---
description: Bu yöntem, bu nesnenin veya üst kapsayıcının düzenleme ve devam etme durumunun güncel olup olmadığını belirler.
title: 'IDebugObject2:: ısencoutte | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9b78eb0295d039d4f5d8ca3169cb77d04321aaf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053743"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Bu yöntem, bu nesnenin veya üst kapsayıcının düzenleme ve devam etme durumunun güncel olup olmadığını belirler. Özel bir ifade değerlendirici bu yöntemi uygulamaz ve her zaman döndürülür `E_NOTIMPL` .

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parametreler
`pfEncOutdated`\
dışı `TRUE`Düzenle ve devam et durumu güncel değilse sıfır (), değilse sıfır () olur `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

> [!NOTE]
> Özel bir ifade değerlendirici her zaman döndürmelidir `E_NOTIMPL` .

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
