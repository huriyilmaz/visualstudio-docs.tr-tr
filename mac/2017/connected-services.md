---
title: Bağlı Hizmetler
description: Mac için Visual Studio'nun içinden mobil uygulamalara Azure veri depolama, kimlik doğrulama ve anında iletme bildirimleri ekleme
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/06/2018
ms.openlocfilehash: 241820de009a5118869583bbe228ecb0604f9001
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985294"
---
# <a name="connected-services-walkthrough"></a>Bağlı Hizmetler walkthrough

Bağlı Hizmetler iş akışı, Azure portalı iş akışını Mac için Visual Studio'ya getirir, böylece hizmet eklemek için projenizden ayrılmak zorunda kalmamanız gerekir.

Bu gözden geçirme, bulut veri depolama, kimlik doğrulama ve anında iletme bildirimlerini bir çapraz platform Xamarin.Forms Taşınabilir Sınıf Kitaplığı (PCL) uygulamasına getiren bir Azure arka uç hizmetinin nasıl ekleyeceğini gösterir.

1. **Hizmetler Galerisi'ni**oluşturan çözümdeki **Bağlı Hizmetler** düğümüne çift tıklayarak başlayın.
  Bu, uygulama türü için kullanılabilir tüm hizmetlerin listesidir. Üzerine tıklayarak bir hizmeti **(Azure Uygulama Hizmeti ile Mobil arka uç**gibi) seçin.

    [![Mac için Visual Studio'da Bağlantılı Hizmetler düğümü](media/connected-services-image001-sml.png "Mac için Visual Studio'da Bağlantılı Hizmetler düğümü")](media/connected-services-image001.png#lightbox)

2. Hizmet Ayrıntıları Sayfası, hizmetin ve yüklenecek bağımlılıkların bir açıklamasına sahiptir.
  Uygulamalara bağımlılıkları eklemek için **Ekle** düğmesini tıklatın:

    [![Azure ile mobil arka uç](media/connected-services-image002-sml.png "Azure ile mobil arka uç")](media/connected-services-image002.png#lightbox)

3. Bağımlılıkların hem PCL'ye hem de çalışacak platforma özel projelere eklenmesi gerekir.
  Hizmeti başvurulacak her projeye (doğrudan veya dolaylı olarak) eklemek için onay kutularını seçin:

    [![Hizmete başvurması gereken tüm projeleri denetleme](media/connected-services-image003-sml.png "Hizmete başvurması gereken tüm projeleri denetleme")](media/connected-services-image003.png#lightbox)

4. NuGet paketleri için **Lisans Kabul** iletişim kutularında **Kabul et'i** seçin.
  Kabul edilecek iki iletişim kutusu olabilir: biri MobileClient ve bağımlılıklar için, diğeri de çevrimdışı veri eşitlemesi için gerekli olan SQLiteStore için:

    [![Lisans Sözleşmelerini Kabul Et](media/connected-services-image004-sml.png "Lisans Sözleşmelerini Kabul Et")](media/connected-services-image004.png#lightbox)

    ![Lisans Kabul penceresi](media/connected-services-image005.png "Lisans Kabul penceresi")

5. Bağımlılıklar eklendikten sonra, Azure ile iletişim kurmak için kullanmak istediğiniz hesapla oturum açmanız istenir.
  Zaten bir Microsoft Kimliğiyle oturum açtıysanız, Mac için Visual Studio Azure aboneliklerinizi ve bunlarla ilişkili tüm uygulama hizmetlerini almaya çalışır. Herhangi bir aboneliğiniz yoksa, ücretsiz deneme sürümüne kaydolarak veya Azure portalında bir abonelik planı satın alarak bir abonelik ekleyebilirsiniz.

6. Listeden bir uygulama hizmeti seçin. Bu, nesnenin `MobileServiceClient` şablon kodunu Azure'daki uygulama hizmetinin ilgili URL'si ile doldurur:

    [![Listeden uygulama hizmetini seçin](media/connected-services-image006-sml.png "Listeden uygulama hizmetini seçin")](media/connected-services-image006.png#lightbox)

    Listede hizmet yoksa, **Yeni** düğmesini tıklatın (Bkz. Adım 9.)

7. Şablon kodunu `MobileServiceClient` PCL'ye kopyalayın. Dosya konumu önemli değildir, ancak bunun yalnızca bir örneği olduğu sürece.
  Önerilen yaklaşım, tüm `AzureService` Azure etkileşimlerini işleyen ve `MobileServiceClient`aşağıdakileri kullanan bir sınıf oluşturmaktır:

    ![Config kodunu ap'ye kopyala](media/connected-services-image007.png "Config kodunu uygulamaya kopyalama")

8. Uygulamanıza veri, çevrimdışı eşitleme, kimlik doğrulama ve anında iletme bildirimleri eklemek için **Sonraki Adımlar'daki** belgeleri izleyin:

    [![Sonraki adımları yönergeleri gözden geçirin](media/connected-services-image008-sml.png "Sonraki adımları yönergeleri gözden geçirin")](media/connected-services-image008.png#lightbox)

9. Mevcut uygulama hizmetleriniz yoksa, Mac için Visual Studio içinden yeni hizmetler oluşturabilirsiniz.
  **Yeni Uygulama Hizmeti** iletişim kutusunu açmak için hizmetler listesinin sol alt kısmındaki **Yeni** düğmesini tıklatın:

    [![Mac için Visual Studio'da yeni bir uygulama hizmeti oluşturun](media/connected-services-image009-sml.png "Mac için Visual Studio'da yeni bir uygulama hizmeti oluşturun")](media/connected-services-image009.png#lightbox)

Yeni bir hizmet aşağıdaki parametreleri gerektirir:

- **Uygulama hizmet adı** – plan için benzersiz ad/kimlik
- **Abonelik** – hizmet için ödemek için kullanmak istediğiniz abonelik
- **Kaynak Grubu** – bir proje için tüm Azure kaynaklarınızı düzenlemenin bir yolu veya organizasyonu. Varolan veya yeni bir tane oluşturma seçeneği. Bu ilk Azure hizmetinizse, yeni bir hizmet oluşturun.
- **Hizmet Planı** – Onu kullanan kaynakların konumunu ve maliyetini belirler. Varolan veya yeni bir tane oluşturma seçeneği. Bu ilk Azure hizmetinizse, varsayılan hizmeti kullanın veya boş katmanda (F1) yeni bir hizmet oluşturun.

Daha fazla bilgi için [Mobil uygulamalar belgelerini](/azure/app-service-mobile/) ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantılı Hizmetler (Windows'ta Visual Studio)](/visualstudio/azure/vs-azure-tools-connected-services-storage)