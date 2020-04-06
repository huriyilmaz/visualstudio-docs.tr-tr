---
title: CONNECTION_PROTOCOL | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737640"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Hata ayıklama sunucusu ile hata ayıklama paketi (DE) arasında iletişim kurmak için kullanılan protokolü gösterir.

## <a name="syntax"></a>Sözdizimi

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Alanlar
`CONNECTION_NONE`\
Sunucuya bağlantı yapılmadı.

`CONNECTION_UNKNOWN`\
Bir bağlantı yapıldı, ancak bilinmeyen bir tür.

`CONNECTION_LOCAL`\
Bağlantı yerel bir sunucuya.

`CONNECTION_PIPE`\
Bağlantı adlı bir boru aracılığıyla yapılır.

`CONNECTION_TCPIP`\
Bağlantı TCP/IP kullanır.

`CONNECTION_HTTP`\
Bağlantı HTTP (bir Web sunucusu üzerinden) kullanır.

`CONNECTION_OTHER`\
Başka bir bağlantı türü oluşturuldu (bu değer şu anda kullanılmadı).

## <a name="remarks"></a>Açıklamalar
Bu değerler [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) yönteminden döndürülür.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
