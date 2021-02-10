---
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ba5456ba3beabb1d5418d739be2aa74838daa41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947183"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Bu diğer adla ilişkili değeri temsil eden bir yönetilen kod arabirimini alır.

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
[out] `IUnknown` Bu diğer adla ilişkili değeri temsil eden arabirim. Bu arabirim arabirim için sorgulanabilir `ICorDebugValue` .

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem yalnızca yönetilen değerler için geçerlidir ( `ICorDebugValue` .NET Framework kullanılabilir bir arabirimdir ve CorDebug. IDL dosyasındaki .NET Framework SDK 'sında tanımlanmıştır).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
