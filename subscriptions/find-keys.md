---
title: Aboneliklerde ürün anahtarlarını bulma Visual Studio talep | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 03/21/2021
ms.topic: conceptual
description: Aboneliklerde ürün anahtarlarını bulma, talep ve dışarı aktarma Visual Studio öğrenin
ms.openlocfilehash: 11478550726aafafd5d2fa2e999e041c76906790
ms.sourcegitcommit: f07b737f43a29e30d040cc5793437f462fedb595
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2021
ms.locfileid: "127964715"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Aboneliklerde ürün anahtarlarını bulma Visual Studio talep ediyor
Bu makalede, ürününden ürün anahtarlarını bulma, talep ve dışarı aktarma https://my.visualstudio.com/productkeys açıklanmıştır.  Anahtarı olan bir ürünü etkinleştirme, anahtarların perakende ve toplu lisans sürümleri ve günlük ürün anahtarı talep sınırları hakkında daha fazla bilgi için ürün anahtar genel [bakışını ziyaret edin.](product-keys.md)

## <a name="locating-and-claiming-product-keys"></a>Ürün anahtarlarını bulma ve talepte bulma
Ürün anahtarlarınızı görüntülemek için Visual Studio aboneliğinde oturum amışsınız. Tek tek ürün anahtarları, aşağıda gösterildiği **gibi** İndirmeler sayfasında belirli bir ürün için mavi Anahtar Al [bağlantısı](https://my.visualstudio.com/downloads) seçerek bulunur.  Tüm anahtarlar, Ürün Anahtarları sayfasında toplu [olarak da](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) kullanılabilir. Tek bir ürün için birden çok anahtar olduğunda, hangi anahtarın kullan gerektiğini tanımlamaya yardımcı olmak için indirme için Notlar sütununda notlar görüntülenir.
> [!div class="mx-imgBorder"]
> ![İndirmeler Sayfasından Anahtar Al](_img/product-keys/download-get-key.png "herhangi bir indirme için bilgi sayfasında Anahtarı al'ı seçerek ilgili ürüne ilişkin bir anahtar edinebilirsiniz.")

Bazı ürünler, ürünün birden çok sürümünü tek bir indirmede paketler. Bu durumlarda, girilen ürün anahtarı ürünün hangi sürümünün yüklü olduğunu belirler.
Bazı anahtarlar otomatik olarak sağlanır( örneğin, "statik" anahtarlar) ve etkinleştirme gerekli değildir. Ürün için Anahtar Al bağlantısı seçerek **diğer anahtarların** talep eduşuna basın.

Ürüne bağlı olarak çeşitli anahtar türleri kullanılabilir.

### <a name="product-key-types"></a>Ürün anahtarı türleri

|    Anahtar Türü           |    Description                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Geçerli değil                    |    Bu ürünü yüklemek için anahtar gerekmez.                                                       |
|    Retail                     |    Perakende anahtarları birden çok etkinleştirmeye olanak sağlar ve ürünün perakende derlemeleri için kullanılır. Çoğu durumda anahtar başına 10 etkinleştirmeye izin verilir, ancak genellikle aynı makinede daha fazla etkinleştirmeye izin verilir.                                                       |
|    Çoklu Etkinleştirme        |    Çoklu Etkinleştirme Anahtarı (MAK), bir ürünün aynı anahtara sahip birden çok yüklemesini etkinleştirmenizi sağlar. MAK'ler, ürünlerin Toplu Lisanslama sürümleriyle birlikte kullanılır. Genellikle abonelik başına yalnızca bir MAK anahtarı sağlanır.    |
|    Statik Etkinleştirme Anahtarı    |    Statik etkinleştirme anahtarları, etkinleştirme gerektirmeyen ürünler için sağlanır. Bunlar, herhangi bir sayıda yükleme için kullanılabilir.                                                                                                                  |
|    Özel Anahtar                 |    Özel anahtarlar, ürünü etkinleştirmek veya yüklemek için özel eylemler veya bilgiler sağlar.                                                                                                                                                                |
|    VA 1.0                     |    Mak'e benzer şekilde birden çok etkinleştirme anahtarı.                                                                                                                                                                                                 |
|    OEM Anahtarı                    |    Birden çok etkinleştirmeye izin verecek orijinal Ekipman Üreticisi anahtarları.                                                                                                                                                                       |
|    DreamSpark Perakende Anahtarı    |    DreamSpark perakende anahtarları tek bir etkinleştirmeye olanak sağlar. DreamSpark Perakende anahtarları toplu olarak ve öncelikli olarak öğrenci tüketimine yöneliktir.                                                                                     |
|    DreamSpark Laboratuvar Anahtarı         |    Birden çok etkinleştirmeye olanak sağlayan DreamSpark programları için laboratuvar kullanım anahtarları. DreamSpark Laboratuvar Anahtarları, üniversite bilgisayar laboratuvarı senaryolarında kullanılmak üzere tasarlanmıştır.                                                                                       |
|    DreamSpark MAK Anahtarı         |    DreamSpark programı müşterileri için MAK anahtarları.                                                                                                                                                                                                  |
|

Ürünün indirme sayfasından bir anahtar talep edebilirsiniz veya ihtiyacınız olan anahtarı Ürün Anahtarları sayfasında [arayabilirsiniz.](https://my.visualstudio.com/productkeys)

### <a name="claiming-product-keys"></a>Ürün anahtarlarını talep ediyor
Yalnızca etkin abonelikleri olan aboneler ürünleri indirebilir ve ürün anahtarlarını talep eder.  Aboneliğiniz etkinken ürün anahtarları [sayfasından talepte bulunarak](https://my.visualstudio.com/productkeys) anahtarlarınızı dışarı aktarabilirsiniz.

Bir ürün anahtarı talep etmek için:
1. Visual Studio oturum açma.  Ürünleri indirmek veya ürün anahtarlarını talep etmek için oturum açık olması gerekir.
2. Ürün Anahtarları [sekmesini](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) seçin.
3. Ürün anahtarları, ürün adına göre alfabetik olarak listelenir.  İstediğiniz ürünün adına kadar aşağı kaydırabilirsiniz veya sayfanın üst kısmında yer alan arama çubuğunu kullanarak ürünü arayabilirsiniz.
> [!div class="mx-imgBorder"]
> ![Ürün Anahtarı ara](_img/product-keys/search-keys.png "İstediğiniz ürüne kaydırın veya herhangi bir ürünü hızla bulmak için arama kutusunu kullanın.")
   
Bu örnekte, 2019'da Visual Studio Enterprise için bir ürün anahtarını bulmak için arama çubuğunu kullandık.
Gördüğünüz gibi, listelenen birkaç sürüm vardır.  2019 sürüm 16.0 ve 16.1 için her biri bir anahtar Visual Studio Enterprise zaten talep edildi.  Her iki sürüm için de farklı türlerde ek anahtarlar kullanılabilir. Notlar sütunundaki talep eden anahtarlar hakkında kısa bir not **kaydedebilirsiniz.**  Bunu Talep Edildi sütunundaki **tarihle birlikte** kullanarak talepte bulundurarak anahtarlara göz edebilirsiniz.  Örneğin, anahtarını kullanarak ürünün yüklemesini etkinleştiren notlar ekleyebilirsiniz.

### <a name="exporting-your-claimed-keys"></a>Talep eden anahtarlarınızı dışarı aktarma
Talepte bulundurarak anahtarların listesini dışarı aktarabilirsiniz.  Buna, sizin için otomatik olarak "talep edildi" olarak işaretlenen çok sayıda statik anahtar ve diğer anahtarlar dahildir.

> [!IMPORTANT]
> Aboneliğinizin süresi dolsa, artık yeni anahtar talep edemeyecek veya talepte bulundurarak anahtarlarınızı dışarı aktaramazsınız.

Anahtarlarınızı dışarı aktarma için Ürün Anahtarları **sayfasının** sağ en sağ tarafından Tüm anahtarları dışarı aktar bağlantısını seçin.  .xml adlı bir KeysExport.xml dosyası oluşturulur ve dosyayı açmayı veya kaydetmeyi seçebilirsiniz.  Bu dosyayı .xml dosyalarını işleyebilen bir uygulamayla açmanız gerekir.  Örneğin dosyayı Excel’de salt okunur bir çalışma kitabı olarak açabilirsiniz.

## <a name="resources"></a>Kaynaklar
- [Visual Studio abonelik desteği](https://aka.ms/vssubscriberhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Yazılım indirmeye ve anahtarları kullanmaya hazır olduğunda, ziyaret https://my.visualstudio.com/downloads edin.  Yazılım indirme hakkında daha fazla bilgi için bkz. [indirmeye genel bakış.](download-software.md)