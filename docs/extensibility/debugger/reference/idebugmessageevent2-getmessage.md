---
title: IDebugMessageEvent2::GetMessage | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 819b796a656f0ef8775fbb1c9e800e3019b81729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727402"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
İletinin görüntülenmesini alır.

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
[çıkış] İleti türünü açıklayan [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) numaralandırmasından bir değer döndürür.

`pbstrMessage`\
[çıkış] İletiyi döndürür.

`pdwType`\
[çıkış] Win32 `MessageBox` işlevinin kurallarını kullanarak iletitürünü döndürür. Ayrıntılar için [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) işlevine bakın.

`pbstrHelpFileName`\
[içinde, dışarı] Yardım dosyası adını döndürür. Yardım dosyası yoksa null (C++) veya boş (C#) değeri olabilir.

`pdwHelpId`\
[içinde, dışarı] Yardım tanımlayıcısını döndürür. Bu iletiyle ilişkili bir yardım yoksa 0 olabilir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
