---
description: Bu işlem için GUID 'YI alır.
title: 'IDebugProcess2:: GetProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d93225a676efe2a5af6a6064f4251c1a9cb02b2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168172"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Bu işlem için GUID 'YI alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Parametreler
`pguidProcessId`\
dışı Bu işlem için GUID döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Genel benzersiz tanımlayıcı (GUID), bu işlemi sistemde çalışan tüm diğer işlemlerden tanımlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
