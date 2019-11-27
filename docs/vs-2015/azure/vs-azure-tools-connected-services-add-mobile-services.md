---
title: Bağlı hizmetler kullanarak mobil hizmet ekleme
description: Visual Studio bağlı Hizmetleri Ekle iletişim kutusunu kullanarak mobil hizmetler ekleyin
documentationcenter: na
author: ghogen
manager: jillfra
ms.assetid: 75c3cb93-88e1-476d-a416-f34caa3608e3
ms.topic: conceptual
ms.workload: azure-vs
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.date: 12/16/2015
ms.author: mlearned
ms.openlocfilehash: 4f84970daea03904d4642317cf6097beb07be7f1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300179"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Visual Studio bağlı Hizmetler'i kullanarak mobil hizmet ekleme
Visual Studio 2015 ile Azure Mobile Services **bağlı hizmet ekle** iletişim kutusunu kullanarak bağlanabilirsiniz. Tüm C# istemci uygulamalarından, tüm JavaScript uygulaması veya platformlar arası Cordova uygulaması bağlanabilirsiniz. Bağlandıktan sonra oluşturma ve verilere erişmek, özel API'ler ve zamanlanan işler oluşturabilir veya anında iletme bildirimleri için destek eklendi.  Bağlı hizmetler işlemi, tüm uygun başvuruları ve bağlantı kodunu ekler. Çeşitli Azure AD gibi popüler kimlik şemaları ile kimlik doğrulaması için yerleşik destek avantajından da sürebilir Facebook, Twitter ve Microsoft Accounts.

## <a name="supported-project-types"></a>Desteklenen proje türleri
> [!NOTE]
> Visual Studio 2015'te, bağlı hizmet Ekle iletişim kutusunu kullanarak bir Windows Evrensel (Windows 10) projeleri için Azure Mobile Services eklenmesi desteklenmiyor. Projeniz için NuGet Paket Yöneticisi'ni kullanarak uygun paketlerini yükleyerek Azure mobil hizmetler ekleyebilirsiniz.
>
>

Aşağıdaki proje türlerini Azure mobil Hizmetler'e bağlanmak için bağlı hizmetler iletişim kutusunu kullanabilirsiniz.

* .NET Windows 8.1 Store, telefon ve evrensel uygulama projeleri
* JavaScript Windows 8.1 Store, telefon ve evrensel uygulama projeleri
* Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan projeler

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Bağlı hizmet Ekle iletişim kutusunu kullanarak Azure mobil Hizmetleri'ne için Bağlan
1. Bir Azure hesabı olduğundan emin olun. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://go.microsoft.com/fwlink/?LinkId=518146)için kaydolabilirsiniz.
2. **Bağlı hizmetler Ekle** iletişim kutusunu açın.

   * .NET uygulamaları için projenizi Visual Studio 'da açın, Çözüm Gezgini ' deki **Başvurular** düğümünün bağlam menüsünü açın ve **bağlı hizmet ekle** ' yi seçin.

        ![Azure mobil hizmetinize bağlanma](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova uygulama projeleri için projenizi Visual Studio 'da açın, Çözüm Gezgini içindeki proje düğümünün bağlam menüsünü açın ve **bağlı hizmet ekle**' yi seçin.
3. **Bağlı hizmet ekle** Iletişim kutusunda **Azure Mobile Services**' u ve ardından **Yapılandır** düğmesini seçin. Zaten yapmadıysanız, Azure'a bağlanmanız istenebilir.

    ![Bir Azure mobil hizmet ekleme](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. **Azure Mobile Services** iletişim kutusunda, varsa, var olan bir mobil hizmeti seçin. Yeni bir Azure mobil hizmet oluşturmak ihtiyacınız varsa, bunu yapmak için aşağıdaki yordamı izleyin. Aksi halde, bir sonraki numaralı adıma geçin.

    Yeni bir mobil hizmet hesabı oluşturmak için:

   1. İletişim kutusunun alt kısmındaki **hizmet oluştur** bağlantısını seçin.
       Yeni mobil bağlı hizmet](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png) eklemek ![
   2. **Mobil hizmet oluştur** iletişim kutusunda, **çalışma zamanı** açılır listesinden bir JavaScript arka uç mobil hizmeti veya bir .net arka uç mobil hizmeti seçebilirsiniz.

       ![Bir mobil hizmet oluşturma](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       Basit ve güçlü bir JavaScript arka uç hizmeti. JavaScript arka uç mobil hizmet oluşturma, sunucu tarafı JavaScript kodu bulutta depolanır, ancak Sunucu Gezgini veya Azure Yönetim Portalı'nı kullanarak sunucu komut dosyalarını düzenleyebilirsiniz.

       Bir .NET arka uç mobil hizmetlerini tam gücü ve Entity Framework ile Web API ve esnekliği sunar. Bir .NET arka uç mobil hizmetlerini oluşturursanız, bir projesi için oluşturduğunuz ve çözümünüze eklenir.
   3. Mobil Hizmeti istediğiniz **bölgeyi** seçin ve ardından sunucu için bir Kullanıcı adı ve parola girin.
   4. Gerekli tüm bilgileri girdikten sonra, mobil hizmeti oluşturmak için **Oluştur** düğmesini seçin.
   5. Yeni mobil hizmet **Azure Mobile Services** iletişim kutusundaki hizmet listesinde görünmelidir. Listeden yeni mobil hizmeti seçin ve ardından hizmeti projenize eklemek için **Ekle** düğmesini seçin.
5. Açılan başlangıç sayfasını inceleyin ve projenizin nasıl değiştirildiğini öğrenin. Bir bağlı hizmet ekleyişinizde tarayıcınızda bir Başlarken sayfası görüntülenir. Önerilen sonraki adımları ve kod örneklerini inceleyebilir veya projenize hangi başvuruların eklendi ve kod ve yapılandırma dosyalarınızın nasıl değiştirilmiş görmek için olanlar sayfasına geçebilirsiniz.
6. Kod örneklerini kılavuz olarak kullanarak, mobil hizmetinize erişmek için kod yazmaya başlayın!

## <a name="how-your-project-is-modified"></a>Projenizi nasıl değiştirilir
Visual Studio'nun projenizi nasıl değiştirdiğini, proje türüne göre değişir. İstemci C# uygulamaları için bkz. [ne oldu – C# projeler](https://go.microsoft.com/fwlink/p/?LinkId=513119). JavaScript istemci uygulamaları için bkz. [ne oldu – JavaScript projeleri](https://go.microsoft.com/fwlink/p/?LinkId=513120). Cordova uygulamaları için bkz. [ne oldu – Cordova projeleri](https://go.microsoft.com/fwlink/p/?LinkId=513116).

## <a name="next-steps"></a>Sonraki adımlar
Soru sorun ve Yardım alın:

* [MSDN Forumu: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services Microsoft Azure ekibi blogundan](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com adresinde Azure Mobile Services](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com adresinde Azure Mobile Services belgeleri](https://azure.microsoft.com/documentation/services/mobile-services/)
