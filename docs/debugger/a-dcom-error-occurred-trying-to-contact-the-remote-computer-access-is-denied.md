---
title: Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi.
titleSuffix: ''
description: "'Uzak bilgisayarla iletişim kurmak için bir DCOM hatası oluştu. Erişim reddedildi.' Uzaktan hata ayıklama hata Visual Studio ilgili bilgileri görüntüleme."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 53d8bbb4a4d053e4120cacfb1d44ca14295a3d22
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630998"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi.
Uzaktan hata ayıklama, aşağıdaki durumlarda yerel ve uzak bilgisayarlar arasında iletişim kurmak için DCOM kullanır:

- Hata ayıklayıcısı Yerel Uyumluluk Modu olarak **ayarlanır veya** Yönetilen **Uyumluluk Modu** Araçlar > Seçenekler > Hata Ayıklama **sayfasında denetlenir**

- Yönetilen C++ (C++/CLI) kodunda hata ayıklaması var.

- Bu Visual Studio 2013, **Araçlar** ve Seçenekler'de Yerel Düzenlemeyi ve **Devam'ı Etkinleştir** seçeneği > hata ayıklama > denetlenir

- Bazı üçüncü taraf hata ayıklama senaryoları

  Bu hata, Visual Studio DCOM üzerinden uzaktan hata ayıklayıcı işlemi için kimlik doğrulaması (veya sağlanan kimlik bilgilerinin yetersiz olduğu kabul edildi) durumunda oluşur. Aşağıdaki geçici çözümlerden biri veya daha fazlası sorunu çözebilir:

- Yerel **Uyumluluk Modu ve Yönetilen** **Uyumluluk Modu'ni kapatın.**

- Bu Visual Studio 2013 Yerel Düzenle ve **Devam'a etkinleştir'i kapatın.**

- her iki bilgisayarı da yeniden başlatın.

- Uzaktan hata ayıklama kimlik bilgilerini girmeyi gerektiriyorsa, kimlik bilgilerini kaydetme seçeneğini işaretleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)