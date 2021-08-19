---
description: Bu nesne için benzersiz bir kimlik veya diğer ad oluşturur veya var olan bir diğer adı döndürür.
title: IDebugObject2::CreateAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::CreateAlias
helpviewer_keywords:
- IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ac9bb6b5916270afc27ec1c8f3b501d78b52664
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043186"
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Bu nesne için benzersiz bir kimlik veya diğer ad oluşturur veya var olan bir diğer adı döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT CreateAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int CreateAlias(
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Parametreler
`ppAlias`\
[out] Yeni (veya var olan) diğer ad.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Diğer ad, nesne bellekteyken belirli bir nesneyi temsil eden bir etikettir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
