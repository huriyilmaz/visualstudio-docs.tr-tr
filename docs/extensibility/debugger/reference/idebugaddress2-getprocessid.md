---
description: Bu IDebugAddress2 arabirimi tarafından temsil edilen nesneye sahip olan işlemin KIMLIĞINI alır.
title: 'IDebugAddress2:: GetProcessId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd7665af4f88c695dd74b51293da3eced3861230
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059203"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Bu [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) arabirimi tarafından temsil edilen nesneye sahip olan işlemin kimliğini alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Parametreler
`pProcID`\
dışı İşlem KIMLIĞI.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
