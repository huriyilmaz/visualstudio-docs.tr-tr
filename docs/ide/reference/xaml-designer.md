---
title: XAML Tasarımcı seçenekleri sayfası
ms.date: 03/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
- VS.ToolsOptionsPages.XAML_Designer.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9a925e7f3c31b8347148c15b050692fcee26fcb1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585619"
---
# <a name="xaml-designer-options-page"></a>XAML Tasarımcı seçenekleri sayfası

Öğelerin ve özniteliklerin XAML belgelerinizde nasıl biçimlendiğini belirtmek için **XAML Designer** seçenekleri sayfasını kullanın. Bu sayfayı açmak için **Araçlar** menüsünü seçin ve ardından **Seçenekler'i**seçin. **XAML Designer** özellik sayfasına erişmek için **XAML Designer** düğümadını seçin. Belgeyi açtığınızda XAML Tasarımcısı ayarları uygulanır. Bu nedenle, ayarlarda değişiklik yaparsanız, değişiklikleri görmek için Visual Studio'yu kapatıp yeniden açmanız gerekir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünde **Ayarlar İçe Ve Dışa Aktar'ı** seçin. Daha fazla bilgi [için, ayarları Sıfırla'ya](../environment-settings.md#reset-settings)bakın.

## <a name="enable-xaml-designer"></a>XAML Tasarımcısını Etkinleştir

Seçildiğinde, bu ayar XAML Tasarımcısı'nı etkinleştirirken. XAML Tasarımcısı, XAML belgelerini görüntülemeniz için görsel bir çalışma alanı sağlar. Kaynaklar ve veri bağlama için IntelliSense gibi Visual Studio'daki belirli işlevler, XAML Tasarımcısının etkinleştirilmesini gerektirir.

Aşağıdaki ayarlar yalnızca XAML Designer etkinleştirildiğinde geçerlidir. Bu seçeneği değiştirirseniz, ayarın etkili olması için Visual Studio'yu yeniden başlatmanız gerekir.

## <a name="default-document-view"></a>Varsayılan belge görünümü

XAML belgeleri yüklendiğinde Tasarım görünümünün görünüp görünmediğini denetlemek için bu ayarı kullanın.

|||
|-|-|
|**Kaynak Görünümü**|XAML görünümünde yalnızca XAML kaynağının görünüp görünmediğini belirtir. Bu, büyük belgeleri yüklerken kullanışlıdır.|
|**Tasarım Görünümü**|XAML görünümünde yalnızca görsel bir XAML Tasarımcısının görünüp görünmediğini belirtir.|
|**Görünümü Böl**|Hem görsel XAML Tasarımcısı'nın hem de XAML kaynağının XAML görünümünde **(Split Oryantasyon** ayarına dayalı konum) yan yana görünüp görünmediğini belirtir.|

## <a name="split-orientation"></a>Bölünmüş Oryantasyon

XAML belgesini düzenlerken XAML Tasarımcısının ne zaman ve nasıl görüneceklerini denetlemek için bu ayarı kullanın. Bu ayarlar yalnızca **Varsayılan belge görünümü** Split **Görünümü**olarak ayarlandığında geçerlidir.

|||
|-|-|
|**Dikey**|XAML kaynağı XAML görünümünün sol tarafında, XAML Tasarımcısı ise diğer tarafta görünür.|
|**Yatay**|XAML Tasarımcısı XAML görünümünün üst kısmında, XAML kaynağı ise altında görünür.|
|**Varsayılan**|XAML belgesi, belgenin projesi tarafından hedeflenen platform için önerilen bölünmüş yönlendirmeyi kullanır. Çoğu platform için bu **Yatay**eşdeğerdir.|

## <a name="zoom-by-using"></a>Kullanarak yakınlaştırma

Bir XAML belgesini düzenlerken yakınlaştırmanın nasıl çalıştığını belirlemek için bu ayarı kullanın.

|||
|-|-|
|**Fare tekerleği**|Fare tekerleği kaydırarak XAML Tasarımcısını yakınlaştırın.|
|**Ctrl + fare tekerleği**|Fare tekerleğinde kaydırma yaparken **Ctrl** tuşuna basarak XAML Tasarımcısını yakınlaştırın.|
|**Alt + fare tekerleği**|Fare tekerleği kaydırırken **Alt** tuşuna basarak XAML Tasarımcısını yakınlaştırın.|

Bu ayarlar, Bir XAML belgesini düzenlerken Tasarımcı davranışını belirler.

|||
|-|-|
|**Oluşturma da etkileşimli öğeleri otomatik olarak adlandırın**|Tasarımcıya bir tane eklediğinizde, yeni bir etkileşimli öğe için varsayılan bir ad sağlanıp sağlanmadığını belirtir.|
|**Öğe oluşturmada otomatik olarak düzen özelliklerini ekleme**|Tasarımcıya bir tane eklediğinizde düzen özelliklerinin yeni bir öğe için sağlanıp sağlanmadığını belirtir. Düzen özellikleri, kenar boşluğu ve Dikey Hizalama gibi bir denetimin düzenini etkileyen özelliklerdir. Aşağıdaki XAML, bu seçenek seçili ve seçilmeden bir Düğmenin nasıl oluşturulduğunu gösterir:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Dörtgen tabanlı düzeni kullanma**|Şu anda seçili denetimin üst kapsayıcının en yakın kenarlarına hizalanıp hizalamadığını belirtir. Bu onay kutusu temizlenirse, denetim hizalamaları taşıma sırasında değişmez veya işlem oluşturur.|
|**Araç kutusu öğelerini otomatik olarak doldurma**|Geçerli çözümdeki kullanıcı denetimlerinin ve özel denetimlerin Araç Kutusu'nda otomatik olarak gösterip gösterilmediğini belirtir.|

## <a name="settings-blend-only"></a>Ayarlar (Yalnızca karışım)

Karışım'ı kullanarak XAML dosyalarını düzenlerken ayarları belirlemek için bu seçenekleri kullanın.

|||
|-|-|
|**Kullanarak yakınlaştırma**|Fare tekerleğikaydırarak veya fare tekerleğinde kaydırma yaparken **Ctrl** veya **Alt** tuşuna basarak XAML Tasarımcısını yakınlaştırın.|
|**Tip birimleri**|Tasarımcıüzerindeki ölçümlerin puanlara mı yoksa piksellere mi dayandığını belirtir. Evrensel Windows Uygulamaları noktaları desteklemediği için, **Puan** seçilirse birimler otomatik olarak piksele dönüştürülür.|

## <a name="artboard-blend-only"></a>Artboard (Sadece Karışım)

Karışım'da XAML belgelerini düzenlerken XAML Tasarımcısı davranışını belirlemek için bu ayarları kullanın.

### <a name="snapping"></a>Yakalamaya

|||
|-|-|
|**Tutturma ızgarası göster**|Bu seçenek seçildiğinde, denetimleri hizalamanıza yardımcı olmak için tasarımcıda ızgara çizgileri görünür. Gridlines'a Tutturma seçeneği seçildiğinde, tasarımcıya eklenen denetimler bu ızgara **çizgilerine** tutturun.|
|**Gridlines'a tutturma**|Denetimler eklendiğinde veya tasarımcının etrafında taşındığında, ızgara çizgilerine yapıştılar.|
|**Izgara çizgisi aralığı**|Piksel veya noktalardaki Kılavuz çizgilerarasındaki aralığı belirtir **(Tür birimleri** ayarına göre belirlenir).|
|**Snapline'a yapışma**|Denetimlerin snapline yapışıp yapışmadığını belirtir.|
|**Varsayılan kenar boşluğu**|**Snap to snaplines** etkinleştirildiğinde, denetim ile piksel veya noktalardaki snaplines arasındaki aralığı belirtir **(Tür birimleri** ayarına göre belirlenir).|
|**Varsayılan dolgu**|**Snap to snaplines** etkinleştirildiğinde, denetim ile piksel veya noktalardaki snaplines arasındaki ekstra aralığı belirtir **(Tür birimleri** ayarına göre belirlenir).|

### <a name="animation"></a>Animasyon

Karma'da bağımlı (hızlandırılmış olmayan) animasyonlar etkinleştirildiğinde bir uyarının görünüp görünmediğini belirlemek için bu ayarı kullanın.

### <a name="effects"></a>Etkiler

XAML Tasarımcısı'nda Blend'i kullanarak XAML dosyalarını düzenlerken efektlerin oluşturulup işlenmediğini belirlemek için bu ayarları kullanın.

|||
|-|-|
|**Efektleri oluşturma**|XAML Designer'da Blend'i kullanarak XAML dosyalarını düzenlerken efektlerin işleyip işlemediğini belirtir.|
|**Yakınlaştırma eşiği**|**Render efektleri** onay kutusu seçildiğinde hangi efektlerin işlendiği yakınlaştırma yüzdesini belirtir. Bu ayarın ötesine yakınlaştırırsanız, efektler artık XAML Tasarımcısı'nda işlemez.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [İzlenecek Yol: İlk WPF masaüstü uygulamam](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
