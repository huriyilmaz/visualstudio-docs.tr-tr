---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730035"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
İnsan tarafından okunabilir bir hata iletisinin yapılmasına izin veren bilgileri verir.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parametreler
`pMessageType`\
[çıkış] İleti türünü açıklayan [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) numaralandırmasından bir değer döndürür.

`pbstrErrorFormat`\
[çıkış] Kullanıcıya son iletinin biçimi (ayrıntılar için "Açıklamalar"a bakın).

`hrErrorReason`\
[çıkış] İletinin ilgili hata kodu.

`pdwType`\
[çıkış] Hatanın önem derecesi (MB_XXX sabitlerini `MessageBox`kullanın; `MB_EXCLAMATION` `MB_WARNING`

`pbstrHelpFileName`\
[çıkış] Yardım dosyasına giden yol (yardım dosyası yoksa null değerine ayarlayın).

`pdwHelpId`\
[çıkış] Görüntülenecek yardım konusunun kimliği (yardım konusu yoksa 0 olarak ayarlayın).

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Hata iletisi `"What I was doing.  %1"`. Daha `"%1"` sonra hata kodundan türetilen hata iletisi (döndürülür) `hrErrorReason`ile arayan tarafından değiştirilir. Parametre, `pMessageType` arayana son hata iletisinin nasıl görüntüleneceğini bildirir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
