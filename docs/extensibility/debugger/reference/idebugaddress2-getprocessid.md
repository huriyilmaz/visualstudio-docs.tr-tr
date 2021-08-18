---
description: Bu IDebugAddress2 arabirimi tarafından temsil edilen nesnenin sahibi olan işlem kimliğini alın.
title: IDebugAddress2::GetProcessID | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35139838a879aa742ded8d3aac2b57cd71500821
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064896"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Bu [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) arabirimi tarafından temsil edilen nesnenin sahibi olan işlem kimliğini alın.

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
[out] İşlem kimliği.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
