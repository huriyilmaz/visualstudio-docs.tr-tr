---
title: 'Hata: hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti bu bilgisayara geri bağlanamıyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a7de83f118b38d9a3c71f1c7e7febf48e0f5bc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520516"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Hata: Hedef bilgisayardaki Visual Studio Uzaktan Hata Ayıklayıcı hizmeti geriye bu bilgisayara bağlanamıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata, Visual Studio Uzaktan Hata Ayıklayıcı hizmetin, hata ayıklaması yaptığınız bilgisayara bağlanmayı denediğinde kimlik doğrulayamayan bir kullanıcı hesabı altında çalıştığı anlamına gelir.  
  
 Aşağıdaki tabloda, bilgisayara hangi hesapların erişebileceği gösterilmektedir:  
  
|Senaryo|LocalSystem hesabı|Etki alanı hesabı|Her iki bilgisayarda da aynı Kullanıcı adı ve parolaya sahip yerel hesaplar|  
|-|-|-|-|-|  
|Aynı etki alanındaki her iki bilgisayar|Yes|Yes|Yes|  
|İki yönlü güvene sahip etki alanlarındaki her iki bilgisayar|Hayır|Hayır|Evet|  
|Bir çalışma grubundaki bilgisayarlardan biri veya her ikisi|Hayır|Hayır|Evet|  
|Farklı etki alanlarındaki bilgisayarlar|Hayır|Hayır|Evet|  
  
 Bunlara ek olarak:  
  
- Visual Studio Uzaktan Hata Ayıklayıcı hizmetini çalıştırdığınız hesabın, uzak bilgisayarda bir yönetici olması gerekir, böylece herhangi bir işlemde hata ayıklayabilirler.  
  
- Ayrıca hesaba, `Log on as a service` **yerel güvenlik ilkesi** yönetim aracını kullanan uzak bilgisayarda ayrıcalık verilmelidir.  
  
- Bilgisayara erişim yerel bir hesap kullanıyorsanız, Visual Studio Uzaktan Hata Ayıklayıcı hizmetini yerel bir hesap altında çalıştırmanız gerekir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Visual Studio Uzaktan Hata Ayıklayıcı hizmetinin uzak bilgisayarda doğru şekilde ayarlandığından emin olun. Daha fazla bilgi için bkz. [cihazdaki uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uzaktan hata ayıklama hataları ve sorun giderme](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
