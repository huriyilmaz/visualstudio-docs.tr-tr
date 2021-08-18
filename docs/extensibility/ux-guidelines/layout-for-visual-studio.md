---
title: Visual Studio | düzeni Microsoft Docs
description: Görünüme sahip Visual Studio iletişim kutuları ve yeni iletişim kutuları da dahil olmak üzere tüm iletişim kutularının düzeni hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ce29e7f2d8d75cf60423cbb65ca3b2da449e4c6c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094548"
---
# <a name="layout-for-visual-studio"></a>Visual Studio İçin Düzen
Bu iletişim Visual Studio çoğu, [](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)Masaüstü iletişim kutusu düzeni ilkelerine uygun, standart iletişim Windows iletişim kutuları olan Yardımcı iletişim [kutusu düzenidir.](/windows/desktop/uxguide/win-dialog-box) Kullanıcı Visual Studio yenilendiğinde, öne çıkan iletişim kutularının bazıları, bunları ürün tanımlama deneyimleri olarak belirleyen yeni bir tasarıma sahiptir. Bu [Themed iletişim kutusu](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) düzeni, bir görünüme sahiptir.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Yardımcı program iletişim kutusu düzeni

- Bir yardımcı program iletişim kutusundaki tüm denetimler üstten/soldan başlamalı ve aşağı doğru akmalı.

- Denetimleri hiçbir zaman büyük bir alanı doldurmak için bir iletişim kutusuna ortalayın.

- Tüm iletişim kutusu metni için ortam yazı tipini kullanın. Görsel bir özellik yazarken, belirli bir yazı tipi ve boyutu seçmek yerine ortam yazı tipini belirtin. Bkz. [Ortam yazı tipi.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)

- Üretimde kalite hedefini desteklemek için tutarlı denetim aralığı ve yerleşimi kullanın.

- İletişim kutuları daha fazla sayıda denetimden, denetimlerin benzersiz bir birliktelik özelliğinden veya her ikisinde de daha karmaşık hale geldi. Bu karmaşık durumlarda, kullanıcıya ayrıştıracak mantıksal bir akış vermek için denetim gruplamaları arasında yeterli alana izin ver.

### <a name="utility-dialog-layout-examples"></a>Yardımcı program iletişim kutusu düzeni örnekleri
 Tüm boyutlar piksel olarak ifade eder.

 ![Denetimlerin üzerindeki etiketler için iletişim kutusu aralığı](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Şekil 08.01-a: Denetimlerin üzerinde etiketleri olan yardımcı program iletişim kutuları için aralık yönergeleri**

 ![Denetimlerin sol tarafından etiketlerin iletişim kutusu aralığı](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Şekil 08.01-b: Denetimlerin sol tarafından etiketleri olan yardımcı program iletişim kutuları için aralık yönergeleri**

### <a name="layout-details"></a>Düzen ayrıntıları

#### <a name="margins"></a>Kenar boşlukları

- Tüm iletişim kutularının tüm kenarlarında 12 piksel kenarlık olması gerekir.

- Grup çerçevesi içindeki kenar boşlukları, çerçevenin kenarından 9 piksel olmalıdır.

- Sekme denetimi içindeki kenar boşlukları, sekme denetimi kenarından 6 piksel olmalıdır.

#### <a name="command-buttons"></a>Komut düğmeleri

- Komut düğmeleri, içerik üzerinde değil iletişim kutusu çerçevesinde çalışır. Bunlar sağ alta yerleştiril olmalı ve düğmeleri ayrı ayarlamak için yeterli değişken alana sahip olması gerekir.

- İletişim kutusunda çalışan yatay düğmeler varsa alternatif komut düğmesi yapılandırması sağ üst köşedeki dikey bir yığındır. Aşağıdaki [İç komut düğmelerine](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) bakın.

- Komut düğmelerinin sol tarafı (iletişim kutusunun sol alt/ortası) boşluk, iletişim kutusu işlem denetimlerinin "bant" parçası olarak kabul edilir. Bu alana müdahale edecek tek şey, genel görev veya iletişim kutusuyla ilgili bir Yardım bağlantısıdır.

- Komut düğmeleri 75x23 piksel olmalıdır.

- Komut düğmelerinin ayrı 6 piksel olması gerekir.

  ![Temel düğme hizalaması](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Şekil 08.01-c: Temel düğme hizalaması**

#### <a name="labels"></a>Etiketler

- Tüm etiketleri sola hizala.

- Bir denetimin üzerinde yer alan etiketler için, denetimin altındaki denetimle tam olarak sola hizalanması ve etiketin alt kısmında diğer denetimin üst kısmından (örneğin, birleşik giriş kutusu) 5 piksel yukarıda olması gerekir.

- Denetimlerin sol tarafından yer alan etiketler için etiket ile giriş denetimi arasındaki minimum genişlik 10 pikseldir. Metin kutularını, birleşik giriş kutularını veya diğer denetimleri hizalamak için örtülü ikinci bir sütun oluşturularak.

- Etiketler cümle büyük/küçük harflidir ve ardından iki nokta üst üste kullanılır. Bkz. [Metin stili.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

#### <a name="distance-between-controls"></a>Denetimler arasındaki uzaklık
 Yığın denetimleri makul bir şekilde. Yığılmış denetimler arasındaki boşluk için mutlak bir kılavuz yoktur. Denetimler arasındaki sıkılık, iletişim kutuları arasında biraz farklılık gösterebilir. Önerilen boşluk, dikey denetim/etiket çiftleri için 20 piksel ve yatay denetim/etiket çiftleri için 9 pikseldir. Yatay çiftler için minimum denetim aralığı 6 pikseldir.

 ![Denetimler arasında önerilen uzaklık](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Şekil 08.01-d: denetimler Öneriler mesafe için denetimler**

#### <a name="control-indentation"></a>Denetim girintisi
 Denetimler iç içe olduğunda iç denetimleri, genellikle etiket olan yukarıdaki denetimin sol kenarıyla yatay olarak hizalar.

 ![İç içe denetim hizalaması](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Şekil 08.01-e: İç içe denetim hizalaması**

#### <a name="control-width"></a>Denetim genişliği
 Metin kutusunun veya diğer benzer denetimlerin genişliği, alan için ortalama girişten daha uzun olmayacaktır. Ortalama İngilizce sözcük beş karakterdir. Örneğin, uzun bir yol adı gerektiren bir metin kutusu yatay düzenin izin olduğu sürece, platform adları için açılan liste ise yalnızca en uzun girişe izin veren bir uzunluk olmalıdır.

#### <a name="helper-text"></a>Yardımcı metin

- bir iletişim kutusu, iletişim kutusunun amacı hakkında daha fazla bilgi sağlayan yardımcı metni görüntüler. Bu genellikle en üstte yer alan ve 1-2 cümle olabilir.

- Satır uzunluğu, kullanıcının ayrıştırması ve okuması için rahat bir genişlik olmalıdır. Orta büyüklükteki bir iletişim kutusu en fazla 550 piksel genişliğinde olmalıdır.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> İç komut düğmeleri
 Daha karmaşık iletişim kutuları, iç denetimin kendi ilgili düğmelerine sahip olabilir ve bu da iletişim kutusunun işleme düğmelerinin bulunduğu yeri etkileyebilir.

- Tamam İptali sağ alt köşede yatay olarak yönlendirildiklerinde iç düğmelerin dikey hizalamasını /  (sütununu) kullanın.

- Tamam İptali sağ üst köşede dikey olarak yönlendirildiklerinde iç düğmelerin yatay hizalamasını /  (satırı) kullanın. Bu durum daha az yaygındır.

- İç düğme boyutu, mümkün olduğunda Tamam İptal düğmelerinin boyutuyla eşleşen standart düğme boyutunu 75x23 /  piksel olarak hedeflemeli. Düğme etiketi düğmenin standart düğme boyutunu aşarsa, bu kümede yer alan diğer düğmeler bu daha geniş boyutla hizalanmış olur.

  ![Yatay Tamam ve İptal düğmeleri](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Şekil 08.01-f: Yatay Tamam/İptal ile Dikey İç düğmeler**

  ![Dikey Tamam ve İptal düğmeleri](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Şekil 08.01-g: Dikey Tamam/İptal ile yatay iç düğmeler**

#### <a name="browse-button"></a>[Gözat...] Düğme
 **[Gözat...]** bir metin kutusunu takip edecek düğmeler "Gözat..." yazarak yazabilir üç nokta dahil olmak üzere tam olarak. Alan darsa veya ekranda birden çok **[Gözat...]** düğmesi varsa, düğme yalnızca üç nokta olacak şekilde azaltabilirsiniz.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Themed dialog layout
 Görünümde Visual Studio iletişim kutuları daha açık görünür ve daha fazla boşluk sağlar. Tipografi daha fazla vurgu ve ilgi sağlar ve daha fazla açık satır aralığı ile yazı tipi boyutları ile ağırlıklarının bir varyasyonu sunar. Mümkün olduğunca, chrome ve başlık çubukları azaltıldı veya kaldırıldı. Bu iletişim kutularının düzeni şu temel deseni izlemeli:

1. İletişim kutusunun arka planı beyazdır.

2. Orta değer grisinde 1 piksel kural kenarlığı vardır.

3. İletişim kutusu başlığı artık bir başlık çubuğunda yer alıyor, ancak daha büyük bir nokta boyutunda görsel ilgi ve vurgu sağlar. (Metin stili'nin yazı tipi [boyutu bölümüne bakın.)](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

4. Açıklama gibi ek metinlerle birlikte etiketlerin Ortam yazı tipi **+ Kalın olması gerekir.**

5. İç sütunlar açık gri renkle 1 piksellik bir kuralla ayrılır.

6. Varsayılan bağlantılarda alt çizgi yoktur. Üzerine gelindiğinde ve basıldığında bir renk değişikliği artı alt çizgi vardır.

7. Yürütme düğmeleri **(Tamam** / **İptal gibi)** sağ alt köşede bulunur.

### <a name="themed-dialog-layout-examples"></a>Themed dialog layout examples
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Şekil 08.01-h: Themed iletişim kutusu**

 ![Themed dialog dimensions](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Şekil 08.01-i: Themed iletişim kutusu - Boyutlar**

 ![Temalı iletişim kutusu yazı tipleri](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Şekil 08.01-j: Temalı iletişim kutusu - Yazı Tipleri**

 ![Temalı iletişim kutusu renkleri](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Şekil 08,01-k: temalı iletişim kutusu-renkler**

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Denetimler (Windows)](/windows/desktop/uxguide/controls)
- [İletişim kutuları (Windows)](/windows/desktop/uxguide/win-dialog-box)
