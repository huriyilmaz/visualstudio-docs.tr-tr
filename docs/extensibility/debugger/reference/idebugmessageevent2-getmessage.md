---
description: Görüntülenecek iletiyi alır.
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d946a020e11b914cbb860c00d681bf94ca249dfaeed60a32b4d407c11f85a4d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433755"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Görüntülenecek iletiyi alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Parametreler
`pMessageType`\
[out] MESSAGETYPE [numaralama](../../../extensibility/debugger/reference/messagetype.md) değerinden iletinin türünü açıklayan bir değer döndürür.

`pbstrMessage`\
[out] İletiyi döndürür.

`pdwType`\
[out] Win32 işlevinin kuralları kullanılarak iletinin türünü `MessageBox` döndürür. Ayrıntılar için [afxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) işlevine bakın.

`pbstrHelpFileName`\
[in, out] Yardım dosyası adını döndürür. Yardım dosyası yoksa null (C++) veya boş (C#) değer olabilir.

`pdwHelpId`\
[in, out] Yardım tanımlayıcısını döndürür. Bu iletiyle ilişkilendirilmiş bir yardım yoksa 0 olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
