---
description: Bu diğer adla ilişkili değeri temsil eden bir yönetilen kod arabirimini verir.
title: IDebugAlias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 223414a7fea10f14fdc8e8c9d71f5b3dbb036ba2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122104435"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Bu diğer adla ilişkili değeri temsil eden bir yönetilen kod arabirimini verir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametreler
`ppUnk`\
[out] `IUnknown` arabirimi, bu diğer adla ilişkili değeri temsil eder. Bu arabirim, arabirim için sorgu `ICorDebugValue` olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem yalnızca yönetilen değerler için geçerlidir (bu, .NET Framework'de kullanılabilen bir arabirimdir ve `ICorDebugValue` cordebug.idl dosyasındaki .NET Framework SDK'sı içinde tanımlanır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
