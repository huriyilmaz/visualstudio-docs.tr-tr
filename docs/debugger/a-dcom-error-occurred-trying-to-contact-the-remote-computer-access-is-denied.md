---
title: Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi. | Microsoft Belgeleri
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc9cae027a078a62b1ef7bab16994a418d76763
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745838"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Uzak bilgisayara erişilmeye çalışılırken DCOM hatası oluştu. Erişim reddedildi.
Uzaktan hata ayıklama, aşağıdaki durumlarda yerel ve uzak bilgisayarlar arasında iletişim kurmak için DCOM kullanır:

- Hata ayıklayıcı **Yerel uyumluluk moduna** ayarlı veya **yönetilen uyumluluk modu** **Araçlar > seçenekler > hata ayıklama** sayfasında işaretlendi

- Yönetilen C++ (C++/CLı) kodunda hata ayıklaması yapıyorsanız.

- Visual Studio 2013, **Yerel Düzenle ve devam et** ' i etkinleştir **araçlar > seçenekler > hata ayıklama** sayfasında işaretlenir

- Bazı üçüncü taraf hata ayıklama senaryoları

  Bu hata, Visual Studio işleminin kimlik doğrulaması yapamadığında (veya sağlanan kimlik bilgileri yetersiz olduğu kabul edildiğinde) DCOM üzerinden uzaktan hata ayıklayıcı işlemi için oluşur. Aşağıdaki geçici çözümlerden biri veya birkaçı sorunu çözebilir:

- **Yerel uyumluluk modunu** ve **yönetilen uyumluluk modunu**kapatın.

- Visual Studio 2013, **yerel düzenlemeyi etkinleştir ve devam et**' i kapatın.

- Her iki bilgisayarı da yeniden başlatın.

- Uzaktan hata ayıklama kimlik bilgilerini girmeyi gerektiriyorsa, kimlik bilgilerini kaydetme seçeneğini işaretleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)