---
title: XAML Tasarımcısı seçenekleri sayfası
description: Öğelerin ve özniteliklerin XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için XAML Tasarımcısı bölümünde Genel sayfasını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0955a6644e8f1dc1d42a1b22b15399a6d1ca452d
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560986"
---
# <a name="xaml-designer-options-page"></a>XAML Tasarımcısı seçenekleri sayfası

Öğelerin ve özniteliklerin XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için **XAML Tasarımcısı** seçenekleri sayfasını kullanın. Bu sayfayı açmak için **Araçlar** menüsünü ve ardından **Seçenekler**' i seçin. **XAML Tasarımcısı** Özellik sayfasına erişmek için **XAML Tasarımcısı** düğümünü seçin. XAML Tasarımcısı ayarları, belgeyi açtığınızda uygulanır. Bu nedenle, ayarlarda değişiklik yaparsanız değişiklikleri görmek için Visual Studio 'Yu kapatıp yeniden açmanız gerekir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>XAML Tasarımcısı etkinleştir

Seçildiğinde, bu ayar XAML Tasarımcısı etkinleştirilir. XAML Tasarımcısı XAML belgelerini düzenlemeniz için görsel bir çalışma alanı sağlar. Visual Studio 'da kaynak ve veri bağlama için IntelliSense gibi bazı işlevler, XAML Tasarımcısı etkinleştirilmesini gerektirir.

Aşağıdaki ayarlar yalnızca XAML Tasarımcısı etkin olduğunda geçerlidir. Bu seçeneği değiştirirseniz, ayarın etkili olması için Visual Studio 'Yu yeniden başlatmanız gerekir.

## <a name="default-document-view"></a>Varsayılan belge görünümü

XAML belgeleri yüklendiğinde Tasarım görünümü görünüp başlatılmayacağını denetlemek için bu ayarı kullanın.

|Ad|Açıklama|
|-|-|
|**Kaynak görünümü**|XAML görünümünde yalnızca XAML kaynağının görünüp başlatılmayacağını belirtir. Büyük belgeler yüklenirken bu faydalıdır.|
|**Tasarım Görünümü**|XAML görünümünde yalnızca bir görsel XAML Tasarımcısı görünüp başlatılmayacağını belirtir.|
|**Bölünmüş görünüm**|Hem görsel XAML Tasarımcısı hem de XAML kaynağının XAML görünümünde bir diğerinin yanında görünüp görünmediğini belirtir ( **bölünmüş yön** ayarına göre konum).|

## <a name="split-orientation"></a>Yönü Böl

XAML belgesi düzenlenirken XAML Tasarımcısı ne zaman ve nasıl görüneceğini denetlemek için bu ayarı kullanın. Bu ayarlar yalnızca **varsayılan belge görünümü** **bölünmüş görünüme** ayarlandığında geçerlidir.

|Ad|Açıklama|
|-|-|
|**Dikey**|Xaml kaynağı XAML görünümünün sol tarafında görünür ve XAML Tasarımcısı diğer tarafta görüntülenir.|
|**Yatay**|XAML Tasarımcısı XAML görünümünün üst kısmında görünür ve XAML kaynağı bunun altında görünür.|
|**Varsayılan**|XAML belgesi, belge projesinin hedeflediği platform için önerilen bölünmüş yönlendirmeyi kullanır. Çoğu platformda bu **yatay** olarak eşdeğerdir.|

## <a name="zoom-by-using"></a>Kullanarak Yakınlaştır

Bir XAML belgesi düzenlenirken yakınlaştırmanın nasıl çalıştığını anlamak için bu ayarı kullanın.

|Ad|Açıklama|
|-|-|
|**Fare tekerleği**|Fare tekerleğini kaydırarak XAML Tasarımcısı yakınlaştırın.|
|**Ctrl + fare tekerleği**|Fare tekerleğini kaydırırken **CTRL** tuşuna basarak XAML Tasarımcısı yakınlaştırın.|
|**Alt + fare tekerleği**|Fare tekerleğini kaydırırken **alt** tuşuna basarak XAML Tasarımcısı yakınlaştırın.|

Bu ayarlar bir XAML belgesi düzenlenirken tasarımcı davranışını belirlenir.

|Ad|Açıklama|
|-|-|
|**Etkileşimli öğeleri oluşturma sırasında otomatik olarak Adlandır**|Tasarımcıya bir tane eklediğinizde yeni bir etkileşimli öğe için varsayılan bir ad verilip verilmeyeceğini belirtir.|
|**Öğe oluşturma üzerine düzen özelliklerini otomatik olarak ekle**|Tasarımcıya bir tane eklediğinizde yeni bir öğe için Düzen özelliklerinin verilip verilmeyeceğini belirtir. Düzen özellikleri, bir denetimin yerleşimini etkileyen, örneğin Margin ve VerticalAlignment olanlardır. Aşağıdaki XAML, bu seçenek seçili olmadan ve ile bir düğmenin nasıl oluşturulduğunu gösterir:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Çeyrek tabanlı düzeni kullan**|Seçili olan denetimin üst kapsayıcının en yakın kenarlarına hizalanacağını belirtir. Bu onay kutusu silinirse, bir taşıma veya oluşturma işlemi sırasında denetim hizalamaları değişmez.|
|**Araç kutusu öğelerini otomatik olarak doldur**|Geçerli çözümdeki Kullanıcı denetimlerinin ve özel denetimlerin araç kutusunda otomatik olarak gösterilip gösterilmeyeceğini belirtir.|

## <a name="settings-blend-only"></a>Ayarlar (yalnızca Blend)

Blend kullanarak XAML dosyalarını düzenlenirken ayarları öğrenmek için bu seçenekleri kullanın.

|Ad|Açıklama|
|-|-|
|**Kullanarak Yakınlaştır**|Fare tekerleğini kaydırarak veya fare tekerleğini kaydırırken **CTRL** ya da **Alt** tuşuna basarak XAML Tasarımcısı yakınlaştırın.|
|**Tür birimleri**|Tasarımcıda ölçümlerin noktalara veya piksellere dayalı olup olmadığını belirtir. Evrensel Windows uygulamaları noktaları desteklemediğinden, **işaret** seçilirse birimler otomatik olarak piksellere dönüştürülür.|

## <a name="artboard-blend-only"></a>Çalışma yüzeyi (yalnızca Blend)

Blend 'de XAML belgelerini düzenlenirken XAML Tasarımcısı davranışını öğrenmek için bu ayarları kullanın.

### <a name="snapping"></a>Yaslama

|Ad|Açıklama|
|-|-|
|**Yaslama kılavuzunu göster**|Bu seçenek belirlendiğinde, denetimleri hizalamaya yardımcı olmak için tasarımcıda kılavuz çizgileri belirir. **Kılavuza yapış** seçeneği belirlendiğinde tasarımcıya eklenen denetimler bu kılavuz çizgilerine ek olarak eklenir.|
|**Kılavuz çizgilerine yasla**|Tasarımcı etrafına denetimler eklendiğinde veya taşındığında, kılavuz çizgilere yaslar.|
|**Kılavuz çizgisi aralığı**|Kılavuz çizgileri arasındaki boşluğu piksel veya punto ( **tür birimleri** ayarı tarafından belirlendiği şekilde) ile belirtir.|
|**Ek bileşen çizgilere yasla**|Denetimlerin ek çizgi çizgilere eklenip eklenmeyeceğini belirtir.|
|**Varsayılan kenar boşluğu**|**Anlık görüntü çizgilere yapış** etkinleştirildiğinde, denetim ve anlık görüntü çizgileri arasındaki aralığı piksel veya punto ( **tür birimleri** ayarı tarafından belirlendiği gibi) olarak belirtir.|
|**Varsayılan doldurma**|**Anlık görüntü çizgilere yapış** etkinleştirildiğinde, denetim ve anlık görüntü çizgileri arasındaki ek boşluğu piksel veya noktalara ( **tür birimleri** ayarı tarafından belirlendiği gibi) belirtir.|

### <a name="animation"></a>Animasyon

Blend 'de bağımlı (hızlandırılmayan) animasyonlar etkinleştirildiğinde bir uyarının görünüp başlatılmayacağını anlamak için bu ayarı kullanın.

### <a name="effects"></a>Etkiler

Blend kullanarak XAML Tasarımcısı XAML dosyaları düzenlenirken efektlerin işlenip işlenmeyeceğini anlamak için bu ayarları kullanın.

|Ad|Açıklama|
|-|-|
|**İşleme efektleri**|Blend kullanarak XAML Tasarımcısı XAML dosyalarını düzenlenirken efektlerin işlenip işlenmeyeceğini belirtir.|
|**Yakınlaştırma eşiği**|**İşleme etkileri** onay kutusu seçildiğinde efektlerin işleme yüzdesini belirtir. Bu ayarın ötesine yaklaşırsanız, efektler artık XAML Tasarımcısı işlemez.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [İzlenecek yol: İlk WPF masaüstü uygulamam](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
