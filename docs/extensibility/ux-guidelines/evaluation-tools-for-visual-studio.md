---
title: Visual Studio için Değerlendirme Araçları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698425"
---
# <a name="evaluation-tools-for-visual-studio"></a>Visual Studio İçin Değerlendirme Araçları
## <a name="craftsmanship-checklist-for-visual-studio"></a>Visual Studio için işçilik kontrol listesi
 Görsel ve etkileşim ayrıntıları için kullanıcı deneyimi kalitesini değerlendirmek için bu denetim listesini kullanın.

### <a name="overview"></a>Genel Bakış

- Tüm komutların, kullanıcılara komutlarının gerçekleştirildiğini söyleyen geri bildirimle sonuçlandığını doğrulayın.

- Tüm UI öğelerinin ve denetimlerinin tüm temalarda ve Yüksek Karşıtlık modunda görünür olduğunu doğrulayın.

- Etkin olmayan ve etkin seçimin hem standart hem de Yüksek Karşıtlık modunda her zaman farklılaştığını doğrulayın.

- Odak noktasının her zaman görünür ve görünür olduğunu doğrulayın.

### <a name="performance"></a>Performans

- Bir komutun tamamlanması bir saniyeden fazla sürerse, bir tür "meşgul" göstergesinin gösterildiğini doğrulayın.

- Bir komutun tamamlanması 10 saniyeden uzun sürerse, belirsiz (tercih edilen) veya belirsiz açık bir ilerleme çubuğunun görüntülendiğini doğrulayın.

### <a name="ui-text"></a>Kullanıcı Bira sımetin

- Tüm etiketlerin cümle veya başlık-case olduğunu ve hiçbir metnin tamamen küçük olmadığını doğrulayın.

    ||Doğru|Yanlış|
    |-|-------------|---------------|
    |**Komut metni (tümü)**|Cümle durumu:<br /><br /> **Dizin adı:**|Dizin Adı:|
    |**Düğme metni (istemci)**|Başlık örneği:<br /><br /> **[ Varsayılan Olarak Ayarlayın ]**|VARSAYıLAN OLARAK AYARLAYıN|
    |**Düğme metni (çevrimiçi)**|Cümle durumu:<br /><br /> **[ Varsayılan olarak ayarlayın ]**||

- Grup üstleri ve düğmeleri dışındaki tüm etiketlerin bir üst nokta üst üste ile sona erdiğini ve eşleştikleri denetimden önce geldiğini doğrulayın.

- Bir elips kullanıcı girişi sonunda yakalamak için Kullanıcı B) başlatmak düğmeleri, komutları ve komut bağlantıları doğrulamak **[...]**.

  Örnekler:

  - İletişim kutusunda **[Gelişmiş...]** düğmesi.

  - Araçlar menüsünün altındaki komut seçenekleri **(Araçlar > Seçenekleri)** elips almamalıdır, çünkü iletişim kutusunu başlatmak komutun amacıdır.

- Kişisel Bir UI'nin endüstri standardı terimler dışında hiçbir kısaltma içermediğini doğrulayın. Örneğin, OOM (bellek dışı) ve kişisel bilgi (kişisel olarak tanımlanabilir bilgiler) olmamalıdır, ancak ne HTML ne de TCP / IP hecelenmiş olması gerekir.

### <a name="keyboard-access"></a>Klavye erişimi

- Klavyeyle her görevi gerçekleştirmenin bir yolu olduğunu doğrulayın. Genellikle bu, her denetim için klavye erişimi yoluyla gerçekleştirilir, ancak bazı yüksek görsel alanlar için kod görünümüne gitme gibi bir geçici çözüm kabul edilebilir.

- Denetimleri mantıksal bir sırada (soldan sağa ve yukarıdan aşağıya) sektede bildiğinizi doğrulayın. Bu çoğu denetim için en iyi uygulama olsa da, tüm denetimler bu yaklaşımı gerektirmez. Örneğin, radyo düğmesi denetimlerinin tek bir sekme durağı olan bir grupta olduğunu doğrulayın.

- Tüm denetimlerin etiketleri olduğunu ve her etikette bir mnemonik olduğunu doğrulayın (özel durumlar, sekmede etiketli bir denetimi izleyebilecek bazı etiketsiz denetimleri içerir).

- Mnemonik çakışma olmadığını doğrulayın.

### <a name="fonts"></a>Yazı Tipleri

- Tüm yazı tiplerinin (yüz, boyut, renk) tutarlı bir şekilde kullanıldığını doğrulayın ve hiyerarşiyi koruyun.

- Tüm UI öğelerinin ortam yazı tipi hizmetini kullandığını doğrulayın. [(Bkz. Görsel Stüdyo için Yazı Tipleri ve Biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Hizmetin kullanılıp kullanılıp kullanılıp kullanılıp kullanılıp kullanılıp kullanılıp kullanmadğ **> >±Ä**ını kontrol Ayarlar açılır düşüşünde, Çevre Yazı Tipi'ni seçin ve yazı tipi yüzünü stilistik olarak farklı bir şeyle (Harrington veya Comic Sans gibi) değiştirin ve boyutu 12 pt olarak ayarlayın. Daha sonra Tamam'a tıklayın. IDE'yi yeniden başlatmanız gerekebilir, ancak çoğu UI hemen değişecektir. Yeniden başlatmada bile yazı tipi değişikliğini alamayan alanlar ortam yazı tipini kullanmıyor.

- Hizmetin türevi olan yazı tiplerinin (örneğin, kalın veya büyütülmüş metin) ortam yazı tipi boyutu değiştirildiğinde "normal" metinle ilişkili olarak boyutlarını ve biçimlendirmelerini koruduğunu doğrulayın.

- Genişletilmiş yazı tipleri nedeniyle kırpma hataları olmadığını doğrulayın. Kırpılabilen yazı tipleri büyük olasılıkla sabit yükseklik denetimlerinin veya sabit yükseklik kaplarının sonucuolur.

### <a name="dialogs"></a>İletişim Kutuları

- İletişim başlığının onu başlatan komutla aynı olduğunu doğrulayın.

- Tüm standart denetimlerin işletim sistemiyle tutarlı olduğunu doğrulayın: arka plan rengi standarttır ve hiçbir denetimin standart denetimlerden farklı görünmesini sağlayan özel bir yeniden şablonlu stile sahip olmaması gerekir.

- Form içindeki kenar boşluklarının 12 piksel olması ve düzgün ve tutarlı görünmesi gerektiğini doğrulayın.

- İletişim kutularının IDE kabuğu nun veya bunların oluşturduğu pencerenin içinde ortalanmış olarak göründüğünü doğrulayın.

- Yararlı olduğunda, iletişim kutuları yeniden boyutlandırılabilir olmalıdır. Yeniden boyutlandırılabilen iletişim kutularında, iletişim kutusunun diğer bölümleri sabit kalırken, yeniden boyutlandırma sırasında uygun denetimlerin yeniden boyutlandırılması gerektiğini doğrulayın.

- Yeniden boyutlandırılabilir iletişim kutularının kullanıcı tarafından ayarlanan boyutu (boyut, konum, iletişim denetimlerinin genişletilmesi vb.) devam ettiğini doğrulayın.

- Başlık çubuğunda simge olmadığını doğrulayın.

- Başlık çubuğunda Simge Durumuna Küçült ve Üst Düzeye Getir düğmesi olmadığını doğrulayın.

#### <a name="dialog-operation-buttons-vs-client-only"></a>İletişim işlemi düğmeleri (yalnızca VS İstemci)

- İşlem düğmelerinin bu sırada olduğunu doğrulayın: **Tamam**, **İptal**et , **Uygula**.

- **Tamam** ve **İptal** düğmelerinin standart boyut olduğunu doğrulayın: 75x23 piksel.

- **Dize** uzunluğuna bakılmaksızın Tamam ve **İptal** düğmelerinin eşit boyutta olduğunu doğrulayın.

- İşlem düğmesindeki etiket düğmenin standarttan daha geniş olmasını gerektiriyorsa, ilgili **İptal** düğmesinin eşit boyutta olduğunu doğrulayın.

- Düğmeler ve ilişkili denetimler arasında 6 piksel dolgu olduğunu doğrulayın.

- **Tamam** ve **İptal** düğmelerinde mnemonics (altı çizili harfle tanımlanan erişim anahtarları) olmadığını doğrulayın.

- Varsayılan olarak tek bir düğmenin (genellikle **Tamam)** odak noktası olduğunu doğrulayın.

- **Esc'nin** iletişim kutusunu iptal ettiğini doğrulayın

- Odak Enter'u işleyen bir denetimde değilse **Enter'ın** varsayılan düğmeyi yürüttüğünden doğrulayın.

- **Tamam** ve **İptal** düğmelerinin iletişim kutusunun sağ alt köşesinde konumlandırılmış olduğunu doğrulayın. Nadir durumlarda, bunların sağ üst üste dikey olarak istiflenmesi kabul edilebilir.

- Dikey yapılandırmanın yalnızca diğer düğmeler iletişim kutusu içinde yatay bir hizadaysa kullanıldığını doğrulayın.

### <a name="control-standards"></a>Kontrol standartları

#### <a name="general"></a>Genel

- Mümkün olduğunda, kullanıcı etkileşimini hızlandırmak ve kullanıcıları güvenli veya yaygın bir sonuca yönlendirmek için iyi varsayılan değerler olduğunu doğrulayın.

- Kullanıcıların önceki deneyimlere göre ne olacağını bilmeleri için standart denetimlerin aynı şekilde gerçekleştiğini doğrulayın.

#### <a name="label-controls"></a>Etiket denetimleri

- Her denetimin bir etiketi olduğunu ve her etiketin kendi denetimiyle (genellikle 4-6 piksel aralığında) görsel olarak eşlendiğini ve karşılık gelen denetimine diğer denetimlerden daha yakın olduğunu doğrulayın.

- Etiketlerin, yukarıda konumlandırılmış ve yatay olarak ortalanmışsa, sol kenarı sola doğru konumlandırılmış olduğunu doğrulayın, böylece etiketin taban çizgisi sola konumlandırılmışsa giriş metninin taban çizgisiyle hizalanır.

- Bir denetimin soluna birden fazla yığılmış etiket ve giriş denetimi yerleştirilmişse, etiketlerin sola ve iletişim kutusunun kenarından eşit bir mesafeye yerleştirilip yerleştirilemeyeceğini, asla sağa ve denetimlerden eşit bir mesafe yitirmeyeceğini doğrulayın. Çiftler, gruplandırmayı göstermek için ek aralık gerekmedikçe eşit olarak dağıtılmalıdır.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Giriş denetimleri (metin kutuları ve açılan kutular)

- Varsayılan ortam yazı tipini kullanırken metin kutuları, açılan kutular ve düğmelerin ekran yüksekliğinin hepsinin 23 piksel olduğunu doğrulayın.

- İpucu metni kullanılıyorsa, rengin renk `Environment.ControlEditHintText` hizmetini kullanarak ayarlı olduğunu doğrulayın.

- Alan bu şekilde tanımlanması gereken gerekli bir alansa, aşağıdakileri doğrulayın:

  - arka planın ayarlı `Environment.ControlEditRequiredBackground` olduğunu ve ön planın`Environment.ControlEditRequiredHintText`

  - denetim içinde **\<"Gerekli>"** olarak görünen ipucu metni olduğunu

#### <a name="button-controls"></a>Düğme denetimleri

- Düğmelerin en az 75x23 piksel boyutunda olduğunu doğrulayın, daha uzun metin barındırıyorum olmadıkça.

- Düğmelerin 3-5 piksellik sol ve sağ kenar boşluklarının yanı sıra içerik için dolgu olduğunu doğrulayın.

- Üzerinde **[Browse...]** düğmesi (veya benzer **[...]** işlevsellik) yerine üzerinde sadece bir elips [...] olan küçük bir kare düğme kullanmak kabul edilebilir. Kullanılırsa, düğmenin 23x23 boyutunda olduğunu doğrulayın.

- Bir iletişim kutusunda birden fazla **[Gözat...]** düğmesi varsa, kısaltılmış sürümün (yalnızca elipsler **[...]**) herkes için kullanıldığını doğrulayın.

- Bu elips **[...]** düğmeleri bir mnemonic yok doğrulayın. Odak, yanındaki giriş denetimine odaklanDığında, bir sekme odağı elips düğmesine taşımalıdır.

- Daha fazla kullanıcı girişi yakalar ikincil UI başlatmak düğmeleri, komutları ve komut bağlantıları bir elips sona ermesi gerektiğini doğrulayın **[...]**.

#### <a name="hyperlinks"></a>Köprüler

- Bir köprü denetiminin etkin olduğunda asla kırmızı yanıp sönmediğini doğrulayın. Bu, renk hizmetinin kullanılmadığının bir göstergesidir

- Kullanılan VS Renkleri'nin aşağıdakiler olduğunu doğrulayın:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Bir paragrafta gömülü olmadıkça köprülerin altı çizili olmayan mavi göründüğünü doğrulayın.

#### <a name="check-boxes"></a>Onay kutuları

- Onay kutusunda çok satırlı metin varsa, kutunun tüm satırlarda dikey olarak ortalanmış değil, ilk metin satırıyla hizalandığından doğrulayın.

- Onay kutularının her zaman ikili bir seçim gösterdiğini ve kullanıcıda gezinmeyin veya yeni pencereler veya sayfalar açmayın.

- Onay kutusu giriş denetimiyle ilgili bir seçenek sunuyorsa, ilişkisini belirtmek için sola ve bu denetimin çok yakınına konumlandırılmış olduğunu doğrulayın.

- Bir onay kutusunun bir iletişim kutusunun veya sayfanın tüm içeriğini etkinleştirmek için **hiçbir zaman** araç olarak kullanılmadığını doğrulayın.

#### <a name="group-boxes"></a>Grup kutuları

- Bir iletişim kutusunun içinde iletişim kutusunun tüm içeriğini içeren tek bir grup kutusu içermediğini doğrulayın.

- Her grup kutusu içinde en az iki denetim olduğundan doğrulayın.

- Nadiren bir iletişim kutusunda ikiden fazla grup kutusu olmalıdır.

- İç içe grup kutusu olmadığını doğrulayın.

### <a name="icons"></a>Simgeler

- Karanlık temada simgelerin doğru şekilde ters çevrilmiş olarak göründüğünü doğrulayın.

- Tüm simgelerin temel kavramlara dayandığını doğrulayın.

- Her simgenin farklı, tanınması kolay ve ikiden fazla kavram içermediğini (durum değiştirici/dil olmadan) doğrulayın.

- Temel simgenin boşluk içinde ortalanmış olarak göründüğünü doğrulayın.

- Yüksek Karşıtlık modunda tüm simgelerin okunaklı göründüğünü doğrulayın.

- Kullanılan herhangi bir rengin renk kullanım standartlarıyla uyumlu olduğunu doğrulayın.

- Simgelerin etrafında hale (kenarlıklar) olmadığını doğrulayın. (Varsa, hale bitişik UI'nin arka plan rengiyle eşleşmelidir).

### <a name="touch-enabled-ui"></a>Dokunmatik özellikli ui

- Etkileşimli denetimlerin kolayca dokunabilen kadar büyük olduğunu doğrulayın - en az **23x23 piksel** boyutunda

- En sık kullanılan denetimlerin en az **40x40 piksel** boyutunda olduğunu doğrulayın.

- Etkileşimli **denetimlerin** aralarında en az 5 piksel aralık olduğunu doğrulayın
