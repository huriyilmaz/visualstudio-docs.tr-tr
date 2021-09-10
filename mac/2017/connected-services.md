---
title: Bağlı Hizmetler
description: Azure veri depolama, kimlik doğrulaması ve anında doğrulama bildirimlerini mobil uygulamalara uygulamanın Mac için Visual Studio
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2018
ms.openlocfilehash: b33b6d3f0865ca338512f744f5b924ae2992179a
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962052"
---
# <a name="connected-services-walkthrough"></a>Bağlı Hizmetler için izlenecek yol

Bağlı Hizmetler iş akışı Azure portal iş akışını Mac için Visual Studio, bu nedenle hizmetleri eklemek için projenizi bırakmak zorunda değilsiniz.

Bu kılavuzda, platformlar arası Xamarin.Forms Taşınabilir Sınıf Kitaplığı (PCL) uygulamasına bulut veri depolama, kimlik doğrulaması ve anında bildirim getiren bir Azure arka uç hizmetinin nasıl ekli olduğu açıklanır.

1. Başlangıç olarak çözümdeki **Bağlı Hizmetler düğümüne** çift tıklayarak başlayabilirsiniz. Bu, Hizmet **Galerisi'ni getirir.**
  Bu, uygulama türü için kullanılabilir tüm hizmetlerin listesidir. Üzerine tıklayarak bir hizmet seçin (örneğin, **Azure App Service** mobil arka uç) .

    [![Mac için Visual Studio'de Bağlı Hizmetler düğümü](media/connected-services-image001-sml.png "Mac için Visual Studio'de Bağlı Hizmetler düğümü")](media/connected-services-image001.png#lightbox)

2. Hizmet Ayrıntıları Sayfasında, hizmetin açıklaması ve yüklenme bağımlılıkları vardır.
  Bağımlılıkları  uygulamaya eklemek için Ekle düğmesine tıklayın:

    [![Azure ile mobil arka uç](media/connected-services-image002-sml.png "Azure ile mobil arka uç")](media/connected-services-image002.png#lightbox)

3. Bağımlılıkların çalışması için hem PCL'ye hem de platforma özgü projelere ekleniyor olması gerekir.
  Hizmete başvuracak her projeye (doğrudan veya dolaylı olarak) eklemek için onay kutularını seçin:

    [![Hizmete başvuracak tüm projeleri denetleme](media/connected-services-image003-sml.png "Hizmete başvuracak tüm projeleri denetleme")](media/connected-services-image003.png#lightbox)

4. Uygulama **paketleri** için **Lisans Kabulü iletişim** NuGet seçin.
  Kabul edilecek iki iletişim kutusu olabilir: biri MobileClient ve bağımlılıklar için, diğeri de çevrimdışı veri eşitlemesi için gereken SQLiteStore için:

    [![Lisans Sözleşmelerini Kabul Etme](media/connected-services-image004-sml.png "Lisans Sözleşmelerini Kabul Etme")](media/connected-services-image004.png#lightbox)

    ![Lisans Kabulü penceresi](media/connected-services-image005.png "Lisans Kabulü penceresi")

5. Bağımlılıklar eklendiktan sonra, Azure ile iletişim kurmak için kullanmak istediğiniz hesapta oturum açmanız isteniyor.
  Zaten bir Microsoft kimliğiyle oturum açtıysanız Mac için Visual Studio Azure aboneliklerinizi ve onlarla ilişkili tüm uygulama hizmetlerini getirmeye çalışabilirsiniz. Aboneliğiniz yoksa, ücretsiz deneme sürümüne kaydolarak veya abonelik planı satın alarak abonelik planı Azure portal.

6. Listeden bir uygulama hizmeti seçin. Bu işlem, nesnenin şablon kodunu `MobileServiceClient` Azure'da uygulama hizmetinin ilgili URL'si ile doldurur:

    [![Listeden app service seçme](media/connected-services-image006-sml.png "Listeden app service seçme")](media/connected-services-image006.png#lightbox)

    Listede hizmet yoksa Yeni düğmesine tıklayın **(bkz.** 9. Adım).)

7. için şablon kodunu `MobileServiceClient` PCL'ye kopyalayın. Dosyanın yalnızca bir örneği olduğu sürece dosya konumu önemli değildir.
  Önerilen yaklaşım, tüm `AzureService` Azure etkileşimlerini ele alan ve kullanan bir sınıf oluşturmaktır: `MobileServiceClient`

    ![Yapılandırma kodunu ap'ye kopyalama](media/connected-services-image007.png "Yapılandırma kodunu uygulamaya kopyalama")

8. Uygulamanıza **veri, çevrimdışı eşitleme,** kimlik doğrulaması ve anında bildirim eklemek için Sonraki Adımlar'daki belgeleri izleyin:

    [![Sonraki adım yönergelerini gözden geçirme](media/connected-services-image008-sml.png "Sonraki adım yönergelerini gözden geçirme")](media/connected-services-image008.png#lightbox)

9. Mevcut uygulama hizmetleriniz yoksa, uygulama hizmetlerinden yeni hizmetler Mac için Visual Studio.
  Hizmetler **listesinin** sol alt kısmında bulunan Yeni düğmesine tıklayarak Yeni hizmetler **iletişim App Service** açın:

    [![Mac için Visual Studio'de yeni bir uygulama Mac için Visual Studio](media/connected-services-image009-sml.png "Mac için Visual Studio'de yeni bir uygulama hizmeti oluşturma")](media/connected-services-image009.png#lightbox)

Yeni bir hizmet için aşağıdaki parametreler gerekir:

- **App Service adı** – plan için benzersiz ad/kimlik
- **Abonelik** – hizmet için ödeme yapmak istediğiniz abonelik
- **Kaynak Grubu:** Bir proje için tüm Azure kaynaklarınızı düzenleme veya düzenleme yolu. Mevcut bir tane kullanma veya yeni bir tane oluşturma seçeneği. İlk Azure hizmetiniz bu ise yeni bir tane oluşturun.
- **Hizmet Planı–** Bunu kullanan kaynakların konumunu ve maliyetini belirler. Mevcut bir tane kullanma veya yeni bir tane oluşturma seçeneği. İlk Azure hizmetiniz bu ise varsayılan hizmeti kullanın veya ücretsiz katmanda (F1) yeni bir tane oluşturun.

Daha fazla [bilgi için Mobil uygulamalar](/azure/developer/mobile-apps/azure-mobile-apps/overview) belgelerini ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlı Hizmetler (Visual Studio Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)
