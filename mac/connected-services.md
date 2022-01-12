---
title: Bağlı Hizmetler
description: Azure veri depolama, kimlik doğrulaması ve Mac için Visual Studio içinden bir platformlar arası uygulamaya anında iletme bildirimleri eklemeyi öğrenin.
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/06/2018
ms.topic: how-to
ms.openlocfilehash: a7fe22162901f60aff761c0678c96072296cbf98
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806280"
---
# <a name="connected-services-walkthrough"></a>Bağlı hizmetler izlenecek yolu

bağlı hizmetler iş akışı, Azure portal iş akışını Mac için Visual Studio taşır; bu nedenle, hizmet eklemek için projenizden çıkmak zorunda kalmazsınız.

Bu izlenecek yol, bulut veri depolama, kimlik doğrulama ve platformlar arası bir Xamarin. Forms taşınabilir sınıf kitaplığı (PCL) uygulamasına anında iletme bildirimleri getiren bir Azure arka uç hizmetinin nasıl ekleneceğini gösterir.

1. ' Yi, çözüm içindeki **bağlı hizmetler** düğümüne çift tıklayarak başlatın, bu, **Hizmetler galerisini** getirir.
  Bu, uygulama türü için kullanılabilir tüm hizmetlerin bir listesidir. Üzerine tıklayarak bir hizmet ( **Azure App Service Ile mobil arka uç** gibi) seçin.

    [![Mac için Visual Studio bağlı hizmetler düğümü](media/connected-services-image001-sml.png "Mac için Visual Studio bağlı hizmetler düğümü")](media/connected-services-image001.png#lightbox)

2. Hizmet Ayrıntıları sayfasında, hizmetin açıklaması ve yüklenecek bağımlılıklar bulunur.
  Uygulamaya bağımlılıkları eklemek için **Ekle** düğmesine tıklayın:

    [![Azure ile mobil arka uç](media/connected-services-image002-sml.png "Azure ile mobil arka uç")](media/connected-services-image002.png#lightbox)

3. Bağımlılıkların çalışması için hem PCL hem de platforma özgü projelere eklenmesi gerekir.
  Hizmeti kendisine başvuracak her projeye eklemek için onay kutularını seçin (doğrudan veya dolaylı olarak):

    [![Hizmete başvurması gereken tüm projeleri denetle](media/connected-services-image003-sml.png "Hizmete başvurması gereken tüm projeleri denetle")](media/connected-services-image003.png#lightbox)

4. NuGet paketleri için **lisans kabulü** iletişim kutularında **kabul et** ' i seçin.
  Bir adet, MobileClient ve Dependencies için bir tane olmak üzere iki iletişim kutusu olabilir ve çevrimdışı veri eşitleme için gerekli olan SQLiteStore için bir diğeri:

    [![Lisans sözleşmelerini kabul et](media/connected-services-image004-sml.png "Lisans sözleşmelerini kabul et")](media/connected-services-image004.png#lightbox)

    ![Lisans kabul penceresi](media/connected-services-image005.png "Lisans kabul penceresi")

5. Bağımlılıklar eklendikten sonra, Azure ile iletişim kurmak için kullanmak istediğiniz hesapla oturum açmanız istenir.
  zaten bir Microsoft kimliğiyle oturum açtıysanız Mac için Visual Studio Azure aboneliklerinizi ve bunlarla ilişkili tüm uygulama hizmetlerini getirmeye çalışacaktır. Aboneliğiniz yoksa, ücretsiz deneme için kaydolup veya Azure portal bir abonelik planı satın alarak bir tane ekleyebilirsiniz.

6. Listeden bir App Service seçin. Bu işlem, nesnenin şablon kodunu `MobileServiceClient` Azure üzerinde App Service 'in karşılık gelen URL 'si ile doldurur:

    [![Listeden App Service 'i seçin](media/connected-services-image006-sml.png "Listeden App Service 'i seçin")](media/connected-services-image006.png#lightbox)

    Listelenen hizmetler yoksa, **Yeni** düğmesine tıklayın (bkz. 9. adım)

7. İçin şablon kodunu `MobileServiceClient` PCL 'e kopyalayın. Dosya konumu önemli değildir, bu nedenle yalnızca bir örneği olduğu sürece.
  Önerilen yaklaşım, `AzureService` tüm Azure etkileşimlerini işleyen ve şunları kullanan bir sınıf oluşturmaktır `MobileServiceClient` :

    ![Yapılandırma kodunu AP 'ye kopyalama](media/connected-services-image007.png "Yapılandırma kodunu uygulamaya Kopyala")

8. Uygulamanıza veri, çevrimdışı eşitleme, kimlik doğrulama ve anında iletme bildirimleri eklemek için **sonraki adımlarda** bulunan belgeleri izleyin:

    [![Sonraki adım yönergelerini gözden geçirin](media/connected-services-image008-sml.png "Sonraki adım yönergelerini gözden geçirin")](media/connected-services-image008.png#lightbox)

9. mevcut bir app service yoksa Mac için Visual Studio içinden yeni hizmetler oluşturabilirsiniz.
  **Yeni App Service** iletişim kutusunu açmak için hizmetler listesinin sol alt kısmındaki **Yeni** düğmesine tıklayın:

    [![Mac için Visual Studio yeni bir app service oluşturun](media/connected-services-image009-sml.png "Mac için Visual Studio yeni bir app service oluşturun")](media/connected-services-image009.png#lightbox)

Yeni bir hizmet aşağıdaki parametreleri gerektirir:

- **App Service adı** – plan için benzersiz ad/kimlik
- **Abonelik** : hizmet için ödeme yapmak üzere kullanmak istediğiniz abonelik
- **Kaynak grubu** : bir proje Için tüm Azure kaynaklarınızı bir yol veya düzenleme. Varolanı kullanma veya yeni bir tane oluşturma seçeneği. İlk Azure hizmetiniz bu ise yeni bir tane oluşturun.
- **Hizmet planı** – onu kullanan kaynakların konumunu ve maliyetini belirler. Varolanı kullanma veya yeni bir tane oluşturma seçeneği. İlk Azure hizmetiniz ise, varsayılan olanı kullanın veya ücretsiz katmanda yeni bir tane oluşturun (F1).

Daha fazla bilgi için [Mobile Apps belgelerini](/azure/developer/mobile-apps/azure-mobile-apps/overview) ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [bağlı hizmetler (Windows Visual Studio)](/visualstudio/azure/vs-azure-tools-connected-services-storage)
