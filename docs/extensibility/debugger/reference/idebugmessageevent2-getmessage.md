---
description: Görüntülenecek iletiyi alır.
title: 'IDebugMessageEvent2:: GetMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 26280ca238b5ffc96b0d8b29f1b2d1a424c544d0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172478"
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
dışı İleti türünü açıklayan [MessageType](../../../extensibility/debugger/reference/messagetype.md) numaralandırmasından bir değer döndürür.

`pbstrMessage`\
dışı İletiyi döndürür.

`pdwType`\
dışı Win32 işlevinin kurallarını kullanarak iletinin türünü döndürür `MessageBox` . Ayrıntılar için bkz. [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) işlevi.

`pbstrHelpFileName`\
[in, out] Yardım dosyası adını döndürür. Yardım dosyası yoksa null (C++) veya boş (C#) değeri olabilir.

`pdwHelpId`\
[in, out] Yardım tanımlayıcısını döndürür. Bu iletiyle ilişkili bir yardım yoksa 0 olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
