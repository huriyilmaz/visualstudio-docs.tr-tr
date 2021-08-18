---
description: İnsan tarafından okunabilir bir hata iletisinin yapısına olanak sağlayan bilgileri döndürür.
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
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
ms.openlocfilehash: 2cf7b18d84ae8279c5d15f9404a6d8d500d44d82
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118911"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
İnsan tarafından okunabilir bir hata iletisinin yapısına olanak sağlayan bilgileri döndürür.

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
[out] [MESSAGETYPE numaralama değerinden](../../../extensibility/debugger/reference/messagetype.md) ileti türünü açıklayan bir değer döndürür.

`pbstrErrorFormat`\
[out] Kullanıcıya son iletinin biçimi (ayrıntılar için bkz. "Açıklamalar").

`hrErrorReason`\
[out] İletinin ilgili olduğu hata kodu.

`pdwType`\
[out] Hatanın önem derecesi (için MB_XXX sabitlerini `MessageBox` kullanın; örneğin, `MB_EXCLAMATION` veya `MB_WARNING` ).

`pbstrHelpFileName`\
[out] Yardım dosyasının yolu (yardım dosyası yoksa null değere ayarlanır).

`pdwHelpId`\
[out] Görüntülemek için yardım konusunun kimliği (yardım konusu yoksa 0 olarak ayarlayın).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata iletisi, satırlarında biçimlendirilmiş `"What I was doing.  %1"` olmalıdır. Daha sonra , çağıranın yerine hata kodundan türetilen hata `"%1"` iletisiyle (içinde döndürülür) `hrErrorReason` değiştirilir. parametresi, `pMessageType` çağrıyı yapana son hata iletisinin nasıl görüntüleniyor olması gerektiğini söyler.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
