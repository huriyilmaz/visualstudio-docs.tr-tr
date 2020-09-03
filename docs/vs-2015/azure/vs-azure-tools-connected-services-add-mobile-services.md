---
title: Bağlı hizmetleri kullanarak Mobile Services ekleme
description: Visual Studio bağlı hizmetler Ekle iletişim kutusunu kullanarak Mobile Services ekleme
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
ms.openlocfilehash: 0a8f6fab3c8f30834a467e2ad98843b16a9245b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916705"
---
# <a name="adding-mobile-services-by-using-visual-studio-connected-services"></a>Visual Studio bağlı hizmetlerini kullanarak Mobile Services ekleme
Visual Studio 2015 ile Azure Mobile Services **bağlı hizmet ekle** iletişim kutusunu kullanarak bağlanabilirsiniz. Herhangi bir C# istemci uygulamasından, herhangi bir JavaScript uygulamasına veya platformlar arası Cordova uygulamasına bağlanabilirsiniz. Bağlandıktan sonra, veri oluşturabilir ve erişebilir, özel API 'Ler ve zamanlanan işler oluşturabilir veya anında iletme bildirimleri için destek ekleyebilirsiniz.  Bağlı hizmetler işlemi, tüm uygun başvuruları ve bağlantı kodunu ekler. Ayrıca, Azure AD, Facebook, Twitter ve Microsoft hesapları gibi çeşitli popüler kimlik şemaları ile kimlik doğrulama için yerleşik destek avantajlarından yararlanabilirsiniz.

## <a name="supported-project-types"></a>Desteklenen proje türleri
> [!NOTE]
> Visual Studio 2015 ' de, bağlı hizmetler Ekle iletişim kutusunu kullanarak bir Windows Evrensel (Windows 10) projelerine Azure Mobile Services ekleme desteklenmez. Projeniz için NuGet Paket Yöneticisi 'Ni kullanarak uygun paketleri yükleyerek Azure Mobile Services 'yi ekleyebilirsiniz.
>
>

Aşağıdaki proje türlerinde Azure Mobile Services bağlanmak için bağlı hizmetler iletişim kutusunu kullanabilirsiniz.

* .NET Windows 8.1 Mağazası, telefon ve evrensel uygulama projeleri
* JavaScript Windows 8.1 depolama, telefon ve evrensel uygulama projeleri
* Apache Cordova için Visual Studio Araçları kullanılarak oluşturulan projeler

## <a name="connect-to-azure-mobile-services-using-the-add-connected-services-dialog"></a>Bağlı hizmetler Ekle iletişim kutusunu kullanarak Azure Mobile Services bağlanma
1. Azure hesabınız olduğundan emin olun. Bir Azure hesabınız yoksa, [ücretsiz deneme](https://azure.microsoft.com/pricing/free-trial/)için kaydolabilirsiniz.
2. **Bağlı hizmetler Ekle** iletişim kutusunu açın.

   * .NET uygulamaları için projenizi Visual Studio 'da açın, Çözüm Gezgini ' deki **Başvurular** düğümünün bağlam menüsünü açın ve **bağlı hizmet ekle** ' yi seçin.

        ![Azure Mobile Service 'e bağlanılıyor](./media/vs-azure-tools-connected-services-add-mobile-services/IC797635.png)
   * Apache Cordova uygulama projeleri için projenizi Visual Studio 'da açın, Çözüm Gezgini içindeki proje düğümünün bağlam menüsünü açın ve **bağlı hizmet ekle**' yi seçin.
3. **Bağlı hizmet ekle** Iletişim kutusunda **Azure Mobile Services**' u ve ardından **Yapılandır** düğmesini seçin. Henüz yapmadıysanız Azure 'da oturum açmanız istenebilir.

    ![Azure mobil hizmeti ekleme](./media/vs-azure-tools-connected-services-add-mobile-services/IC797636.png)
4. **Azure Mobile Services** iletişim kutusunda, varsa, var olan bir mobil hizmeti seçin. Yeni bir Azure Mobil Hizmeti oluşturmanız gerekiyorsa, bunu yapmak için aşağıdaki yordamı izleyin. Aksi halde, bir sonraki numaralı adıma geçin.

    Yeni bir mobil hizmet hesabı oluşturmak için:

   1. İletişim kutusunun alt kısmındaki **hizmet oluştur** bağlantısını seçin.
       ![Yeni mobil bağlı hizmet ekle](./media/vs-azure-tools-connected-services-add-mobile-services/IC797637.png)
   2. **Mobil hizmet oluştur** iletişim kutusunda, **çalışma zamanı** açılır listesinden bir JavaScript arka uç mobil hizmeti veya bir .net arka uç mobil hizmeti seçebilirsiniz.

       ![Mobil hizmet oluşturma](./media/vs-azure-tools-connected-services-add-mobile-services/IC797638.png)

       JavaScript arka uç hizmeti basit ve güçlü bir işlemdir. Bir JavaScript arka uç mobil hizmeti oluşturursanız, sunucu tarafı JavaScript kodu bulutta depolanır, ancak Sunucu Gezgini veya Azure Yönetim Portalı ' nı kullanarak sunucu betikleri düzenleyebilirsiniz.

       .NET arka uç Mobil Hizmeti, Web API 'SI ve Entity Framework için tam güç ve esneklik sağlar. Bir .NET arka uç mobil hizmeti oluşturursanız, sizin için bir proje oluşturulur ve çözümünüze eklenir.
   3. Mobil Hizmeti istediğiniz **bölgeyi** seçin ve ardından sunucu için bir Kullanıcı adı ve parola girin.
   4. Gerekli tüm bilgileri girdikten sonra, mobil hizmeti oluşturmak için **Oluştur** düğmesini seçin.
   5. Yeni mobil hizmet **Azure Mobile Services** iletişim kutusundaki hizmet listesinde görünmelidir. Listeden yeni mobil hizmeti seçin ve ardından hizmeti projenize eklemek için **Ekle** düğmesini seçin.
5. Görüntülenen Başlarken sayfasını gözden geçirin ve projenizin nasıl değiştirildiğini öğrenin. Her bağlı hizmet eklediğinizde tarayıcınızda Başlarken sayfası görüntülenir. Önerilen sonraki adımları ve kod örneklerini gözden geçirebilir veya projenize hangi başvuruların eklendiğini ve kod ve yapılandırma dosyalarınızın nasıl değiştirildiğini görmek için ne oldu sayfasına geçiş yapabilirsiniz.
6. Kod örneklerini kılavuz olarak kullanarak, mobil hizmetinize erişmek için kod yazmaya başlayın!

## <a name="next-steps"></a>Sonraki adımlar
Soru sorun ve yardım alın:

* [MSDN Forumu: Azure Mobile Services](https://social.msdn.microsoft.com/forums/azure/home?forum=azuremobile)
* [Azure Mobile Services Microsoft Azure ekibi blogundan](https://azure.microsoft.com/blog/topics/mobile/)
* [Azure.microsoft.com adresinde Azure Mobile Services](https://azure.microsoft.com/services/mobile-services/)
* [Azure.microsoft.com adresinde Azure Mobile Services belgeleri](https://azure.microsoft.com/documentation/services/mobile-services/)
