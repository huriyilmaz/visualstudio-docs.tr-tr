---
description: İnsanlar tarafından okunabilen bir hata iletisinin oluşturulmasına izin veren bilgileri döndürür.
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c35d0bda87ded6de95b7bc744c01ea82a97ab3354a2dbf0330dd2abcd18a5097
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417320"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
İnsanlar tarafından okunabilen bir hata iletisinin oluşturulmasına izin veren bilgileri döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parametreler
`pMessageType`\
dışı İleti türünü açıklayan [MessageType](../../../extensibility/debugger/reference/messagetype.md) numaralandırmasından bir değer döndürür.

`pbstrErrorFormat`\
dışı Kullanıcıya son iletinin biçimi (Ayrıntılar için bkz. "açıklamalar").

`hrErrorReason`\
dışı İletinin bulunduğu hata kodu.

`pdwType`\
dışı Hatanın önem derecesi (için MB_XXX sabitleri kullanın `MessageBox` ; Örneğin, `MB_EXCLAMATION` veya `MB_WARNING` ).

`pbstrHelpFileName`\
dışı Yardım dosyasının yolu (Yardım dosyası yoksa null değere ayarlanır).

`pdwHelpId`\
dışı Görüntülenecek Yardım konusunun KIMLIĞI (Yardım konusu yoksa 0 olarak ayarlanır).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata iletisi, satırları üzerinde biçimlendirilmelidir `"What I was doing.  %1"` . `"%1"`Ardından, çağıran tarafından, hata kodundan (' de döndürülen) alınan hata iletisiyle değiştirilmelidir `hrErrorReason` . `pMessageType`Parametresi, çağıranın son hata iletisinin nasıl görüntüleneceğini söyler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
