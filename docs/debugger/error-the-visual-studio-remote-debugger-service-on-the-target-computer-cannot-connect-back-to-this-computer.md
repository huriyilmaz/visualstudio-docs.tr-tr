---
title: Hata-hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti bu bilgisayara geri bağlanamıyor
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975d2d1c1f66fe06f8fc3a9568f790fbe4c21e36
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460396"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Hata: Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti geriye bu bilgisayara bağlanamıyor
Bu hata, uzaktan hata ayıklayıcı hizmetinin hata ayıklaması yaptığınız bilgisayara bağlanmayı denediğinde kimlik doğrulayamayan bir kullanıcı hesabı altında çalıştığı anlamına gelir. Bu hata, eski hata ayıklama altyapısı kullanılarak uzaktan hata ayıklanırken ve uzaktan hata ayıklayıcı bir hizmet olarak çalışırken oluşabilir.

 Aşağıdaki tabloda, bilgisayara hangi hesapların erişebileceği gösterilmektedir:

|||||
|-|-|-|-|
||LocalSystem hesabı|Etki alanı hesabı|Her iki bilgisayarda da aynı Kullanıcı adı ve parolaya sahip yerel hesaplar|
|Aynı etki alanındaki her iki bilgisayar|Yes|Yes|Yes|
|İki yönlü güvene sahip etki alanlarındaki her iki bilgisayar|Hayır|Hayır|Evet|
|Bir çalışma grubundaki bilgisayarlardan biri veya her ikisi|Hayır|Hayır|Evet|
|Farklı etki alanlarındaki bilgisayarlar|Hayır|Hayır|Evet|

 Bunlara ek olarak:

- Visual Studio Uzaktan Hata Ayıklayıcı hizmetini çalıştırdığınız hesabın, uzak bilgisayarda bir yönetici olması gerekir, böylece herhangi bir işlemde hata ayıklayabilirler.

- Ayrıca hesaba, `Log on as a service` **yerel güvenlik ilkesi** yönetim aracını kullanan uzak bilgisayarda ayrıcalık verilmelidir.

- Bilgisayara erişim yerel bir hesap kullanıyorsanız, Visual Studio Uzaktan Hata Ayıklayıcı hizmetini yerel bir hesap altında çalıştırmanız gerekir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Visual Studio Uzaktan Hata Ayıklayıcı hizmetinin uzak bilgisayarda doğru şekilde ayarlandığından emin olun. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

2. Uzaktan hata ayıklayıcı hizmetini, önceki tabloda gösterildiği gibi, hata ayıklayıcı ana bilgisayarına erişebilen bir hesap altında çalıştırın.

### <a name="to-add-log-on-as-a-service-privilege"></a>"Hizmet olarak oturum aç" ayrıcalığı eklemek için

1. **Başlat** menüsünde, **Denetim Masası**' nı seçin.

2. Denetim Masası 'nda, gerekirse **Klasik Görünüm**' ü seçin.

3. **Yönetim Araçları**'na çift tıklayın.

4. Yönetimsel Araçlar penceresinde **yerel güvenlik ilkesi**' ne çift tıklayın.

5. **Yerel güvenlik ayarları** penceresinde, **Yerel ilkeler** klasörünü genişletin.

6. **Kullanıcı hakları ataması**' na tıklayın.

7. **İlke** sütununda **, hizmet olarak oturum aç iletişim kutusunda** geçerli yerel Grup İlkesi atamalarını görüntülemek için **hizmet olarak oturum** aç ' a çift tıklayın.

8. Yeni kullanıcılar eklemek için **Kullanıcı veya Grup Ekle** düğmesine tıklayın.

9. Kullanıcı ekleme işiniz bittiğinde **Tamam**' a tıklayın.

### <a name="to-work-around-this-error"></a>Bu hatayı geçici olarak çözmek için

- Uzaktan Hata Ayıklama İzleyicisi bir hizmet yerine uygulama olarak çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama Hataları ve Sorun Giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)