---
title: 'VsgDbg:: VsgDbg (Oluşturucu) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734755"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Oluşturucu)
Grafik tanılama 'nın uygulama içi bileşenini, belirtilen Boolean parametresine göre varsayılan olarak yakalayıp, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için `VsgDbg` sınıfının bir örneğini oluşturur.

## <a name="syntax"></a>Sözdizimi

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametreler
 Grafik tanılama 'nın uygulama içi bileşeninin grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek üzere hazırlanacağını belirtmek için `true` `bDefaultInit`;  uygulamanın Şu anda grafik bilgilerini etkin bir şekilde yakalayıp kaydetmek üzere hazırlanmamalıdır `false`.

## <a name="remarks"></a>Açıklamalar
 Oluşturucu `bDefaultInit` `true` olarak ayarlandığında, grafik günlük dosyasının dosya adı `DONT_SAVE_VSGLOG_TO_TEMP` ve `VSG_DEFAULT_RUN_FILENAME` Önişlemci simgelerinin uygulamanıza dahil etmeden `vsgcapture.h` önce nasıl tanımlandığını belirler.

 Oluşturucu `false` olarak ayarlanan `bDefaultInit` ile çağrıldığında, grafik tanılama 'nın uygulama içi bileşeni, daha sonra `Init` işlevi çağırarak grafik bilgilerini daha sonra yakalamak ve kaydetmek için hazır olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [VsgDbg::~VsgDbg (Yok Edici)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)