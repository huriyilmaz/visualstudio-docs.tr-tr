---
title: Visual Studio için Düzen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698401"
---
# <a name="layout-for-visual-studio"></a>Visual Studio İçin Düzen
Visual Studio iletişim kutularının çoğunluğu, standart [Windows Masaüstü iletişim kutusu düzen ilkelerini](/windows/desktop/uxguide/win-dialog-box)izleyen temalı iletişim kutuları olan [araç kutusu yerleşimidir](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout). Visual Studio, Kullanıcı arabirimini yenilemeye yönelik olarak taşındıkça, daha belirgin birçok iletişim kutusu, bunları ürün tanımlama deneyimleri olarak belirleyen yeni bir tasarıma sahiptir. Bu [temalı iletişim kutusu düzeninde](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) temalı bir görünüm vardır.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Yardımcı program iletişim kutusu düzeni

- Yardımcı program iletişim kutusundaki tüm denetimler üst/sol tarafta ve aşağı doğru bir şekilde başlamalıdır.

- Bir iletişim kutusunda büyük bir alanı dolduracak denetimleri hiçbir şekilde ortalayın.

- Tüm iletişim metni için ortam yazı tipini kullanın. Görsel bir belirtim yazarken, belirli bir yazı tipi ve boyut seçmek yerine ortam yazı tipini belirtin. [Ortam yazı tipine](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)bakın.

- Güncel denetim aralığı ve yerleşimini, craftsmansevkiyat 'daki kalite için hedefi desteklemek üzere kullanın.

- İletişim kutuları, çok sayıda denetimden daha karmaşık hale gelebilir, denetimlerin benzersiz bir juxtaposition veya her ikisi de olabilir. Bu karmaşık durumlar için, Kullanıcı tarafından ayrıştırılacak bir mantıksal akış sağlamak üzere denetim gruplandırmaları arasında yeterli alana izin verin.

### <a name="utility-dialog-layout-examples"></a>Yardımcı program iletişim kutusu düzen örnekleri
 Tüm boyutlar piksel olarak ifade edilir.

 ![Denetimlerin üzerindeki etiketler için iletişim kutusu aralığı](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Şekil 08,01-a: denetimlerin üzerindeki etiketlerle yardımcı program iletişimleri için boşluk yönergeleri**

 ![Denetimlerin sol tarafındaki Etiketler için iletişim kutusu aralığı](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Şekil 08,01-b: denetimlerin sol tarafındaki etiketlerin bulunduğu yardımcı program iletişim kutuları için boşluk yönergeleri**

### <a name="layout-details"></a>Düzen ayrıntıları

#### <a name="margins"></a>Kenar boşlukları

- Tüm iletişim kutularında tüm kenarlar etrafında 12 piksellik bir kenarlık olmalıdır.

- Bir grup çerçevesinin içindeki kenar boşlukları çerçevenin kenarından 9 piksel olmalıdır.

- Sekme denetimi içindeki kenar boşlukları sekme denetiminin kenarından 6 piksel olmalıdır.

#### <a name="command-buttons"></a>Komut düğmeleri

- Komut düğmeleri, içerikte değil, iletişim kutusu çerçevesinde çalışır. Bu kişiler sağ alt kısımdaki bir yere yerleştirilmelidir ve düğmeleri birbirinden ayrı ayrı ayarlamak için yukarıdaki yeterli değişken alanına sahip olmalıdır.

- İletişim kutusunda çalışan yatay düğmeler varsa, alternatif komut düğmesi yapılandırması, sağ üst köşedeki dikey bir yığındır. Aşağıdaki [iç komut düğmelerine](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) bakın.

- Komut düğmelerinin solundaki boşluk (iletişim kutusunun sol alt/orta), iletişim kutusu işlem denetimlerinin "bant" parçası olarak değerlendirilir. Bu alanda intrude gereken tek şey, genel görev veya iletişim kutusuyla ilgili bir yardım bağlantıdır.

- Komut düğmeleri 75x23 piksel olmalıdır.

- Komut düğmeleri 6 piksel dışında olmalıdır.

  ![Temel düğme hizalaması](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Şekil 08,01-c: temel düğme hizalaması**

#### <a name="labels"></a>Etiketler

- Tüm etiketleri sola hizalayın.

- Bir denetimin üzerine oturacak Etiketler için, bu, aşağıdaki denetimle tam olarak sola hizalanmalıdır ve etiketin altı, diğer denetimin üst kısmında 5 piksel olmalıdır (örneğin, Birleşik giriş kutusu).

- Denetimlerin soluna oturlan Etiketler için, etiket ve giriş denetimi arasındaki en küçük genişlik 10 pikseldir. Metin kutularını, Birleşik giriş kutularını veya diğer denetimleri hizalamak için örtük bir ikinci sütun oluşturulmalıdır.

- Etiketler tümce durumdur ve ardından iki nokta üst üste gelir. Bkz. [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Denetimler arasındaki mesafe
 Yığın denetimleri makul bir şekilde. Yığın denetimleri arasındaki boşluk için mutlak kılavuz yok. Denetimler arasındaki sıkı işlem, iletişim kutuları arasında biraz farklılık gösterebilir. Önerilen Aralık, dikey denetim/etiket çiftleri için 20 piksel ve yatay denetim/etiket çiftleri için 9 piksel olur. Yatay çiftler için en düşük denetim aralığı 6 pikseldir.

 ![Denetimler arasında önerilen uzaklık](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Şekil 08,01-d: denetimler arasındaki mesafe için öneriler**

#### <a name="control-indentation"></a>Denetim girintileme
 Denetimler iç içe olduğunda, iç denetimleri yukarıdaki denetimin sol kenarı ile yatay olarak hizalayın, genellikle etiketi.

 ![İç içe denetim hizalaması](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Şekil 08,01-e: Iç Içe denetim hizalaması**

#### <a name="control-width"></a>Denetim genişliği
 Metin kutusunun veya diğer benzer denetimlerin genişliği alanın ortalama girişinden daha uzun olmamalıdır. Ortalama Ingilizce kelime beş karakterdir. Örneğin, uzun yol adı gerektiren bir metin kutusu, yatay düzen izin verdiği sürece, platform adları için bir açılan menü yalnızca en uzun girdiye izin veren bir uzunluk olmalıdır.

#### <a name="helper-text"></a>Yardımcı metin

- İletişim kutusu, iletişim kutusunun amacı hakkında daha fazla bilgi sağlayan yardımcı metni görüntüleyebilir. Bu genellikle en üstte bulunur ve 1-2 cümle olabilir.

- Bir kullanıcının ayrıştırması ve okuması için satır uzunluğu rahat bir genişlik olmalıdır. Orta bir iletişim kutusu 550 pikselden daha fazla olmamalıdır.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> İç komut düğmeleri
 Daha karmaşık iletişim kutularında, iç denetim kendi ilgili düğmelerine sahip olabilir ve bu da iletişim kutusunun tamamlama düğmelerinin nerede olduğunu etkileyebilir.

- **OK** / Sağ alt köşede, Tamam**iptali** yatay olarak yönlendirildiğinizde, iç düğmelerden oluşan dikey bir hizalama (sütun) kullanın.

- **OK** / Sağ üst köşede, Tamam**iptali** dikey olarak yönlendirildiğinden, iç düğmelerin yatay hizalamasını (satır) kullanın. Bu durum daha az yaygındır.

- İç düğme boyutu, mümkün olduğunda **Tamam** / **iptal** düğmelerinin boyutuyla eşleşen 75x23 piksellik standart düğme boyutunu hedeflemelidir. Düğme etiketi, düğmeyi standart düğme boyutunu aşarsa, bu küme içindeki diğer düğmelerin bu geniş boyutla hizalanması gerekir.

  ![Yatay Tamam ve Iptal düğmeleri](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Şekil 08,01-f: yatay Tamam/Iptal ile dikey Iç düğmeler**

  ![Dikey Tamam ve Iptal düğmeleri](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Şekil 08,01-g: dikey Tamam/Iptal ile yatay iç düğmeler**

#### <a name="browse-button"></a>[Gözatmaya...] Bu
 **[Gözatmaya...]** bir metin kutusunu izleyen düğmelerin "Gözatmalıdır..." şeklinde yazım denetimi yapmanız gerekir. tam olarak, üç nokta da dahil. Boşluk sıkışık varsa veya ekranda birden çok **[gözatılan...]** düğmeleri varsa, düğme yalnızca üç nokta olacak şekilde azaltılabilir.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Temalı iletişim kutusu düzeni
 Visual Studio 'daki temalı iletişim kutularının daha hafif bir görünümü vardır ve daha fazla boşluk sunun. Tipografi, daha fazla açık satır aralığı ve yazı tipi boyutu ve kalınlıklarla ilgili daha fazla karakter sunan daha fazla vurgulama sağlar. Mümkün olduğunda Chrome ve başlık çubukları düşürüldü veya kaldırılmıştır. Bu iletişim kutularının düzeni şu temel düzeni izlemelidir:

1. İletişim kutusunun arka planı beyazdır.

2. Orta değer gri değerinde 1 piksellik bir kural kenarlığı vardır.

3. İletişim kutusu başlığı artık bir başlık çubuğunda yer alınmaz, ancak görsel ilgi ve daha büyük bir nokta boyutunda vurgu sağlar. ( [Metin stilindeki](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)yazı tipi boyutu bölümüne bakın.)

4. Açıklama gibi ek metinle bağlanmış Etiketler, **ortam yazı tipi + kalın**olmalıdır.

5. İç sütunlar, açık gri olan 1 piksellik bir kuralla ayrılır.

6. Varsayılan bağlantıların alt çizgi yoktur. Üzerine gelme ve basılan durumlar renk değişikliğine ve alt çizgilere sahiptir.

7. Sağ alt köşedeki kaydet düğmeleri ( **Tamam** / **iptal**gibi).

### <a name="themed-dialog-layout-examples"></a>Temalı iletişim kutusu düzen örnekleri
 ![Temalı iletişim kutusu düzeni](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Şekil 08,01-h: temalı iletişim kutusu**

 ![Temalı iletişim kutusu boyutları](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Şekil 08,01-ı: temalı iletişim kutusu-Boyutlar**

 ![Temalı iletişim kutusu yazı tipleri](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Şekil 08,01-j: temalı iletişim kutusu-yazı tipleri**

 ![Temalı iletişim kutusu renkleri](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Şekil 08,01-k: temalı iletişim kutusu-renkler**

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Denetimler (Windows)](/windows/desktop/uxguide/controls)
- [İletişim kutuları (Windows)](/windows/desktop/uxguide/win-dialog-box)
