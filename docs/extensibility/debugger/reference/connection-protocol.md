---
description: Hata ayıklama sunucusu ile hata ayıklama paketi (DE) arasında iletişim kurmak için kullanılan protokolü belirtir.
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24ac267552166bea43df77f31cb79d8198fb7514
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170867"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Hata ayıklama sunucusu ile hata ayıklama paketi (DE) arasında iletişim kurmak için kullanılan protokolü belirtir.

## <a name="syntax"></a>Syntax

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Alanlar
`CONNECTION_NONE`\
Bir sunucuya bağlantı yapılmadı.

`CONNECTION_UNKNOWN`\
Bir bağlantı kuruldu, ancak bilinmeyen bir türde.

`CONNECTION_LOCAL`\
Bağlantı, yerel bir sunucuya.

`CONNECTION_PIPE`\
Bağlantı, adlandırılmış bir kanal üzerinden.

`CONNECTION_TCPIP`\
Bağlantı TCP/IP kullanır.

`CONNECTION_HTTP`\
Bağlantı HTTP kullanır (bir Web sunucusu üzerinden).

`CONNECTION_OTHER`\
Başka bir bağlantı türü oluşturuldu (Bu değer şu anda kullanılmıyor).

## <a name="remarks"></a>Açıklamalar
Bu değerler [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) yönteminden döndürülür.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
