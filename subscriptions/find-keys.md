---
title: Visual Studio aboneliklerinde ürün anahtarlarını bulma ve talep etme | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 03/09/2020
ms.topic: conceptual
description: Visual Studio aboneliklerinde ürün anahtarlarını nasıl bulabileceğinizi, talep edin ve dışa aktarabileceğinizi öğrenin
ms.openlocfilehash: 3946388669533a59176dc79cd72f238994a0a01b
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232494"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde ürün anahtarlarını bulma ve talep etme
Bu makalede, ürün anahtarlarının nasıl bulunup, talep tevecbine nasıl geçilen https://my.visualstudio.com/productkeysve dışa aktarılabilen ler açıklanmaktadır.  Anahtarların anahtar, perakende ve toplu lisans sürümleri ve günlük ürün anahtarı talep limitleri ile bir ürünü etkinleştirme hakkında daha fazla bilgi için lütfen [ürün anahtarlarına genel bakışı](product-keys.md)ziyaret edin.

## <a name="locating-and-claiming-product-keys"></a>Ürün anahtarlarını bulma ve talep etme
Ürün anahtarlarınızı görüntülemek için Visual Studio aboneliğinizde oturum açmış olmalısınız. Tek tek ürün anahtarları, aşağıda gösterildiği gibi [İndirilenler](https://my.visualstudio.com/downloads) sayfasında belirli bir ürünün mavi **Get Key** bağlantısını seçerek bulunur.  Tüm anahtarlar [Ürün Anahtarları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sayfasında toplu olarak da mevcuttur. Tek bir ürün için birden çok anahtar bulunduğunda, hangi anahtarın kullanılması gerektiğini belirlemenize yardımcı olmak için indirme için Notlar sütununda notlar görüntülenir.
> [!div class="mx-imgBorder"]
> ![İndirme Sayfasından Anahtar Al](_img/product-keys/download-get-key.png)

Bazı ürünler, ürünün birden çok sürümünü tek bir indirmede paketler. Bu gibi durumlarda, girilen ürün anahtarı ürünün hangi sürümünün yüklü olduğunu belirler.
Etkinleştirme gerekli olmadığı için gerektiğinden gerektiği kadar kullanabileceğiniz "statik" tuşlar gibi bazı anahtarlar otomatik olarak sağlanır. Diğer anahtarlar, ürünün **Anahtar Al** bağlantısını seçerek talep edilmelidir.

Ürüne bağlı olarak çeşitli anahtar türleri mevcuttur.

### <a name="product-key-types"></a>Ürün anahtar türleri

|    Anahtar Türü           |    Açıklama                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Geçerli değil                    |    Bu ürünü yüklemek için anahtar gerekmez.                                                       |
|    Perakende                     |    Perakende anahtarları birden çok etkinleştirmeye izin verir ve ürünün perakende yapılarında kullanılır. Çoğu durumda, anahtar başına 10 etkinleştirmeye izin verilir, ancak genellikle aynı makinede daha fazla etkinleştirme izin verilir.                                                       |
|    Çoklu Etkinleştirme        |    Çoklu Etkinleştirme Anahtarı (MAK), aynı anahtara sahip bir ürünün birden çok kurulumunu etkinleştirmenizi sağlar. MAK'lar genellikle ürünlerin Toplu Lisanslama sürümlerinde kullanılır. Genellikle, abonelik başına yalnızca bir MAK anahtarı sağlanır.    |
|    Statik Aktivasyon Anahtarı    |    Etkinleştirme gerektirmeyen ürünler için statik etkinleştirme anahtarları sağlanır. Bunlar herhangi bir sayıda kurulum için kullanılabilir.                                                                                                                  |
|    Özel Anahtar                 |    Özel anahtarlar, ürünü etkinleştirmek veya yüklemek için özel eylemler veya bilgiler sağlar.                                                                                                                                                                |
|    VA 1.0                     |    Bunlar mak'a benzer çoklu etkinleştirme anahtarlarıdır.                                                                                                                                                                                                 |
|    OEM Anahtarı                    |    Bunlar, birden çok etkinleştirmeye izin veren Orijinal Ekipman Üreticisi anahtarlarıdır.                                                                                                                                                                       |
|    DreamSpark Perakende Anahtar    |    Bu perakende anahtarları DreamSpark içindir ve bir aktivasyon sağlar. DreamSpark Perakende anahtarları toplu olarak verilir ve öncelikle öğrenci tüketimi için tasarlanmıştır.                                                                                     |
|    DreamSpark Laboratuvar Anahtarı         |    Bu laboratuvar kullanım anahtarları DreamSpark programları içindir ve birden çok etkinleştirme sağlar. DreamSpark Lab Keys üniversite bilgisayar laboratuvarı senaryolarında kullanılmak üzere tasarlanmıştır.                                                                                       |
|    DreamSpark MAK Anahtar         |    Bunlar DreamSpark programı müşterileri için MAK tuşlarıdır.                                                                                                                                                                                                  |
|

Ürünün indirme sayfasından bir anahtar talep edebilir veya [Ürün Anahtarları](https://my.visualstudio.com/productkeys) sayfasında ihtiyacınız olan anahtarı arayabilirsiniz.

### <a name="claiming-product-keys"></a>Ürün anahtarlarını talep etme
Yalnızca etkin aboneliği olan aboneler ürün indirebilir ve ürün anahtarlarını talep edebilir.  Aboneliğiniz etkinken talep ettiğiniz anahtarları [Ürün Anahtarları](https://my.visualstudio.com/productkeys) sayfasından dışa aktarabilirsiniz.

Ürün anahtarı nı talep etmek için:
1. Visual Studio aboneliğinizde oturum açın.  Ürünleri indirmek veya ürün anahtarlarını talep etmek için oturum açmış olmalısınız.
2. [Ürün Tuşları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sekmesine tıklayın.
3. Ürün anahtarları alfabetik olarak ürünün adına göre listelenir.  İstenilen ürünün adına doğru ilerleyebilir veya sayfanın üst kısmındaki arama çubuğunu kullanarak onu arayabilirsiniz.
> [!div class="mx-imgBorder"]
> ![Ürün Anahtarı Ara](_img/product-keys/search-keys.png)
   
Bu örnekte, Visual Studio Enterprise 2019 için bir ürün anahtarı bulmak için arama çubuğunu kullandık.
Gördüğünüz gibi, listelenen birkaç sürümü vardır.  Visual Studio Enterprise 2019 sürümleri 16.0 ve 16.1 için birer anahtar zaten talep edilmiştir.  Her iki sürüm için de farklı türde ek anahtarlar kullanılabilir. **Notlar** sütununa talep edilen anahtarlar hakkında kısa bir not kaydedebilirsiniz dikkat edin.  Bunu, talep ettiğiniz anahtarları izlemek için **Talep sütunundaki** tarihle birlikte kullanabilirsiniz.  Örneğin, anahtarı kullanarak ürünün yüklemesini etkinleştirdiğinizde not alabilirsiniz.

### <a name="exporting-your-claimed-keys"></a>Talep edilen anahtarlarınızı dışa aktarma
Talep ettiğiniz tüm anahtarların bir listesini ve sizin için otomatik olarak "talep edilen" olarak işaretlenmiş statik ve diğer anahtarların büyük bir seçkisini dışa aktarabilirsiniz.

> [!IMPORTANT]
> Aboneliğinizin süresi dolduğunda, artık yeni anahtarlar talep edemeyecek veya talep edilen anahtarlarınızı dışa aktaramazsınız.

Anahtarlarınızı dışa aktarmak için, Ürün Anahtarları sayfasının en sağındaki **Tüm Anahtarları Dışa** Aktar bağlantısına tıklamanız yeterlidir.  KeysExport.xml başlıklı bir .xml dosyası oluşturulur ve dosyayı açma veya kaydetme seçeneğiniz olur.  .xml dosyalarını işleyebilen bir uygulama ile dosyayı açmanız gerekir.  Örneğin, dosyayı Excel'de salt okunur çalışma kitabı olarak açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yazılım indirmeye ve anahtarları kullanmaya hazır https://my.visualstudio.com/downloadsolduğunuzda, 'yi ziyaret edin.  Yazılım indirme hakkında daha fazla bilgi için lütfen [indirmeye genel bakışa](download-software.md)bakın.