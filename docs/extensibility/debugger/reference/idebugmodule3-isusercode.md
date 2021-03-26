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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbc56943574cc5549e96e3281b4398df7d486f7d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065612"
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
