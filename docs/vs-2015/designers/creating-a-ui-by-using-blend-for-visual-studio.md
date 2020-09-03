---
title: Blend kullanarak Kullanıcı arabirimi oluşturma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
ms.assetid: efd12263-cc2d-4081-a2bb-9a2cc17c442c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a65f42dafca696bfa638964b825410b576d4845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544293"
---
# <a name="creating-a-ui-by-using-blend-for-visual-studio"></a>Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için Blend XAML tabanlı Windows Masaüstü, Web, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)ve [Windows Mağazası](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) uygulamaları tasarlamanıza yardımcı olur. Visual Studio ile aynı temel XAML tasarım deneyimini sağlar ve animasyonlar ve davranışlar gibi gelişmiş görevler için görsel tasarımcılar ekler.

 Visual Studio için Blend, Visual Studio 'nun bir parçası olarak eklendiğinden, bunu indirmeniz gerekmez. Bununla birlikte, sisteminizde yüklemek üzere Visual Studio yükleyicisi 'nde seçmeniz gerekir.

 Visual Studio için Blend yeni başladıysanız, çalışma alanının benzersiz özellikleri hakkında bilgi sahibi olmak için biraz zaman ayırın. Bu konu, sizi hızlı bir tura götürür.

> [!NOTE]
> Çalışma yüzeyi, belge anahattı penceresi ve cihaz penceresi gibi paylaşılan tasarım özelliklerine ilişkin tura geçmek için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 **Bu konuda**:

- [Araçlar paneli turu](#Tools)

- [Varlıklar paneli turu](#Assets)

- [Nesneler ve Zaman Çizelgesi paneli turu](#Objects)

- [Özellikler panelinin turu](#Properties)

## <a name="tour-of-the-tools-panel"></a><a name="Tools"></a> Araçlar paneli turu
 Uygulamanızdaki nesneleri oluşturmak ve değiştirmek için Visual Studio için Blend **Araçlar** panelini kullanabilirsiniz. Nesneleri bir araç seçip çalışma yüzeyinde farenizle çizerek bir araç seçerek oluşturursunuz.

 ![Araçlar paneli](../designers/media/blend5toolspanel.png "Blend5Toolspanel")

|Görüntü|Araç türü|Görüntü|Araç türü|
|-|-|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Seçim araçları** Nesneleri ve yolları seçin.<br /><br /> İç içe geçmiş nesneler ve yol kesimleri seçmek için **doğrudan seçim** aracını kullanın.|![Belirtme A](../designers/media/b5-label-a.png "b5_label_A")|**Gradyan ve fırça araçları**|
|![](../designers/media/b1-2.png "B1_2")|**Araçları görüntüle** Kaydırma ve yakınlaştırma gibi çalışma yüzeyi görünümünü ayarlayın.|![Belirtme çizgisi B](../designers/media/b5-label-b.png "b5_label_B")|**Yol araçları**|
|![](../designers/media/b1-3.png "B1_3")|**Fırça araçları** Bir nesnenin görsel öznitelikleriyle çalışın (örneğin, fırçayı dönüştürme, nesne boyama veya bir nesnenin özniteliklerini başka bir nesneye uygulamak gibi).|![Belirtme çizgisi C](../designers/media/b5-label-c.png "b5_label_C")|**Şekil araçları**|
|![](../designers/media/b1-4.png "B1_4")|**Nesne araçları** Çalışma yüzeyinde, yollar, şekiller, düzen bölmeleri, metin ve denetimler gibi en yaygın nesneleri çizin.|![Belirtme çizgisi D](../designers/media/b5-label-d.png "b5_label_D")|**Düzen bölmeleri**|
|![](../designers/media/b1-5.png "B1_5")|**Varlık araçları** **Varlıklar** paneline erişin ve kütüphanedeki en son kullanılan varlığı göstermek için.|![Belirtme çizgisi](../designers/media/b5-label-e.png "b5_label_E")|**Metin denetimleri**|
|||![Belirtme çizgisi F](../designers/media/b5-label-f.png "b5_label_F")|**Ortak denetimler**|

 **Kısa bir video izleyin:** [araç çubuğunun](https://www.youtube.com/watch?v=VkdUJcvoo54&list=PLBDF977B2F1DAB358&index=4) ![yüklü özelliklerini yapılandırın](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") .

## <a name="tour-of-the-assets-panel"></a><a name="Assets"></a> Varlıklar paneli turu
 Visual Studio 'daki **araç kutusuna** benzer şekilde, **varlıklar** panelinde tüm denetimleri bulabilirsiniz. Denetimlere ek olarak, **varlıklar** panelinde stiller, medya, davranışlar ve efektler dahil olmak üzere çalışma yüzeyinizi ekleyebileceğiniz her şeyi bulabilirsiniz.

 ![Varlıklar paneli](../designers/media/blend5-assets-panel.png "Blend5_Assets_panel")

|Görüntü|Description|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Arama kutusu** Varlık listesini filtrelemek için **arama** kutusuna yazın.|
|![](../designers/media/b1-2.png "B1_2")|**Kılavuz modu ve liste modu** **Kılavuz modu** görünümü Ile varlıkların **liste modu** görünümü arasında geçiş yapın.|
|![](../designers/media/b1-3.png "B1_3")|**Varlık kategorileri** Bu kategorideki varlıkların listesini görüntülemek için bir kategori veya alt kategori ' ye tıklayın.|
|![](../designers/media/b1-4.png "B1_4")|**Stiller** Kaynak sözlüğünde bulunan tüm stilleri görüntüleyin.|
|![](../designers/media/b1-5.png "B1_5")|**Açıklama** Seçili varlıklar kategorisi veya alt kategorisinin açıklamasını görüntüleyin.|

## <a name="tour-of-the-objects-and-timeline-panel"></a><a name="Objects"></a> Nesneler ve Zaman Çizelgesi paneli turu
 Çalışma yüzeyinizdeki nesneleri düzenlemek ve isterseniz bunlara animasyon uygulamak için bu paneli kullanın.

 ![Animasyon modundaki nesne ve zaman çizelgesi paneli](../designers/media/b5-object-timeline-animation.png "b5_object_timeline_animation")

|Görüntü|Description|
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Nesne görünümü** Bir belgenin görsel ağacını görüntüleyin. Farklı ayrıntı düzeylerinde ayrıntıya gidebilirsiniz. Çalışma yüzeyinde daha fazla nesne düzenlemek için Katmanlar da ekleyebilirsiniz. Böylece bunları bir grup olarak kilitleyebilir ve gizleyebilirsiniz.|
|![](../designers/media/b1-2.png "B1_2")|**Kayıt modu göstergesi** Özellik değişikliklerini bir zaman çizelgesinde kayıt yapıp görmeyeceğinizi öğrenin.|
|![](../designers/media/b1-3.png "B1_3")|**Görsel taslak seçici** Oluşturduğunuz film şeritleri listesini görüntüleyin.|
|![](../designers/media/b1-4.png "B1_4")|**Görsel Taslağı kapat** Geçerli görsel taslağı kapatın.|
|![](../designers/media/b1-5.png "B1_5")|**Görsel taslak seçenekleri** Görsel Taslağı oluşturun, çoğaltın, ters çevirin, silin, yeniden adlandırın veya kapatın.|
|![](../designers/media/b1-6.png "B1_6")|**Kayıttan yürütme denetimleri** Zaman çizelgesinde ilerleyin. Ayrıca, zaman çizelgesinde gezinmek için (veya *Temizleme*) oynatma kafasını sürükleyebilirsiniz.|
|![](../designers/media/b1-7.png "B1_7")|**Kapsam** dön Nesneleri önceki kök nesneye veya önceki kapsama geri görünümü olarak kapsam. Bunu yalnızca bir stili veya şablonu değiştirirken yapabilirsiniz.|
|![](../designers/media/b1-8.png "B1_8")|**Ana kare kaydetme** Geçerli zaman noktasındaki seçili nesnenin özelliklerinin anlık görüntüsünü kaydeder.|
|![](../designers/media/b1-9.png "B1_9")|**Yaslama seçenekleri** Zaman çizelgesi yaslaması, yaslama çözünürlüğü ayarlayın ve zaman çizelgesi yaslamasını kapatın.|
|![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209")|**Göster/Gizle**, **Kilitle/kilidini aç** nesneler görünümü için görünürlük ve kilitleme seçeneklerini göster veya gizle.|
|![](../designers/media/b1-11.png "B1_11")|**Zaman çizelgesindeki oynatma kafası konumu** Geçerli saati milisaniye cinsinden gösterin. Zaman içinde belirli bir noktaya atlamak için bu alana doğrudan bir zaman değeri girebilirsiniz. Duyarlık, **yapışma seçeneklerinde**ayarlanan yaslama çözünürlüğüne bağlıdır.|
|![](../designers/media/b1-12.png "B1_12")|**Oynatma kafası** Animasyonun hangi noktaya olduğunu saptayın. Animasyonun önizlemesini görüntülemek için, oynatma kafasını zaman çizelgesi boyunca sürükleyebilirsiniz.|
|![](../designers/media/b1-13.png "B1_13")|**Zaman çizelgelerinde ayarlanan ana kareler** Bir özellik değerini belirli bir zaman noktasında değiştirin.|
|![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe")|**Nesnelerin sırasını değiştirme** Nesnelerin görüntüleme sırasını ayarlayın. Yapı görünümündeki nesneleri Z düzeninde (önden arkaya) veya biçimlendirme sırasına göre ( **xaml** görünümünde göründükleri sırada) düzenlemek için bu düğmeye tıklayın.|
|![](../designers/media/b1-15.png "B1_15")|**Zaman çizelgesi yakınlaştırma** Zaman çizelgesinin yakınlaştırma çözünürlüğünü ayarlayın. Yakınlaştırma bir animasyonu daha ayrıntılı düzenlemenize izin verir ve uzaklaştırmaysa daha uzun süreler boyunca neler olduğuna ilişkin daha kapsamlı bir özet gösterir. Yakınlaştırma yapar, ancak zaman içinde istediğiniz konumunda bir ana kare ayarlayamazsınız, yaslama çözünürlüğünün yeterince yüksek olarak ayarlandığını doğrulayın.|
|![Belirtme çizgisi 16](../designers/media/b5-label-16.png "b5_label_16")|**Zaman çizelgesi bileşim alanı** Zaman çizelgesini görüntüleyin ve sürükleyerek veya kısayol menülerini kullanarak ana kareleri taşıyın.|

## <a name="tour-of-the-properties-panel"></a><a name="Properties"></a> Özellikler panelinin turu
 Bir nesnenin özelliklerini görüntülemek ve değiştirmek için bu paneli kullanın. Bunları doğrudan çalışma yüzeyinde da ayarlayabilirsiniz. Bunu yaparsanız, özellik değişiklikleri **Özellikler** panelinde yansıtılır.

 ![Özellikler paneli](../designers/media/blend5-properties-panel.png "Blend5_properties_panel")

 **Kategoriler** Özelliklerin kategorilerini genişletin ve daraltın. **Expand** ![](../designers/media/6375953d-074c-421a-bbb3-6f5055b67b64.png "6375953d-074C-421a-BBB3-6f5055b67b64") Kategori ayrıntılarını göstermek veya gizlemek için Genişlet ' e tıklayın ve ![Daralt](../designers/media/b5-collapse-button.png "b5_collapse_button") ' ı **daraltın** .

|                                                                                                         |                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                 ![](../designers/media/b1-1.png "B1_1")                                 |                                                                              **Ad ve tür** Seçili nesnenin simgesini, adını ve türünü görüntüleyin.                                                                              |
|                                 ![](../designers/media/b1-2.png "B1_2")                                 |                                                                          **Düzenleme ölçütü** Özellikleri ada, kaynağa veya kategoriye göre alfabetik olarak düzenleyin.                                                                          |
|                                 ![](../designers/media/b1-3.png "B1_3")                                 |                                                        **Fırça özellikleri** Fırça, vuruş fırçası ve ön plan fırçası gibi fırçalar için görsel özelliklerini ayarlayın.                                                        |
|                                 ![](../designers/media/b1-4.png "B1_4")                                 |                                                                                    **Renk düzenleyici** Düz renk ve gradyan fırçaları için kullanın.                                                                                    |
|                                 ![](../designers/media/b1-5.png "B1_5")                                 |                                                                                                 **Renk seçici** Bir renk seçin.                                                                                                 |
|                                 ![](../designers/media/b1-6.png "B1_6")                                 |                                                                              **Renk yongaları** Başlangıç rengini, geçerli rengi ve son rengi görüntüleme                                                                               |
|                                 ![](../designers/media/b1-7.png "B1_7")                                 | **Damlalıklar** Ekranınızdaki herhangi bir öğenin rengini kullanın. **Renk damlalığı** , **düz renk fırçası** seçildiğinde kullanılabilir. Gradyan **damlalığı** , **gradyan fırçası** seçildiğinde kullanılabilir. |
|                                 ![](../designers/media/b1-8.png "B1_8")                                 |                                                                        **Özellikler ve olaylar** Seçili bir öğe için özellikleri ayarlayın veya olayları seçin.                                                                         |
|                                 ![](../designers/media/b1-9.png "B1_9")                                 |                                                         **Arama kutusu** Özellikleri arayın. **Arama** kutusuna yazarak görüntülenen özellikleri filtreleyin.                                                          |
| ![](../designers/media/97fa60b9-0caf-4387-9225-b57510d32209.png "97fa60b9-0caf-4387-9225-b57510d32209") |                                **Fırça Düzenleyicisi sekmeleri** Bir fırça Düzenleyicisi seçmek için kullanın. **Fırça**, **düz renk fırçası**, **gradyan fırçası**, **kutucuk fırçası**veya **fırça kaynağı**seçeneklerinden birini belirleyebilirsiniz.                                |
|                                ![](../designers/media/b1-11.png "B1_11")                                |                                    **Renk kaynakları** Farklı özelliklere tam olarak aynı rengi uygulayın. **Renk kaynakları** sekmesi, **yerel kaynakları** ve **sistem kaynaklarını**içerir.                                    |
|                                ![](../designers/media/b1-12.png "B1_12")                                |                                                 **RGB renk alanı** **R**,  **G**veya **B** (kırmızı, yeşil, mavi) sayı düzenleyicilerinin değerlerini ayarlayarak rengi değiştirin.                                                  |
|                                ![](../designers/media/b1-13.png "B1_13")                                |                                                                        **Alfa kanalı** ' **Nin yanında bulunan**sayı düzenleyicisini kullanarak alfa değerini değiştirin.                                                                        |
| ![](../designers/media/d839d12c-07a1-4127-a830-4a8e7069f4fe.png "d839d12c-07a1-4127-a830-4a8e7069f4fe") |                                       **Rengi kaynağa Dönüştür** Seçili rengi bir renk kaynağına dönüştürün. Renk kaynakları sekmesine tıkladığınızda renk kaynakları kullanılabilir.                                        |
|                                ![](../designers/media/b1-15.png "B1_15")                                |                                                                                 **Onaltılık değer** Görüntülenecek rengin onaltılık değerini görüntüleyin.                                                                                 |
|                     ![Belirtme çizgisi 16](../designers/media/b5-label-16.png "b5_label_16")                     |                                                                                **Gradyan kaydırıcı** Yalnızca bir gradyan fırçası seçiliyse görünür.                                                                                 |
| ![](../designers/media/d50027a1-6824-4ad8-8b4e-558b0756dcf8.png "d50027a1-6824-4ad8-8b4e-558b0756dcf8") |                                                                     **Gelişmiş özellikleri göster** Yaygın olarak kullanılan özelliklerin kategorilerini görüntüleyin.                                                                      |

 **Kısa bir video izleyin:** ![yüklü Özellikler](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [Özellikler panelini](https://www.youtube.com/watch?v=HCqQfiobdag&list=PLBDF977B2F1DAB358&index=7)yapılandırma.

## <a name="see-also"></a>Ayrıca Bkz.
 [Denetimleri ekleme ve davranışlarını değiştirme](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md) [nesneleri](../designers/animate-objects-in-xaml-designer.md) , [Visual Studio ve Visual Studio için Blend xaml tasarlayan](../designers/designing-xaml-in-visual-studio.md) [şekil ve yollar çizme](../designers/draw-shapes-and-paths.md)
