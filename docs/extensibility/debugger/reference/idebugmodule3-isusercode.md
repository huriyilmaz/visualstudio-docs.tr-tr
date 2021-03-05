---
description: Modülün Kullanıcı kodunu temsil edip etmediğini gösteren bilgileri alır.
title: 'IDebugModule3:: IsUserCode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a936d4408b2d289477a860ffca3d53ca7b0ad61d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164844"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
Modülün Kullanıcı kodunu temsil edip etmediğini gösteren bilgileri alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT IsUserCode(
   BOOL* pfUser
);
```

```csharp
int IsUserCode(
   out int pfUser
);
```

## <a name="parameters"></a>Parametreler
`pfUser`\
dışı `TRUE`Modül Kullanıcı kodunu temsil ediyorsa sıfır olmayan () `FALSE` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
