---
description: Bu diğer adı kaldırma için işaretler.
title: IDebugAlias::D ıspoz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7428b1a8d0dcb95d14274270542d4bba8c50bde9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059189"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Bu diğer adı kaldırma için işaretler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parametreler
 Yok.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem çağrıldıktan sonra, diğer ad artık kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
