---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12e575979e5bd1527dfa0d8e15b290d6b78e36ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723911"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Bu işlem için GUID 'YI alır.

## <a name="syntax"></a>Söz dizimi

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
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
