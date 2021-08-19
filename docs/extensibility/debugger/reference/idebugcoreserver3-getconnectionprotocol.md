---
description: Sunucu ile hata ayıklama paketi arasında iletişim kurmak için kullanılan protokolü gösteren bir değer döndürür.
title: 'IDebugCoreServer3:: GetConnectionProtocol | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords:
- IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46a5f134eb46380d0abfac7531da8f1557de1a51
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111521"
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
Sunucu ile hata ayıklama paketi arasında iletişim kurmak için kullanılan protokolü gösteren bir değer döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetConnectionProtocol(
   CONNECTION_PROTOCOL* pProtocol
);
```

```csharp
int GetConnectionProtocol(
   CONNECTION_PROTOCOL[] pProtocol
);
```

## <a name="parameters"></a>Parametreler
`pProtocol`\
dışı [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) numaralandırmasındaki değerlerden birini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)
