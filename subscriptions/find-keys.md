---
title: Visual Studio aboneliklerinde ürün anahtarlarını bulma ve oluşturma | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 07/30/2020
ms.topic: conceptual
description: Visual Studio aboneliklerinde ürün anahtarlarını bulma, talep etme ve dışa aktarma hakkında bilgi edinin
ms.openlocfilehash: 8ee21c544a44bfd5eca831cdc9fd1c8e00adb35b
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453745"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde ürün anahtarlarını bulma ve oluşturma
Bu makalede ürün anahtarlarının ' den nasıl bulunduğu, talep verilmesi ve dışarı aktarılacağı açıklanmaktadır https://my.visualstudio.com/productkeys .  Bir ürünü anahtar, perakende ve toplu lisans sürümleriyle ve günlük ürün anahtarı talep limitlerine göre etkinleştirme hakkında daha fazla bilgi için lütfen [ürün anahtarlarına genel bakış](product-keys.md)' ı ziyaret edin.

## <a name="locating-and-claiming-product-keys"></a>Ürün anahtarlarını bulma ve oluşturma
Ürün anahtarlarınızı görüntülemek için Visual Studio aboneliğinizde oturum açmış olmanız gerekir. [Karşıdan yüklemeler](https://my.visualstudio.com/downloads) sayfasında aşağıda gösterildiği gibi, belirli bir ürün Için mavi **get anahtar** bağlantısı seçilerek tek tek ürün anahtarları bulunur.  Tüm anahtarlar, [ürün anahtarları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sayfasında toplu olarak da kullanılabilir. Tek bir ürün için birden çok anahtar varsa, bu yükleme için notlar sütununda notlar görüntülenir ve bu da hangi anahtarın kullanılması gerektiğini belirlemenize yardımcı olur.
> [!div class="mx-imgBorder"]
> ![Indirmeler sayfasından anahtar al](_img/product-keys/download-get-key.png "Bu ürün için bir anahtar almak üzere herhangi bir indirmenin bilgi sayfasında anahtar al ' a tıklayın.")

Bazı ürünler ürünün birden çok sürümünü tek bir indirme halinde paketler. Bu durumlarda, girilen ürün anahtarı ürünün hangi sürümünün yüklü olduğunu belirler.
Etkinleştirme gerekli olmadığından, bazı anahtarlar, "static" anahtarları gibi otomatik olarak sağlanır. Diğer anahtarların, ürün için **anahtar al** bağlantısı seçilerek talep alınmalıdır.

Ürüne bağlı olarak çeşitli anahtar türleri mevcuttur.

### <a name="product-key-types"></a>Ürün anahtarı türleri

|    Anahtar türü           |    Açıklama                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Geçerli değil                    |    Bu ürünü yüklemek için gereken anahtar yok.                                                       |
|    Retail                     |    Perakende tuşları çoklu etkinleştirmeleri sağlar ve ürünün perakende yapıları için kullanılır. Çoğu durumda, her anahtar için 10 etkinleştirmeye izin verilir, ancak aynı makinede genellikle daha fazlasına izin verilir.                                                       |
|    Çoklu etkinleştirme        |    Çoklu etkinleştirme anahtarı (MAK), aynı anahtarla bir ürünün birden çok yüklemesini etkinleştirmenizi sağlar. Mak 'leri, genellikle ürünlerin toplu lisanslama sürümleriyle kullanılır. Genellikle, abonelik başına yalnızca bir MAK anahtarı sağlanır.    |
|    Statik etkinleştirme anahtarı    |    Statik etkinleştirme anahtarları, etkinleştirme gerektirmeyen ürünler için sağlanır. Bunlar, herhangi bir sayıda yükleme için kullanılabilir.                                                                                                                  |
|    Özel anahtar                 |    Özel anahtarlar, ürünü etkinleştirmek veya yüklemek için özel eylemler veya bilgiler sağlar.                                                                                                                                                                |
|    VA 1,0                     |    Bunlar MAK 'a benzeyen birden çok etkinleştirme anahtarlardır.                                                                                                                                                                                                 |
|    OEM anahtarı                    |    Bunlar, birden çok etkinleştirmeye izin veren özgün ekipman üreticisi anahtarlardır.                                                                                                                                                                       |
|    DreamSpark perakende anahtarı    |    Bu perakende tuşları DreamSpark içindir ve tek bir etkinleştirmeye izin verir. DreamSpark perakende anahtarları toplu olarak verilir ve öncelikle öğrenci tüketimine yöneliktir.                                                                                     |
|    DreamSpark Lab anahtarı         |    Bu laboratuvar kullanım tuşları, DreamSpark programları içindir ve birden çok etkinleştirmeye izin verir. DreamSpark laboratuvar anahtarları, University bilgisayar laboratuvarı senaryolarında kullanılmak üzere tasarlanmıştır.                                                                                       |
|    DreamSpark MAK anahtarı         |    Bunlar DreamSpark program müşterileri için MAK anahtarlardır.                                                                                                                                                                                                  |
|

Ürünün karşıdan yükleme sayfasından bir anahtar talep edebilir veya [ürün anahtarları](https://my.visualstudio.com/productkeys) sayfasında ihtiyacınız olan anahtarı arayabilirsiniz.

### <a name="claiming-product-keys"></a>Ürün anahtarları talep ediliyor
Yalnızca etkin abonelikleri olan aboneler ürünleri indirebilir ve ürün anahtarlarını talep edebilir.  Aboneliğiniz etkinken, [ürün anahtarları](https://my.visualstudio.com/productkeys) sayfasından talep ettiğiniz anahtarları dışarı aktarabilirsiniz.

Bir ürün anahtarı talep etmek için:
1. Visual Studio aboneliğinizde oturum açın.  Ürünleri indirmek veya ürün anahtarlarını talep etmek için oturum açmış olmanız gerekir.
2. [Ürün anahtarları](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) sekmesine tıklayın.
3. Ürün anahtarları ürün adına göre alfabetik olarak listelenir.  İstediğiniz ürünün adına aşağı doğru kaydırabilir ya da sayfanın en üstündeki arama çubuğunu kullanarak arama yapabilirsiniz.
> [!div class="mx-imgBorder"]
> ![Ürün anahtarı ara](_img/product-keys/search-keys.png "İstediğiniz ürüne kaydırın veya herhangi bir ürünü hızlı bir şekilde bulmak için arama kutusunu kullanın.")
   
Bu örnekte, Visual Studio Enterprise 2019 için bir ürün anahtarı bulmak için arama çubuğunu kullandık.
Gördüğünüz gibi, çeşitli sürümler listelenir.  Tek bir anahtar, 16,0 ve 16,1 Visual Studio Enterprise 2019 sürümleri için zaten talep edildi.  Farklı türlerde ek anahtarlar, her iki sürüm için de kullanılabilir. **Notlar** sütununda, istenen anahtarlar hakkında kısa bir not kaydedebileceğinizi unutmayın.  Bunu, talep ettiğiniz anahtarların izini sağlamak için, **istenen** sütundaki tarihle birlikte kullanabilirsiniz.  Örneğin, anahtarı kullanarak ürünün yüklemesini etkinleştirdiğinizde Not alabilirsiniz.

### <a name="exporting-your-claimed-keys"></a>Talep edilen anahtarlarınız dışarı aktarılıyor
İstediğiniz tüm anahtarların bir listesini, sizin için otomatik olarak "talep edilen" olarak işaretlenen büyük bir statik ve diğer anahtar seçimleriyle birlikte dışarı aktarabilirsiniz.

> [!IMPORTANT]
> Aboneliğinizin süresi dolarsa, artık yeni anahtarları talep edemeyeceksiniz veya talep ettiğiniz anahtarları dışarı aktarabilirsiniz.

Anahtarlarınızı dışarı aktarmak için, ürün anahtarları sayfasının en sağındaki **tüm anahtarları dışarı aktar** bağlantısına tıklamanız yeterlidir.  KeysExport.xml adlı bir. xml dosyası oluşturulur ve dosyayı açma veya kaydetme seçeneğiniz olacaktır.  Bu dosyayı .xml dosyalarını işleyebilen bir uygulamayla açmanız gerekir.  Örneğin dosyayı Excel’de salt okunur bir çalışma kitabı olarak açabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yazılım indirmeye ve anahtarları kullanmaya hazırsanız, adresini ziyaret edin https://my.visualstudio.com/downloads .  Yazılım indirme hakkında daha fazla bilgi için lütfen [indirmeye genel bakış](download-software.md)bölümüne bakın.