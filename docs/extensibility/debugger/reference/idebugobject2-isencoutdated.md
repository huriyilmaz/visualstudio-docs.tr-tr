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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 583b77ed4f3fbfc81bb595ddde025b8c08f169dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170022"
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
