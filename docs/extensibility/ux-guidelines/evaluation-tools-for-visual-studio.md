---
title: Visual Studio için değerlendirme araçları | Microsoft Docs
description: Visual Studio için Tasarlayabileceğiniz yeni özelliklerle ilgili görsel ve etkileşim ayrıntıları için Kullanıcı deneyimi kalitesini değerlendirmek üzere bu denetim listesini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fb96033f2fb3ce10a7bba553aa494fb1b8a50941
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102096"
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

- Tüm Kullanıcı arabirimi öğelerinin ortam yazı tipi hizmetini kullanbildiğini doğrulayın. ( [Visual Studio Için yazı tiplerine ve biçimlendirmeye](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)bakın)

     Hizmetin kullanılıp kullanılmadığını kontrol etmek için **araçlar > seçenekler > yazı tipi ve renkler**' e gidin. Ayarlar açılan menüsünde, ortam yazı tipi ' ni seçin ve yazı tipi yüzünüzü bir stillistik olarak farklı bir şekilde değiştirin (harrington veya Comic Sans gibi) ve boyutu 12 nk olarak ayarlayın. Daha sonra Tamam'a tıklayın. IDE 'yi yeniden başlatmanız gerekebilir, ancak çoğu kullanıcı arabirimi hemen değişecektir. Yeniden başlatma sırasında bile yazı tipi değişikliğini içermeyen bölgeler, ortam yazı tipini kullanmıyor.

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

- Üç nokta **[...]** düğmelerinin bir anımsatıcı olmadığından emin olun. Odak, yanındaki giriş denetimine olduğunda, odağı bir sekmenin üç nokta düğmesine taşıması gerekir.

- Daha fazla kullanıcı girişi yakalayan ikincil kullanıcı arabirimini başlatan düğmelerin, komutların ve komut bağlantılarının üç **noktayla bitip bitm** gerektiğini doğrulayın .

#### <a name="hyperlinks"></a>Köprüler

- Etkin olduğunda köprü denetimi asla kırmızı yanıp sönmez. Bu, renk hizmetinin kullanım olmadığının göstergesidir

- Kullanılan VS Renklerini doğrulayın:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Bir paragrafa ekli olmadığı sürece köprülerin altı çizili olmayan mavi olduğunu doğrulayın.

#### <a name="check-boxes"></a>Onay kutuları

- Onay kutusunda çok satırlı metin varsa, kutunun tüm satırlarda dikey olarak ortalanmamış ilk metin satırıyla hizalı olduğunu doğrulayın.

- Onay kutularının her zaman ikili seçim olduğunu doğrulayın ve kullanıcıya gidin veya yeni pencereler ya da sayfalar açmayın.

- Bir onay kutusu giriş denetimiyle ilgili bir seçenek gösteriyorsa, ilişkisini belirtmek için bu denetimin altında sola ve çok yakın bir konuma sahip olduğunu doğrulayın.

- Bir iletişim kutusunun veya sayfanın **içeriğinin** tamamını etkinleştirmek için hiçbir zaman bir onay kutusunun kullanılmay olduğunu doğrulayın.

#### <a name="group-boxes"></a>Grup kutuları

- İletişim kutusunun içinde iletişim kutusunun içeriğinin tamamını içeren tek bir grup kutusu olmadığını doğrulayın.

- Her grup kutusunda en az iki denetim olduğunu doğrulayın.

- Bir iletişim kutusunda nadiren ikiden fazla grup kutusu olması gerekir.

- İç içe grup kutusu olmadığını doğrulayın.

### <a name="icons"></a>Simgeler

- Simgelerin koyu temada doğru ters şekilde görüntüleniyor olduğunu doğrulayın.

- Tüm simgelerin temel kavramları temel alarak çalıştığını doğrulayın.

- Her simgenin ayrı olduğunu, kolayca tanındığını ve ikiden fazla kavram içeremeden (durum değiştirici/dil olmadan) emin olun.

- Temel simgenin alan içinde ortalandı olarak görüntülendiğinden emin olur.

- Tüm simgelerin yerel modda okunaklı Yüksek Karşıtlık doğrulayın.

- Kullanılan tüm renklerin renk kullanım standartlarına uygun olduğunu doğrulayın.

- Simgelerin etrafında halo (kenarlıklar) olmadığını doğrulayın. (Varsa halo, bitişik kullanıcı arabiriminin arka plan rengiyle eşleşmeli).

### <a name="touch-enabled-ui"></a>Dokunma özellikli kullanıcı arabirimi

- Etkileşimli denetimlerin kolayca dokunılabilir olacak kadar büyük olduğunu doğrulayın - boyut olarak en az **23x23** piksel

- En sık kullanılan denetimlerin en az **40x40 piksel boyutunda olduğunu** doğrulayın.

- Etkileşimli denetimlerin aralarında en az **5 piksel boşluk olduğunu** doğrulayın
