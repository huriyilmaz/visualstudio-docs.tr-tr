---
description: Hata ayıklama sırasında otomatik Office uygulamalar hakkında bilgi alır.
title: GetAutoInsertExtensions yöntemi
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7bb7a75c4bc1abd5c5fb29c55a3be42e44ff2af55403c1d9ecccbf00efb5c755
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268332"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions yöntemi
  Hata ayıklama sırasında otomatik Office uygulamalar hakkında bilgi alır.

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
|*psaExtensionNames*|Uygulamalar için uzantı adları Office.|

## <a name="return-value"></a>Döndürülen değer
 Yöntemin başarıyla tamamlandıktan sonra tamamlandıktan sonra bir HRESULT değeri.

## <a name="remarks"></a>Açıklamalar
 Eklenecek Office her uygulama, Office altındaki bir değere karşılık gelen bir uygulama uzantısı adı **olarakHKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer.** Ana bilgisayar bu değerleri kayıt defterinde bu şekilde olmalı ve ardından uzantıları otomatik olarak eklemeli.
