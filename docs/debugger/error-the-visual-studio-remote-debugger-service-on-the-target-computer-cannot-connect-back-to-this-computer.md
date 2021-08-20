---
description: Bu hata, uzaktan hata ayıklayıcı hizmetinin, hata ayıklana bilgisayara bağlanmaya çalıştığında kimlik doğrulaması yapmayan bir kullanıcı hesabı altında çalıştığından emin olun.
title: Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti geriye bu bilgisayara bağlanamıyor
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 986fdcdd9b22c76ba87ba31a9e9a256363c40a01
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112821"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Hata: Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti geriye bu bilgisayara bağlanamıyor
Bu hata, uzaktan hata ayıklayıcı hizmetinin, hata ayıklana bilgisayara bağlanmaya çalıştığında kimlik doğrulaması yapmayan bir kullanıcı hesabı altında çalıştığından emin olun. Bu hata, eski hata ayıklama altyapısı kullanılarak uzaktan hata ayıklarken ve uzaktan hata ayıklayıcı bir hizmet olarak çalıştırıldıkları zaman oluşabilir.

 Aşağıdaki tabloda hangi hesapların bilgisayara erişebilirsiniz?

|Senaryo|LocalSystem hesabı|Etki alanı hesabı|Her iki bilgisayarda da aynı kullanıcı adı ve parolaya sahip yerel hesaplar|
|-|-|-|-|
|Aynı etki alanındaki her iki bilgisayar|Yes|Yes|Yes|
|İki yol güveni olan etki alanlarındaki her iki bilgisayar|Hayır|Hayır|Yes|
|Çalışma grubu üzerinde bir veya iki bilgisayar|Hayır|Hayır|Yes|
|Farklı etki alanlarındaki bilgisayarlar|Hayır|Hayır|Yes|

 Ek olarak:

- Visual Studio Uzaktan Hata Ayıklayıcı hizmetini altında Visual Studio Uzaktan Hata Ayıklayıcı, herhangi bir işlemde hata ayıklaması için uzak bilgisayarda bir yönetici olmalıdır.

- Hesaba, Yerel Güvenlik İlkesi yönetim `Log on as a service` aracını kullanan uzak bilgisayarda da ayrıcalık **verilmesi** gerekir.

- Bilgisayara erişen bir yerel hesap kullanıyorsanız, yerel bir hesap altında Visual Studio Uzaktan Hata Ayıklayıcı hizmet çalıştırmanız gerekir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Uzak bilgisayarda Visual Studio Uzaktan Hata Ayıklayıcı doğru şekilde ayar olduğundan emin olun. Daha fazla bilgi için [bkz. Uzaktan Hata Ayıklama.](../debugger/remote-debugging.md)

2. Önceki tabloda gösterildiği gibi, uzaktan hata ayıklayıcı hizmetini hata ayıklayıcı ana bilgisayarına erişen bir hesap altında çalıştırın.

### <a name="to-add-log-on-as-a-service-privilege"></a>"Hizmet olarak oturum aç" ayrıcalığı eklemek için

1. Başlat **menüsünden** Başlat'ı **Denetim Masası.**

2. Bu Denetim Masası, gerekirse **Klasik Görünüm'i** seçin.

3. **Yönetim Araçları**'na çift tıklayın.

4. Yönetimsel Araçlar penceresinde Yerel Güvenlik **İlkesi'ne çift tıklayın.**

5. Yerel Güvenlik **Ayarlar** penceresinde Yerel İlkeler **klasörünü** genişletin.

6. Kullanıcı **Hakları Ataması'ne tıklayın.**

7. İlke **sütununda,** Hizmet  olarak oturum aç iletişim kutusunda geçerli yerel grup ilkesi atamalarını görüntülemek için Hizmet olarak oturum **aç'a** çift tıklayın.

8. Yeni kullanıcı eklemek için Kullanıcı veya **Grup Ekle düğmesine** tıklayın.

9. Kullanıcı eklemeyi bitirdikten sonra Tamam'a **tıklayın.**

### <a name="to-work-around-this-error"></a>Bu hatayla ilgili bir çalışma yapmak için

- Uygulamayı Uzaktan Hata Ayıklama İzleyicisi yerine uygulama olarak çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
