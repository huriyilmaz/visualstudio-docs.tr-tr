---
title: XAML canlı önizleme ile masaüstü uygulaması kullanıcı arabirimini yakalama ve düzenleme
description: masaüstü uygulaması kullanıcı arabirimini yakalamak, Visual Studio içinde yinelemeli değişiklikler yapmak ve bu değişiklikleri gerçek zamanlı olarak görüntülemek için xaml dinamik yeniden yükleme ile xaml canlı önizlemesini eşleştirin.
ms.date: 11/08/2021
ms.topic: conceptual
helpviewer_keywords:
- xaml edit
- xaml live preview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
monikerRange: vs-2022
ms.openlocfilehash: 0f5839bc7f05afb4f4e91db4608a9b30687aca8d
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132002620"
---
# <a name="xaml-live-preview-capture-and-edit-desktop-app-ui"></a>XAML canlı önizlemesi: masaüstü uygulaması kullanıcı arabirimini yakalama ve düzenleme

xaml canlı önizlemesi sayesinde, bir masaüstü uygulamasının kullanıcı arabirimini (uı) yakalayabilir ve Visual Studio içinde yerleşik bir pencereye getirebilirsiniz. böylece, uygulamayı değiştirmek için [XAML sık yeniden yükleme](xaml-hot-reload.md) kullanımını daha kolay hale getirebilir ve bu değişiklikleri yaptığınız zaman gerçek zamanlı olarak görüntüleyebilirsiniz.

:::image type="content" source="media/vs-2022/xaml-live-preview.gif" alt-text="XAML canlı önizlemesi 'nin eylemde gösterildiği bir animasyon.":::

## <a name="xaml-live-preview-window"></a>XAML canlı önizleme penceresi

XAML canlı önizleme penceresi hata ayıklama sırasında kullanılabilir. açmak için,   >    >  **XAML canlı önizleme** Windows hata ayıkla sayfasına gidin.

:::image type="content" source="media/vs-2022/xaml-live-preview-menu.png" alt-text="Hata ayıklama menü çubuğundan XAML canlı önizleme seçeneğinin ekran görüntüsü.":::

Ya da uygulama araç çubuğunda **xaml canlı önizleme 'de göster** düğmesini seçin.

:::image type="content" source="media/vs-2022/xaml-live-preview-toolbar.png" alt-text="Uygulama araç çubuğundan XAML canlı önizlemesi seçeneğinin ekran görüntüsü.":::

### <a name="scrolling-and-zooming"></a>Kaydırma ve yakınlaştırma

Kaydırma çubuklarıyla kaydırmanın yanı sıra aşağıdaki etkileşimleri de kullanabilirsiniz:

- Fare tekerleği, dikey ve yatay (fareniz destekliyorsa).
- Hem dikey hem de yatay bir dokunmatik yüzey iki parmakla kaydırma.
- Fare sürükleme eylemiyle eşleştirilmiş bir **CTRL** tuşuna basın.

Yakınlaştırma için aşağıdaki etkileşimleri de kullanabilirsiniz:

- Sol alt köşedeki yakınlaştırma/kapatma düğmeleri.
-  + Bir klavye kullanmayı tercih ediyorsanız CTRL **artı işareti** (+) veya **CTRL**+ + **eksi işareti** (-) klavye kısayoluna basın.
- Fare tekerleği eylemiyle eşleştirilmiş bir **CTRL** tuşuna basın veya dokunmatik yüzey ile yakınlaştırma eylemi. Bir fare kullanmanın ek bir ödülü denetim alanı bulundurma.

:::image type="content" source="media/vs-2022/xaml-live-preview-scroll-zoom.gif" alt-text="XAML canlı Önizlemedeki kaydırma ve yakınlaştırma eylemlerinin animasyonu.":::

### <a name="element-selection"></a>Öğe seçimi

XAML canlı Önizlemedeki öğe seçimi, çalışan bir uygulamadaki seçime benzer. Canlı görsel ağaçta veya kaynak XAML 'de öğeleri bulmanıza olanak tanır.

:::image type="content" source="media/vs-2022/xaml-live-preview-element-selection.gif" alt-text="XAML canlı önizlemede öğe seçimi eyleminin animasyonu.":::

Öğe seçimi, ilk dört araç çubuğu düğmesi (soldan sağa) tarafından denetlenir.

:::image type="content" source="media/vs-2022/xaml-live-preview-toolbar-selection.png" alt-text="Öğe seçimi için XAML Canlı Önizleme araç çubuğu düğmelerinin ekran görüntüsü.":::

Araç çubuğu düğmeleri aşağıdaki eylemleri üretir:

- **Öğe seçimi** , öğe seçimi eylemini başlatır; diğer bir deyişle, farenizi XAML canlı Önizlemedeki uygulama içeriğinin üzerine taşırken öğeleri vurgular. Bir öğeye tıkladığınızda, canlı görsel ağaçta seçilir. Ayrıca, **Önizleme seçili öğe** etkinse kaynağına gider ve kaynak xaml kullanılabilir. Bu davranış, canlı görsel ağaç ile aynıdır.
- **Seçim sırasında öğe bilgisini göster** fare altındaki öğeyle ilgili boyut, renk ve yazı tipi bilgilerinin görüntülenmesini denetleyen bir iki durumlu düğmedir.
- **Yalnızca kendı xaml** , hangi öğelerin vurgulanmasını denetleyen bir iki durumlu düğmedir: tümü veya yalnızca kaynak xaml içeren öğeler çözümde kullanılabilir. Bu davranış, canlı görsel ağaç ile aynıdır.
- **Seçili öğenin önizlemesi** , bir öğe SEÇILDIĞINDE kaynak xaml 'e gezinmeyi denetleyen bir iki durumlu düğmedir. Varsayılan olarak kapalıdır. Bu davranış, canlı görsel ağaç ile aynıdır.

### <a name="rulers"></a>Cetveller

Cetveller uygulamanızdaki öğeleri hizalamanıza yardımcı olur. Bunlar, uygulama birimlerinde, önceki cetvele kadar olan mesafeyi görüntüler. Bu şekilde, uygulamanızın farklı parçaları arasındaki uzaklıkları doğrulamaya yardımcı olurlar.

:::image type="content" source="media/vs-2022/xaml-live-preview-rulers.gif" alt-text="Ve cetvelin eylemde animasyonunu.":::

Araç çubuğu düğmelerinin ikinci grubu, cetvelleri aşağıdaki gibi denetler (soldan sağa):

:::image type="content" source="media/vs-2022/xaml-live-preview-toolbar-rulers.png" alt-text="XAML canlı önizleme sürümündeki ikinci cetvel grubu araç çubuğu düğmelerinin ekran görüntüsü.":::

- **Dikey cetvel ekleyin**. Tek bir dikey cetvel ekler. Bir satırda bu düğmeye birkaç kez tıklarsanız, mevcut cetvellere çakışmayacak şekilde yeni cetveller yerleştirir.
- **Yatay cetvel ekleyin**. Dikey cetvele benzer tek bir yatay cetvel ekler.
- **Tüm cetvelleri kaldırın**. Tüm cetvelleri zaman ortadan kaldırır.
- **Cetvel rengini seçin**. Cetvellerin rengini değiştirir.
- **Cetvel görünürlüğünü değiştirin**. Tek bir tıklama ile tüm cetvelleri gizler veya gösterir.

Cetveller klavye kullanımı kolay. Bunların çevresinde sekme ekleyebilirsiniz. Tek seferde cetvelleri bir piksel taşımak için ok tuşlarını kullanabilir veya aynı anda 10 uygulama birimi ile taşımak için ok tuşlarıyla birlikte **CTRL** tuşuna basabilirsiniz. **Del** tuşu Şu anda seçili olan cetveli siler. Ayrıca, etiketin yakınında **cetveli Sil** düğmesini seçerek fareyle bir cetveli silebilirsiniz.

Öğe seçimi kullanılırken bir öğenin etrafına cetveller de ekleyebilirsiniz. Sağ tıklama dikey cetveller ekler. Yatay cetveller eklemek için sağ tıkladığınızda **SHIFT** tuşunu basılı tutun.

:::image type="content" source="media/vs-2022/xaml-live-preview-outline-rulers.gif" alt-text="Ve XAML canlı Önizlemedeki bir görüntünün anahattına nasıl cetveller ekleyebileceğiniz animasyonu.":::

### <a name="multi-window-applications"></a>Çoklu pencere uygulamaları

Uygulamanızda birden çok pencere varsa, pencere açılan kutusunu kullanarak hangi pencerenin görüntüleneceğini seçebilirsiniz. Veya önizlemek istediğiniz penceredeki uygulama araç çubuğunda bulunan **xaml canlı önizleme 'de göster** düğmesini kullanın.

:::image type="content" source="media/vs-2022/xaml-live-preview-change-window.gif" alt-text="XAML canlı Önizlemedeki çoklu pencere uygulaması özelliğinin animasyonu.":::

## <a name="supported-platforms"></a>Desteklenen platformlar

Visual Studio 2022 ' nin ilk sürümü aşağıdaki platformları ve hata ayıklama senaryolarını destekler.

|Platform  |Öğe seçimi & bilgi Ipucu  |Cetveller  |
|---------|---------|---------|
|WPF      |Yes         |Yes         |
|UWP      |Yes         |Yes         |
|WinUI3 Masaüstü     |Hayır         |Yes         |
|MAUı (Android Emulator)     |Hayır         |Evet (px *)         |
|Xamarin 5.0 + (Android Emulator)     |Hayır          |Evet (px *)         |

> [!NOTE]
> Yukarıdaki tabloda, (* * px * * *) piksel cinsinden görüntülenen cetvelleri belirtir; diğer tüm platformlar, bir izleyicinin DPI 'sını temel alan platform birimlerinde bilgi görüntüler.

## <a name="limitations"></a>Sınırlamalar

XAML canlı önizlemesi, bir uygulama ekran görüntüsünü saniyede birkaç kez yakalayıp ve [PrintWindow](/windows/win32/api/winuser/nf-winuser-printwindow)gibi kullanılabilir API 'leri kullanarak çalışıyor. Aşağıdaki sınırlamalara tabidir:

- Uygulama penceresinin bir bölümü ekran kapalıysa, bu bölümün XAML sık yükleme değişikliklerini görüntülemesi olasıdır.
- Bir pencere, &mdash; &mdash; WDA_EXCLUDEFROMCAPTURE veya [DwmsetwindowDWMWA_CLOAK Attribute](/windows/win32/api/dwmapi/nf-dwmapi-dwmsetwindowattribute) Ile [Setwindowdisplayaffinity](/windows/win32/api/winuser/nf-winuser-setwindowdisplayaffinity) KULLANıLARAK, ekran görüntüsü yakalama ve xaml canlı önizlemesi için kullanılamaz hale gelebilir.

## <a name="next-steps"></a>Sonraki adımlar

Xaml canlı önizleme ile yakından birlikte bulunan [xaml dinamik yeniden yükleme](xaml-hot-reload.md)hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio 2022 sürüm notları](/visualstudio/releases/2022/release-notes-preview)
