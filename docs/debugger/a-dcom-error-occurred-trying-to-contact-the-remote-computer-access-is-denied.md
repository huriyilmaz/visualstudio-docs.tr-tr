---
title: Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi.
titleSuffix: ''
description: "' Uzak bilgisayara bağlanmaya çalışırken bir DCOM hatası oluştu. Erişim engellendi. ' bu Visual Studio uzaktan hata ayıklama hata başvurusuyla ilgili bilgileri görüntüleyin."
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052492"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi.
Uzaktan hata ayıklama, aşağıdaki durumlarda yerel ve uzak bilgisayarlar arasında iletişim kurmak için DCOM kullanır:

- Hata ayıklayıcı **Yerel uyumluluk moduna** ayarlı veya **yönetilen uyumluluk modu** **Araçlar > seçenekler > hata ayıklama** sayfasında işaretlendi

- Yönetilen C++ (C++/CLı) kodunda hata ayıklaması yapıyorsanız.

- Visual Studio 2013, **yerel düzenle ve devam et** ' i etkinleştir **araçlar > seçenekler > hata ayıklama** sayfasında işaretlenir

- Bazı üçüncü taraf hata ayıklama senaryoları

  bu hata, Visual Studio işlemi DCOM üzerinden uzaktan hata ayıklayıcı işlemine kendi kimliğini doğrulayamadığında (veya sağlanan kimlik bilgileri yetersiz olduğu kabul edildiğinde) oluşur. Aşağıdaki geçici çözümlerden biri veya birkaçı sorunu çözebilir:

- **Yerel uyumluluk modunu** ve **yönetilen uyumluluk modunu** kapatın.

- Visual Studio 2013, **yerel düzenlemeyi etkinleştir ve devam et**' i kapatın.

- Her iki bilgisayarı da yeniden başlatın.

- Uzaktan hata ayıklama kimlik bilgilerini girmeyi gerektiriyorsa, kimlik bilgilerini kaydetme seçeneğini işaretleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)