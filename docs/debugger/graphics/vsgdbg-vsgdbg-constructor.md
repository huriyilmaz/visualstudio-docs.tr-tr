---
description: Grafik tanılama 'nın uygulama içi bileşenini, belirtilen Boolean parametresine göre varsayılan olarak, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için, grafik tanılama 'nın uygulama içi bileşenini hazırlamadan veya ile birlikte VsgDbg sınıfının bir örneğini oluşturur.
title: 'VsgDbg:: VsgDbg (Oluşturucu) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae4259b1af1bcb51b05431131db596d2a26da895
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160453"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Oluşturucu)
Grafik `VsgDbg` Tanılama 'nın uygulama içi bileşenini, belirtilen Boolean parametresine göre varsayılan olarak yakalayıp, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için bir örneği ile veya kullanarak bir sınıfının örneğini oluşturur.

## <a name="syntax"></a>Sözdizimi

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametreler
 `bDefaultInit``true`Grafik tanılama 'nın uygulama içi bileşeninin grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek üzere hazırlanacağını belirtmek için; `false` uygulamanın Şu anda grafik bilgilerini etkin bir şekilde yakalayıp kaydetmek üzere hazırlanmamalıdır.

## <a name="remarks"></a>Açıklamalar
 Oluşturucu `bDefaultInit` olarak ayarlandığı ile çağrıldığında `true` , grafik günlük dosyasının dosya adı, `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` uygulamanıza dahil etmeden önce ve Önişlemci simgelerinin nasıl tanımlanarak belirlenir `vsgcapture.h` .

 Oluşturucu `bDefaultInit` olarak ayarlandığı ile çağrıldığında `false` , grafik tanılama 'nın uygulama içi bileşeni, daha sonra işlevi çağırarak grafik bilgilerini daha sonra yakalamak ve kaydetmek için hazır olabilir `Init` .

## <a name="see-also"></a>Ayrıca bkz.
- [VsgDbg::~VsgDbg (Yok Edici)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Dengeleyici](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
