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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734755"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Oluşturucu)
Grafik `VsgDbg` Tanılama 'nın uygulama içi bileşenini, belirtilen Boolean parametresine göre varsayılan olarak yakalayıp, grafik bilgilerini etkin bir şekilde yakalamak ve kaydetmek için bir örneği ile veya kullanarak bir sınıfının örneğini oluşturur.

## <a name="syntax"></a>Söz dizimi

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