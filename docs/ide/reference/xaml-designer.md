---
title: XAML Tasarımcısı seçenekleri sayfası
description: XAML belgelerinize öğelerin ve özniteliklerin nasıl XAML Tasarımcısı belirtmek için genel bölümündeki Genel sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
- VS.ToolsOptionsPages.XAML_Designer.General
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- uwp
ms.openlocfilehash: 01832b96a9505a9883896cc60027e2029d6b3b45
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724886"
---
# <a name="xaml-designer-options-page"></a>XAML Tasarımcısı seçenekleri sayfası

XAML **XAML Tasarımcısı** öğelerin ve özniteliklerin nasıl biçimlendiril olduğunu belirtmek için XAML Tasarımcısı seçenekleri sayfasını kullanın. Bu sayfayı açmak için Araçlar menüsünü **ve** ardından Seçenekler'i **seçin.** Bir özellik **XAML Tasarımcısı** erişmek için XAML Tasarımcısı **seçin.** Ayarlar için XAML Tasarımcısı, belgeyi açabilirsiniz. Bu nedenle, ayarlarda değişiklik yaptıysanız, değişiklikleri görmek için ayarları kapatıp Visual Studio açmanız gerekir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri **ve Dışarı Ayarlar'yi** seçin.  Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../environment-settings.md#reset-settings)

## <a name="enable-xaml-designer"></a>XAML Tasarımcısı

Bu ayar seçildiğinde, bu ayar XAML Tasarımcısı. Bu XAML Tasarımcısı, XAML belgelerini düzenlemeniz için görsel bir çalışma alanı sağlar. Kaynaklarda intellisense Visual Studio veri bağlama gibi belirli işlevler için verilerin etkinleştirilmesi XAML Tasarımcısı gerekir.

Aşağıdaki ayarlar yalnızca XAML Tasarımcısı geçerlidir. Bu seçeneği değiştirirseniz, ayarın etkili olması Visual Studio yeniden başlatmanız gerekir.

## <a name="default-document-view"></a>Varsayılan belge görünümü

XAML belgeleri yüklendiğinde Tasarım görünümü olup olmadığını kontrol etmek için bu ayarı kullanın.

|Ad|Açıklama|
|-|-|
|**Kaynak Görünümü**|XAML görünümünde yalnızca XAML kaynağının görünür olup olmadığını belirtir. Bu, büyük belgeleri yüklerken yararlıdır.|
|**Tasarım Görünümü**|XAML görünümünde yalnızca XAML Tasarımcısı görüntü olup olmadığını belirtir.|
|**Bölünmüş Görünüm**|Hem görselin hem XAML Tasarımcısı XAML kaynağının XAML görünümünde (Bölme Yönü ayarına göre konum) yanında görünip **görünmeyemeyeceklerini** belirtir.|

## <a name="split-orientation"></a>Yönlendirmeyi Bölme

Bir XAML belgesini düzenlerken uygulamanın ne XAML Tasarımcısı ve nasıl görüntülendiğinde denetim için bu ayarı kullanın. Bu ayarlar yalnızca Varsayılan **belge görünümü Bölünmüş Görünüm** olarak ayarlanmış olduğunda **geçerlidir.**

|Ad|Açıklama|
|-|-|
|**Dikey**|XAML kaynağı XAML görünümünün sol tarafında, XAML Tasarımcısı ise diğer tarafta görünür.|
|**Yatay**|Bu XAML Tasarımcısı XAML görünümünün en üstünde görünür ve XAML kaynağı bunun altında görünür.|
|**Varsayılan**|XAML belgesi, belgenin projesi tarafından hedeflenen platform için önerilen bölme yönlendirmesini kullanır. Çoğu platform için bu, Yatay ile **eşdeğerdir.**|

## <a name="zoom-by-using"></a>kullanarak yakınlaştırma

XAML belgesini düzenlerken yakınlaştırmanın nasıl çalıştığını belirlemek için bu ayarı kullanın.

|Ad|Açıklama|
|-|-|
|**Fare tekerleği**|Fare tekerleğini XAML Tasarımcısı ekranı yakınlaştırın.|
|**Ctrl + fare tekerleği**|Fare tekerleğini XAML Tasarımcısı **Ctrl tuşuna** basarak ekranı yakınlaştırın.|
|**Alt + fare tekerleği**|Fare tekerleğini XAML Tasarımcısı **Alt** tuşuna basarak ekranı yakınlaştırın.|

Bu ayarlar, bir XAML belgesini düzenlerken Tasarımcı davranışını belirler.

## <a name="default-zoom-setting"></a>Varsayılan Yakınlaştırma Ayarı

XAML belgesini görüntülemek için varsayılan yakınlaştırma değerini belirlemek için bu ayarı kullanın.

|Ad|Açıklama|
|-|-|
|**Son Kullanılan**|Varsayılan olarak tüm XAML belgeleri için son kullanılan yakınlaştırma değerini kullanın. Bir XAML belgesi ilk kez açıldığında yalnızca ilk kez "Hepsini Sığdır" ayarını kullanır.|
|**Hepsini Sığdır**|XAML tasarımcısı için yakınlaştırma değerini "Hepsini Sığdır" olarak ayarlamak için bu seçeneği kullanın. Bir XAML belgesi kapatılan ve yeniden açıldıklarında, son ayar değeri o oturum için kalıcı olur, ancak farklı oturumlar için varsayılan olarak "Hepsini Sığdır" kullanılır.|

Bu ayarlar, bir XAML belgesini düzenlerken Tasarımcı davranışını belirler.

|Ad|Açıklama|
|-|-|
|**Etkileşimli öğeleri oluşturma sırasında otomatik olarak adla**|Tasarımcı'ya bir ad eklerken yeni bir etkileşimli öğe için varsayılan adın sağlanacak olup olmadığını belirtir.|
|**Öğe oluşturma sırasında düzen özelliklerini otomatik olarak ekleme**|Tasarımcı'ya bir öğe eklerken düzen özelliklerinin yeni bir öğe için sağlanacak olup olmadığını belirtir. Düzen özellikleri, denetimin düzenini etkileyen özelliklerdir; örneğin Margin ve VerticalAlignment. Aşağıdaki XAML' de düğmenin bu seçenek seçili olmadan nasıl oluşturulacaklarını gösterir:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Çeyrek tabanlı düzen kullanma**|Seçili olan denetimin üst kapsayıcının en yakın kenarlarıyla uyumlu olup olmadığını belirtir. Bu onay kutusu temizse, taşıma veya oluşturma işlemi sırasında denetim hizalamaları değişmez.|
|**Araç kutusu öğelerini otomatik olarak doldurmak**|Geçerli çözümde kullanıcı denetimlerinin ve özel denetimlerin Araç Kutusunda otomatik olarak göster olup olmadığını belirtir.|

## <a name="settings-blend-only"></a>Ayarlar (yalnızca Blend)

Blend kullanarak XAML dosyalarını düzenlerken ayarları belirlemek için bu seçenekleri kullanın.

|Ad|Açıklama|
|-|-|
|**kullanarak yakınlaştırma**|Fare tekerleğini XAML Tasarımcısı veya fare tekerleğini kaydırırken **Ctrl** veya **Alt** tuşuna basarak ekranı yakınlaştırın.|
|**Tür birimleri**|Tasarımcıda ölçümlerin noktaları mı yoksa pikselleri mi temel alan olduğunu belirtir. Universal Windows Apps noktaları desteklemez, noktalar seçilirse birimler otomatik olarak **piksellere** dönüştürülür.|

## <a name="artboard-blend-only"></a>Çalışma Panosu (yalnızca Blend)

Blend'de XAML belgelerini düzenlerken XAML Tasarımcısı davranışını belirlemek için bu ayarları kullanın.

### <a name="snapping"></a>Yakalamaya

|Ad|Açıklama|
|-|-|
|**Yasla kılavuzu göster**|Bu seçenek seçildiğinde, denetimleri hizalamanıza yardımcı olmak için kılavuz çizgileri tasarımcıda görünür. Kılavuz çizgilerine yasla seçeneği seçildiğinde tasarımcıya eklenen denetimler bu **kılavuz çizgilerine** yaslar.|
|**Kılavuz çizgilerini yasla**|Denetimler tasarımcıya ekleniyor veya taşındığında kılavuz çizgilerine yaslar.|
|**Kılavuz çizgisi aralığı**|Kılavuz çizgileri arasındaki boşluğu piksel veya nokta cinsinden belirtir (Tür birimleri **ayarı tarafından belirlenir).**|
|**Yaslık çizgilere yasla**|Denetimlerin yaslık çizgilere yaslıtıp yaslanamay olmadığını belirtir.|
|**Varsayılan kenar boşluğu**|**Yaslama çizgilerini** yasla etkinleştirildiğinde, denetim ile yaslama çizgileri arasındaki aralığı piksel veya nokta cinsinden belirtir **(Tür birimleri ayarı tarafından belirlenir).**|
|**Varsayılan doldurma**|**Yaslama çizgilerini** yasla etkinleştirildiğinde, denetim ile yaslama çizgileri arasındaki ek aralığı piksel veya nokta cinsinden belirtir **(Tür birimleri ayarı tarafından belirlenir).**|

### <a name="animation"></a>Animasyon

Blend'de bağımlı (hızlandırılmış olmayan) animasyonlar etkinleştirildiğinde bir uyarının görüntü olup olmadığını belirlemek için bu ayarı kullanın.

### <a name="effects"></a>Etkiler

Blend kullanarak XAML dosyalarını düzenlerken etkilerin işlenecek olup olmadığını XAML Tasarımcısı için bu ayarları kullanın.

|Ad|Açıklama|
|-|-|
|**İşleme etkileri**|Blend kullanarak XAML dosyalarını düzenlerken etkilerin iş XAML Tasarımcısı belirtir.|
|**Yakınlaştırma eşiği**|İşleme etkileri onay kutusu seçildiğinde etkilerin hangi **yakınlaştırmada işlen** olduğunu belirtir. Bu ayarın ötesine ilerlerseniz, etkiler artık XAML Tasarımcısı.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [İzlenecek yol: İlk WPF masaüstü uygulamam](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
