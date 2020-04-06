---
title: Visual Studio için Düzen | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698401"
---
# <a name="layout-for-visual-studio"></a>Visual Studio İçin Düzen
Visual Studio iletişim kutularının çoğu, standart [Windows Masaüstü iletişim düzeni ilkelerini](/windows/desktop/uxguide/win-dialog-box)izleyen temalı iletişim kutuları olan Yardımcı Bilgi Programı iletişim [düzenidir.](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout) Visual Studio ui'sini yenilemek için harekete geçtiğinde, daha belirgin iletişim kurullarından bazıları, bunları ürün tanımlayıcı deneyimler olarak tanımlayan yeni bir tasarıma sahiptir. Bu [Temalı iletişim düzeni](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) temalı bir görünüme sahiptir.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Yardımcı iletişim düzeni

- Yardımcı program iletişim kutusundaki tüm denetimler üst/soldan başlayıp aşağı doğru akmalıdır.

- Büyük bir alanı doldurmak için denetimleri asla bir iletişim kutusunda ortalamayın.

- Tüm iletişim metni için ortam yazı tipini kullanın. Görsel bir spec yazarken, belirli bir yazı tipi ve boyutu seçmek yerine ortam yazı tipini belirtin. [Bkz. ortam yazı tipi.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)

- Işçilikte kalite hedefini desteklemek için tutarlı kontrol aralıklarını ve yerleşimlerini kullanın.

- İletişim kutuları daha fazla sayıda denetimden, benzersiz bir denetim yan yana gelmesinden veya her ikisinden daha karmaşık hale gelebilir. Bu karmaşık durumlar için, kontrol gruplandırmaları arasında yeterli boşluk kullanıcıya ayrıştırmak için mantıksal bir akış vermek için izin verin.

### <a name="utility-dialog-layout-examples"></a>Yardımcı iletişim düzeni örnekleri
 Tüm boyutlar piksel olarak ifade edilir.

 ![Denetimlerin üzerindeki etiketler için iletişim aralığı](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Şekil 08.01-a: Denetimlerin üzerinde etiketleri olan yardımcı iletişim kutuları için boşluk yönergeleri**

 ![Denetimlerin solundaki etiketler için iletişim aralığı](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Şekil 08.01-b: Denetimlerin solunda etiketleri olan yardımcı iletişim kutuları için boşluk yönergeleri**

### <a name="layout-details"></a>Düzen ayrıntıları

#### <a name="margins"></a>Kenar boşlukları

- Tüm iletişim kutularının tüm kenarlarında 12 pikselkenarlı olmalıdır.

- Grup çerçevesi içindeki kenar boşlukları çerçevenin kenarından 9 piksel olmalıdır.

- Sekme denetimindeki kenar boşlukları sekme denetiminin kenarından 6 piksel olmalıdır.

#### <a name="command-buttons"></a>Komut düğmeleri

- Komut düğmeleri iletişim çerçevesi üzerinde çalışır, içerikte değil. Sağ alt ada yerleştirilmeli ve düğmeleri ayrı olarak ayarlamak için yukarıda yeterli değişken alanı olmalıdır.

- İletişim kutusunda çalışan yatay düğmeler varsa, alternatif komut düğmesi yapılandırması sağ üstteki dikey yığındır. Aşağıdaki [İç komut düğmelerine](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) bakın.

- Komut düğmelerinin solundaki boşluk (iletişim kutusunun sol alt/ortası) iletişim işlemi denetimlerinin "bandının" bir parçası olarak kabul edilir. Bu alana izinsiz girebilecek tek şey, genel görev veya iletişim kutusuyla ilgili bir Yardım bağlantısıdır.

- Komut düğmeleri 75x23 piksel olmalıdır.

- Komut düğmeleri 6 piksel arayla olmalıdır.

  ![Temel düğme hizalaması](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Şekil 08.01-c: Temel düğme hizalaması**

#### <a name="labels"></a>Etiketler

- Tüm etiketleri sol hizala.

- Denetimin üzerinde yer alan etiketler için, alttaki denetimle tam olarak sol hizalamalı ve etiketin alt kısmı diğer denetimin üst kısmından 5 piksel yukarıda olmalıdır (örneğin, açılan kutu).

- Denetimlerin solunda bulunan etiketler için, etiket ile giriş denetimi arasındaki minimum genişlik 10 pikseldir. Metin kutularını, açılan kutuları veya diğer denetimleri hizalamak için zımni bir ikinci sütun oluşturulmalıdır.

- Etiketler cümle durumu ve bir üst üste tarafından takip edilir. Bkz. [Metin stili.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

#### <a name="distance-between-controls"></a>Denetimler arasındaki mesafe
 Yığın kontrolleri makul. Yığılmış denetimler arasındaki boşluk için mutlak bir kılavuz yoktur. Denetimler arasındaki sıkılık iletişim ler arasında biraz farklılık gösterebilir. Önerilen aralık dikey kontrol/etiket çiftleri için 20 piksel, yatay kontrol/etiket çiftleri için 9 pikseldir. Yatay çiftler için minimum kontrol aralığı 6 pikseldir.

 ![Denetimler arasında önerilen mesafe](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Şekil 08.01-d: Kontroller arasındaki mesafe için öneriler**

#### <a name="control-indentation"></a>Kontrol girintisi
 Denetimler iç içe geçtiğinde, iç denetimleri genellikle etiket olan denetimin sol kenarıyla yatay olarak hizala.

 ![İç içe denetleme hizalaması](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Şekil 08.01-e: İç içe kontrol hizalaması**

#### <a name="control-width"></a>Kontrol genişliği
 Bir metin kutusunun veya diğer benzer denetimlerin genişliği, alanın ortalama girdisinden daha uzun olmamalıdır. Ortalama İngilizce kelime beş karakterdir. Örneğin, uzun bir yol adı gerektiren bir metin kutusu yatay düzenizin izin verdiği kadar uzun olmalıdır, platform adları için bir açılır yalnızca en uzun girişe izin veren bir uzunluk olmalıdır.

#### <a name="helper-text"></a>Yardımcı metin

- Bir iletişim kutusu, iletişim kutusunun amacı hakkında daha fazla bilgi sağlayan yardımcı metni görüntüleyebilir. Bu genellikle üst oturur ve 1-2 cümle olabilir.

- Satır uzunluğu, kullanıcının ayrıştması ve okuması için rahat bir genişlik olmalıdır. Orta iletişim kutusu en fazla 550 piksel genişliğinde olmalıdır.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>İç komut düğmeleri
 Daha karmaşık iletişim kutularında, iç denetimin kendi ilgili düğmeleri olabilir ve bu da iletişim kutusunun işleme düğmelerinin bulunduğu yeri etkileyebilir.

- **Ok**/**İptal** sağ alt köşesinde yatay olarak yönlendirildiğinde iç düğmelerden oluşan dikey bir hizalama (sütun) kullanın.

- **Ok**/**İptal** sağ üst köşesinde dikey olarak yönlendirildiğinde iç düğmelerden oluşan yatay bir hizalama (satır) kullanın. Bu durum daha az yaygındır.

- İç düğme boyutu, mümkün olduğunda **OK**/**İptal** düğmelerinin boyutuyla eşleşen 75x23 piksellik standart düğme boyutunu hedeflemelidir. Düğme etiketi düğmenin standart düğme boyutunu aşması durumunda, bu kümedeki diğer düğmeler bu daha geniş boyutta hizalanmalıdır.

  ![Yatay Tamam ve İptal düğmeleri](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Şekil 08.01-f: Yatay Ok/İptal ile Dikey İç düğmeleri**

  ![Dikey Tamam ve İptal düğmeleri](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Şekil 08.01-g: Dikey Ok/İptal ile yatay iç düğmeler**

#### <a name="browse-button"></a>[Gözatın...] Düğme
 **[Gözatın...]** metin kutusunu izleyen düğmelerde "Gözat..." yazmalıdır. elipsler de dahil olmak üzere tam olarak. Alan darsa veya ekranda birden fazla **[Gözat...]** düğmesi varsa, düğme sadece elipslere indirgenebilir.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Temalı iletişim düzeni
 Visual Studio'daki temalı diyaloglar daha hafif bir görünüme sahiptir ve daha fazla beyaz alan sunar. Tipografi daha fazla vurgu ve ilgi sağlayarak daha açık çizgi aralıkları ve yazı tipi boyutları ve ağırlıklarının bir varyasyonu sunar. Mümkün olduğunda, krom ve başlık çubukları azaltıldı veya kaldırıldı. Bu iletişim lerin düzeni aşağıdaki temel deseni izlemelidir:

1. İletişim kutusunun arka planı beyazdır.

2. Orta değerli gride 1 piksel kural kenarlığı vardır.

3. İletişim başlığı artık bir başlık çubuğunda bulunmaz, ancak daha büyük bir nokta boyutunda görsel ilgi ve vurgu sağlar. (Metin [stilinde](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)yazı tipi boyutu bölümüne bakın.)

4. Açıklama gibi ek metinle birleşen etiketler **Çevre yazı tipi + Kalın**olmalıdır.

5. İç sütunlar açık gri 1 piksel kuralı ile ayrılır.

6. Varsayılan bağlantıların alt puanı yoktur. Hover ve basılı devletler bir renk değişikliği artı altını çiziyor.

7. Commit düğmeleri **(Tamam**/**İptal**gibi) sağ alt köşede oturun.

### <a name="themed-dialog-layout-examples"></a>Temalı iletişim düzeni örnekleri
 ![Temalı iletişim düzeni](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Şekil 08.01-h: Temalı iletişim**

 ![Temalı iletişim boyutları](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Şekil 08.01-i: Temalı diyalog - Boyutlar**

 ![Temalı iletişim yazı tipleri](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Şekil 08.01-j: Temalı iletişim kutusu - Yazı Tipleri**

 ![Temalı iletişim renkleri](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Şekil 08.01-k: Temalı iletişim kutusu - Renkler**

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Denetimler (Windows)](/windows/desktop/uxguide/controls)
- [İletişim Kutuları (Windows)](/windows/desktop/uxguide/win-dialog-box)
