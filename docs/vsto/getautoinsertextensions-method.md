---
title: Getautoınserbir yöntemi
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24fd5768a9eafa4a023aeabf21c862ea1a0d1891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931532"
---
# <a name="getautoinsertextensions-method"></a>Getautoınserbir yöntemi
  Hata ayıklama sırasında otomatik olarak eklenecek Office uygulamaları hakkında bilgi alır.

 Bu yöntem gelecekte kullanılmak üzere ayrılmıştır.

## <a name="syntax"></a>Sözdizimi

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
 Office 'in ekleneceği her bir uygulama, **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer** altındaki bir değere karşılık gelen bir Office uygulaması uzantı adı olarak döndürülür. Konağın bu değerleri kayıt defterinde araması ve sonra otomatik olarak uzantıları eklemesi gerekir.
