---
title: Visual Studio için değerlendirme araçları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698425"
---
# <a name="evaluation-tools-for-visual-studio"></a>Visual Studio İçin Değerlendirme Araçları
## <a name="craftsmanship-checklist-for-visual-studio"></a>Visual Studio için craftsmansevkiyat denetim listesi
 Görsel ve etkileşim ayrıntıları için Kullanıcı deneyimi kalitesini değerlendirmek üzere bu denetim listesini kullanın.

### <a name="overview"></a>Genel Bakış

- Tüm komutların, kullanıcılara komutlarının yapıldığını bildiren geri bildirimle sonuçlandığını doğrulayın.

- Tüm Kullanıcı arabirimi öğelerinin ve denetimlerinin tüm temalar ve Yüksek Karşıtlık modunda görünür olduğunu doğrulayın.

- Etkin olmayan ve etkin seçimin her zaman hem standart hem de Yüksek Karşıtlık modunda farklılaştırılan olduğunu doğrulayın.

- Odağın her zaman görünür ve görünür olduğunu doğrulayın.

### <a name="performance"></a>Performans

- Bir komutun tamamlaması için bir saniyeden daha fazla sürerse, bir tür "meşgul" göstergesinin gösterildiğini doğrulayın.

- Bir komutun tamamlaması için 10 saniyeden daha fazla sürerse, kesin bir ilerleme çubuğunun (tercih edilen) veya belirsiz olarak gösterildiğini doğrulayın.

### <a name="ui-text"></a>UI metni

- Tüm etiketlerin tümce veya başlık büyük/küçük harf olduğunu ve metinlerin tamamen küçük harfli olduğunu doğrulayın.

    ||Doğru|Yanlış|
    |-|-------------|---------------|
    |**Komut metni (tümü)**|Tümce durumu:<br /><br /> **Dizin adı:**|Dizin adı:|
    |**Düğme metni (istemci)**|Başlık durumu:<br /><br /> **[Varsayılan olarak ayarla]**|VARSAYıLAN OLARAK AYARLA|
    |**Düğme metni (çevrimiçi)**|Tümce durumu:<br /><br /> **[Varsayılan olarak ayarla]**||

- Grup üstbilgileri ve düğmeleri hariç tüm etiketlerin, iki nokta üst üste ile bitdiğini ve eşleştirdikleri denetimin önüne eklendiğini doğrulayın.

- Kullanıcı girişini yakalamak için UI 'yi Başlatan düğmelerin, komutların ve komut bağlantılarının üç nokta ( **...]**) ile bitidiğinizi doğrulayın.

  Örnekler:

  - İletişim kutusunda bir **[Gelişmiş...]** düğmesi.

  - Araçlar menüsünün (**araçlar > seçenekleri**) altındaki komut seçenekleri bir üç nokta almaz, çünkü iletişim kutusu başlatıldığında komutun amacı olur.

- Sektör standardı terimleri dışında, Kullanıcı arabiriminin hiçbir kısaltmalar içerdiğini doğrulayın. Örneğin, hiçbir HTML veya TCP/IP 'nin yazılması gerekmez, ancak OOM (yetersiz bellek) ve PII (kişisel bilgiler) olmalıdır.

### <a name="keyboard-access"></a>Klavye erişimi

- Klavye ile her görevi gerçekleştirmenin bir yolu olduğunu doğrulayın. Bu, genellikle her denetim için klavye erişimi aracılığıyla gerçekleştirilir, ancak bazı yüksek görsel alanlarda, kod görünümüne geçme gibi bir geçici çözüm kabul edilebilir.

- Bir mantıksal düzende (soldan sağa ve yukarıdan aşağıya) denetimler arasında sekme bildiğinizi doğrulayın. Çoğu denetim için bu en iyi uygulamadır, ancak tüm denetimler bu yaklaşımı gerektirmez. Örneğin, radyo düğmesi denetimlerinin tek sekme durağı olan bir grupta olduğunu doğrulayın.

- Tüm denetimlerin etiketlere sahip olduğunu ve her etiketin bir anımsatıcı içerdiğini doğrulayın (özel durumlar, sekmede etiketli bir denetimi izleyebilecek etiketli olmayan bazı denetimler içerir).

- Hiçbir anımsatıcı çakışması olmadığını doğrulayın.

### <a name="fonts"></a>Yazı Tipleri

- Tüm yazı tiplerinin (yüz, boyut, renk) tutarlı olarak kullanıldığını ve hiyerarşiyi korudığını doğrulayın.

- Tüm Kullanıcı arabirimi öğelerinin ortam yazı tipi hizmetini kullanbildiğini doğrulayın. (Bkz. [Visual Studio Için yazı tipleri ve biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Hizmetin kullanılıp kullanılmadığını kontrol etmek için **araçlar > seçenekler > yazı tipi ve renkler**' e gidin. Ayarlar açılan menüsünde ortam yazı tipi ' ni seçin ve yazı tipi yüzünüzü bir stillistik olarak farklı (Harrington veya Comic Sans gibi) olarak değiştirin ve boyutu 12 nk olarak ayarlayın. Daha sonra Tamam'a tıklayın. IDE 'yi yeniden başlatmanız gerekebilir, ancak çoğu kullanıcı arabirimi hemen değişecektir. Yeniden başlatma sırasında bile yazı tipi değişikliğini içermeyen bölgeler, ortam yazı tipini kullanmıyor.

- Ortam yazı tipi değiştirildiğinde, hizmetin türevi olan fontların (örneğin, kalın veya büyütülmüş metin), "normal" metinle ilişkili boyut ve biçimlendirmelerini koruyacağını doğrulayın.

- Büyütülmüş yazı tiplerinde dolayı kırpma hatası olmadığını doğrulayın. Kırpıldığı yazı tipleri büyük olasılıkla sabit yükseklik denetimleri veya sabit yükseklik kapsayıcıları sonucudur.

### <a name="dialogs"></a>İletişim Kutuları

- İletişim kutusu başlığının, onu başlatan komutla aynı olduğunu doğrulayın.

- Tüm Standart denetimlerin işletim sistemiyle tutarlı olduğundan emin olun: arka plan rengi standarttır ve denetimlerin standart denetimlerden farklı görünmesini sağlayan özel bir yeniden şablonlu stili olmamalıdır.

- Form içindeki kenar boşluklarının 12 piksel olması gerektiğini ve Tekdüzen ve tutarlı görünmesini gerektiğini doğrulayın.

- İletişim kutularının IDE kabuğu veya bunları oluşturan pencere içinde ortalanmasını doğrulayın.

- Faydalı olduğunda, iletişim kutuları yeniden boyutlandırılabilir olmalıdır. Yeniden boyutlandırılabilir iletişim kutularında, yeniden boyutlandırmaya devam edilirken, iletişim kutusunun diğer bölümleri sabit kaldığı sürece uygun denetimlerin yeniden boyutlandırılması gerektiğini doğrulayın.

- Yeniden boyutlandırılabilir iletişim kutularının Kullanıcı tarafından ayarlanmış tüm boyutları (boyut, konum, iletişim kutusu denetimlerinin genişletilmesi vb.) kalıcı olarak doğrulayın.

- Başlık çubuğunda bir simge olmadığından emin olun.

- Başlık çubuğunda simge durumuna küçült ve büyüt düğmelerinin bulunmadığını doğrulayın.

#### <a name="dialog-operation-buttons-vs-client-only"></a>İletişim kutusu işlem düğmeleri (yalnızca VS Istemcisi)

- İşlem düğmelerinin bu sırada olduğunu doğrulayın: **Tamam**, **iptal**, **Uygula**.

- **Tamam** ve **iptal** düğmelerinin Standart boyut olduğunu doğrulayın: 75x23 piksel.

- **Tamam** ve **iptal** düğmelerinin dize uzunluğuna bakılmaksızın eşit boyutta olduğunu doğrulayın.

- Bir işlem düğmesi üzerindeki etiket, düğmenin standart 'tan daha geniş olmasını gerektiriyorsa, karşılık gelen **iptal** düğmesinin eşit boyutta olduğunu doğrulayın.

- Düğmeler ve ilişkili denetimler arasında 6 piksellik bir doldurma olduğunu doğrulayın.

- **Tamam** ve **iptal** düğmelerinin anımsatıcıları (altı çizili bir harfle tanımlanan erişim anahtarları) olmadığından emin olun.

- Bir düğmenin (genellikle **Tamam**) varsayılan olarak odağa sahip olduğunu doğrulayın.

- **ESC** 'nin iletişim kutusunu iptal ettiğini doğrulayın

- Odak, bir denetimde işlem yapan bir denetimde değilse, **ENTER** 'ın varsayılan düğmeyi yürüttüğünü doğrulayın.

- **Tamam** ve **iptal** düğmelerinin iletişim kutusunun sağ alt köşesinde konumlandığını doğrulayın. Nadir özel durumlarda, bunlar için sağ üst köşedeki dikey olarak yığılmaları kabul edilebilir.

- Dikey yapılandırmanın, yalnızca diğer düğmelerin iletişim kutusu içindeki yatay hizalamadaki kullanıldığını doğrulayın.

### <a name="control-standards"></a>Denetim standartları

#### <a name="general"></a>Genel

- Mümkün olduğunda, kullanıcı etkileşimini hızlandırmak ve kullanıcıları güvenli ya da genel bir sonuca yönlendirmek için uygun bir varsayılan değer olduğunu doğrulayın.

- Standart denetimlerin, kullanıcıların daha önceki deneyime göre neler olacağını bilmesi için aynı şekilde davrandığını doğrulayın.

#### <a name="label-controls"></a>Etiket denetimleri

- Her bir denetimin bir etiketi olduğunu ve her etiketin, denetimiyle (genellikle bir 4-6 piksel aralığında) görsel olarak eşleştirildiğini ve ilgili denetimine diğer denetimlerden daha yakın olduğunu doğrulayın.

- Etiketlerin taban çizgisi sola yerleştirildiyse giriş metninin taban çizgisiyle hizalanabilmesi için etiketlerin sol ve ortalanan denetim sol kenarı ile sola doğru konumlandırılmış olduğunu doğrulayın.

- Birden çok yığılmış etiket ve giriş denetimlerinin bir denetimin soluna yerleştirildiğini, etiketlerin sol ve iletişim kutusunun kenarından eşit uzaklıkta olduğunu, hiçbir şekilde doğrudan temizlemeyeceğini ve denetimlerden eşit bir mesafeyi olduğunu doğrulayın. Çiftleri, gruplandırmayı göstermek için ek aralığa gerek duymadığı müddetçe eşit bir şekilde dağıtılmalıdır.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Giriş denetimleri (metin kutuları ve Birleşik giriş kutuları)

- Varsayılan ortam yazı tipini kullanırken, metin kutuları, Birleşik giriş kutuları ve düğmelerin görüntüleme yüksekliğinin tüm 23 piksel olduğunu doğrulayın.

- İpucu metni kullanılırsa, rengin `Environment.ControlEditHintText` Color hizmetini kullanmaya ayarlandığını doğrulayın.

- Alan, bu şekilde tanımlanması gereken gerekli bir alan ise şunları doğrulayın:

  - arka planın olarak ayarlandığı `Environment.ControlEditRequiredBackground` ve ön plan olarak ayarlandığı `Environment.ControlEditRequiredHintText`

  - Denetim içinde **" \<Required> "** olarak görünen İpucu metni

#### <a name="button-controls"></a>Düğme denetimleri

- Daha uzun metin konağunda, düğmelerin en düşük 75x23 piksel boyutunda olduğunu doğrulayın.

- Düğmelerin 3-5 piksel sol ve sağ kenar boşluklarına ve içerik için doldurma içerdiğini doğrulayın.

- Bir **[gözatın...]** düğmesi (veya benzer işlevsellik) yerine yalnızca üç nokta **[...]** ile küçük bir kare düğme kullanmak kabul edilebilir. Kullanıldıysa, düğmenin 23x23 boyutunda olduğunu doğrulayın.

- Bir iletişim kutusunda birden fazla **[gözatdır...]** düğmesi varsa, kısaltılmış sürümün (yalnızca üç nokta-yalnızca üç nokta-yalnızca **[...]**) kullanıldığını doğrulayın.

- Üç nokta **[...]** düğmelerinin bir anımsatıcı olmadığından emin olun. Odak, yukarıdaki giriş denetiminde olduğunda, bir sekme odağı üç nokta düğmesine taşımalıdır.

- Daha fazla kullanıcı girişi yakalayan ikincil kullanıcı arabirimini başlatan düğmelerin, komutların ve komut bağlantılarının üç nokta **[...]** ile bitmesi gerektiğini doğrulayın.

#### <a name="hyperlinks"></a>Köprüler

- Bir köprü denetiminin etkin olduğunda hiçbir zaman kırmızı şekilde yanıp sönmez olduğunu doğrulayın. Bu, renk hizmetinin kullanımda olmadığı bir göstergedir

- Kullanılan VS renklerinin şu şekilde olduğunu doğrulayın:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Bir paragrafta gömülü olmadığı takdirde köprülerin altı çizili olmadan mavi göründüğünü doğrulayın.

#### <a name="check-boxes"></a>Onay kutuları

- Bir onay kutusunun çok satırlı metni varsa, kutunun tüm satırlarda dikey ortalanmış şekilde metnin ilk satırıyla hizalanacağını doğrulayın.

- Onay kutularının her zaman bir ikili seçimi olduğunu ve kullanıcıya gitmeyin ya da yeni pencereler veya sayfalar açmayın olduğunu doğrulayın.

- Bir onay kutusu, bir giriş denetimiyle ilgili bir seçenek gösteriyorsa, bu denetimin sol ve sağ tarafında olduğunu ve ilişkisini göstermek için çok yakın olduğunu doğrulayın.

- Bir onay kutusunun bir iletişim kutusu veya sayfanın tüm içeriğini etkinleştirmek için **hiçbir** şekilde kullanılmadığını doğrulayın.

#### <a name="group-boxes"></a>Grup kutuları

- İletişim kutusunun tüm içeriğini içeren bir iletişim kutusunun içinde tek bir grup kutusu içermediğini doğrulayın.

- Her bir grup kutusunda en az iki denetim olduğunu doğrulayın.

- Nadiren bir iletişim kutusunda ikiden fazla grup kutusu olması gerekir.

- İç içe geçmiş grup kutusu bulunmadığını doğrulayın.

### <a name="icons"></a>Simgeler

- Koyu Temada simgelerin doğru şekilde ters göründüğünü doğrulayın.

- Tüm simgelerin temel kavramları temel aldığını doğrulayın.

- Her simgenin farklı olduğunu, tanılamayı kolay olduğunu ve ikiden fazla kavram (durum değiştiricisi olmadan) içermediğini doğrulayın.

- Taban simgesinin boşluk içinde ortalanmış göründüğünü doğrulayın.

- Yüksek Karşıtlık modda tüm simgelerin okunabilir göründüğünü doğrulayın.

- Kullanılan rengin renk kullanım standartları ile hizalandığını doğrulayın.

- Simgelerin etrafında has (sınır) olmadığından emin olun. (Varsa Halo, bitişik Kullanıcı arabiriminin arka plan rengiyle eşleşmelidir).

### <a name="touch-enabled-ui"></a>Dokunmatik özellikli Kullanıcı arabirimi

- Etkileşimli denetimlerin, boyutu kolay touchable-minimum **23x23 piksel** olacak şekilde yeterince büyük olduğunu doğrulayın

- En sık kullanılan denetimlerin boyutunun en az **40x40 piksel** olduğunu doğrulayın.

- Etkileşimli denetimlerin aralarında en az **5 piksel boşluk** olduğunu doğrulayın
