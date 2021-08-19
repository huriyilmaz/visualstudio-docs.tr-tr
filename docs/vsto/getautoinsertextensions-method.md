---
description: hata ayıklama sırasında otomatik olarak eklenecek Office uygulamalar hakkında bilgi alır.
title: Getautoınserbir yöntemi
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
ms.openlocfilehash: 0a4da4447af30a44c00d824120fb6733f409a6ac
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155999"
---
# <a name="getautoinsertextensions-method"></a>Getautoınserbir yöntemi
  hata ayıklama sırasında otomatik olarak eklenecek Office uygulamalar hakkında bilgi alır.

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
 eklenecek Office yönelik her uygulama, **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer** altındaki bir değere karşılık gelen bir Office uygulama uzantısı adı olarak döndürülür. Konağın bu değerleri kayıt defterinde araması ve sonra otomatik olarak uzantıları eklemesi gerekir.
