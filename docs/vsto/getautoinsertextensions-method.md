---
title: Getautoınserbir yöntemi
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543513"
---
# <a name="getautoinsertextensions-method"></a>Getautoınserbir yöntemi
  Hata ayıklama sırasında otomatik olarak eklenecek Office uygulamaları hakkında bilgi alır.

 Bu yöntem gelecekte kullanılmak üzere ayrılmıştır.

## <a name="syntax"></a>Söz dizimi

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*psaExtensionNames*|Office uygulamalarının uzantı adları.|

## <a name="return-value"></a>Döndürülen değer
 Metodun başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Office 'in ekleneceği her bir uygulama, **HKEY_CURRENT_USER \Software\Microsoft\Office\WEF\Developer**altındaki bir değere karşılık gelen bir Office uygulaması uzantı adı olarak döndürülür. Konağın bu değerleri kayıt defterinde araması ve sonra otomatik olarak uzantıları eklemesi gerekir.
