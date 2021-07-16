---
description: Belirtilen Boole parametresine bağlı olarak grafik bilgilerini varsayılan olarak etkin bir şekilde yakalamak ve kaydetmek için grafik tanılamanın uygulama içinde bileşenini hazırlayan veya hazırlamadan VsgDbg sınıfının bir örneğini oluşturun.
title: VsgDbg::VsgDbg (Oluşturucu) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e3693301aef27e01f2d12fa954f94fcc55fb8dea
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232433"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Oluşturucu)
Belirtilen Boole parametresine göre grafik bilgilerini varsayılan olarak etkin bir şekilde yakalamak ve kaydetmek için grafik tanılamanın uygulama içinde bileşenini hazırlamadan veya ile sınıfının `VsgDbg` bir örneğini oluşturun.

## <a name="syntax"></a>Sözdizimi

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametreler
 `bDefaultInit`grafik tanılamanın uygulama içinde bileşeninin grafik bilgilerini etkin bir şekilde yakalamaya ve `true` kaydetmeye hazır olacağını belirtmek için; `false` uygulamanın şu anda etkin bir şekilde grafik bilgilerini yakalamaya ve kaydetmeye hazır olmadığını belirtmek için.

## <a name="remarks"></a>Açıklamalar
 oluşturucusu olarak ayarlandığı zaman, grafik günlük dosyasının dosya adı ve önişlemci sembollerinin uygulamanıza dahil olmadan önce nasıl `bDefaultInit` `true` `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` `vsgcapture.h` tanımlandığına göre belirlenir.

 oluşturucusu olarak ayarlanacak şekilde çağrıldılarında, grafik tanılamalarının uygulama içinde bileşeni, daha sonra işlevi çağrılarak grafik bilgilerini etkin bir şekilde yakalamaya ve `bDefaultInit` `false` kaydetmeye `Init` hazırlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [VsgDbg::~VsgDbg (Yok Edici)](vsgdbg-tilde-vsgdbg-destructor.md)
- [ınit](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
