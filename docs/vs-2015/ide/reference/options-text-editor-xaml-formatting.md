---
title: Seçenekler, metin düzenleyici, XAML, biçimlendirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 537223aab878aee2fb00e9417d0415f0a17d2dd5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534140"
---
# <a name="options-text-editor-xaml-formatting"></a>Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öğelerin ve özniteliklerin XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için **biçimlendirme** özelliği sayfasını kullanın. **Seçenekler** iletişim kutusunu açmak için **Araçlar** menüsüne ve ardından **Seçenekler**' e tıklayın. **Biçimlendirme** özelliği sayfasına erişmek Için **metin düzenleyici**, **xaml**, **biçimlendirme** düğümünü genişletin.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="auto-formatting-events"></a>Otomatik biçimlendirme olayları
Aşağıdaki olaylardan herhangi biri algılandığında otomatik biçimlendirme gerçekleşebilir.

- Bitiş etiketi veya basit etiket tamamlama.

- Başlangıç etiketinin tamamlanması.

- Panodan yapıştırılıyor.

- Klavye komutları biçimlendiriliyor.

  Hangi olayların otomatik biçimlendirmeye neden olduğunu belirtebilirsiniz.

|Name|Açıklama|
|-|-|
|**Bitiş etiketi veya basit etiket tamamlandığında**|Bir bitiş etiketi veya basit bir etiket yazmayı bitirdiğinizde otomatik biçimlendirme gerçekleşir. Basit bir etiketin öznitelikleri yoktur, örneğin `<Button />` .|
|**Başlangıç etiketi tamamlandığında**|Başlangıç etiketi yazmayı bitirdiğinizde otomatik biçimlendirme gerçekleşir.|
|**Panodan yapıştırılırken**|Otomatik biçimlendirme, panodaki XAML 'yi XAML görünümüne yapıştırdığınızda oluşur.|

## <a name="quotation-mark-style"></a>Tırnak Işareti stili
Bu ayar, öznitelik değerlerinin tek veya çift tırnak işareti içine alınmış olup olmadığını gösterir. Otomatik biçimlendirici ve IntelliSense otomatik tamamlama bu ayarı kullanır.

Bu seçeneği ayarladıktan sonra, yalnızca Tasarımcı kullanılarak veya XAML görünümünde el ile eklenen öznitelikler etkilenir.

|Name|Açıklama|
|-|-|
|**Çift tırnak işareti (")**|Öznitelik değerleri çift tırnak içine alınır.<br /><br /> `<Button Name="button1">Hello</Button>`|
|**Tek tırnak (')**|Öznitelik değerleri tek tırnak içine alınır.<br /><br /> `<Button Name='button1'>Hello</Button>`|

## <a name="tag-wrapping"></a>Etiket sarmalama
Etiket sarmalama için bir satır uzunluğu belirtebilirsiniz. Etiket kaydırma etkinleştirildiğinde, daha sonra tasarımcı kullanılarak eklenen XAML, uygun şekilde sarmalanır.

|Name|Açıklama|
|-|-|
|**Belirtilen uzunluğu aşan etiketleri sarın**|Çizgilerin, **uzunluğa**göre belirtilen satır uzunluğuna kaydırılıp kaydırılmayacağını belirtir.|
|**Uzunluk**|Bir çizginin içerebileceği karakter sayısı. Gerekirse, bazı XAML satırları belirtilen satır uzunluğunu aşabilir.|

## <a name="attribute-spacing"></a>Öznitelik aralığı
Özniteliklerin XAML belgenizde nasıl düzenlendiğini denetlemek için bu ayarı kullanın

|Name|Açıklama|
|-|-|
|**Öznitelikler arasındaki newlines ve boşlukları koru**|Öznitelikler arasındaki yeni satırlar ve boşluklar otomatik biçimlendirmeden etkilenmez.<br /><br /> `<Button Height="23" Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**Öznitelikler arasına tek boşluk Ekle**|Öznitelikler bir satır kaplar ve bitişik öznitelikleri ayıran bir alandır. Etiket kaydırma ayarları uygulanır.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|
|**Her özniteliği ayrı bir satıra yerleştir**|Her öznitelik kendi satırını kaplar. Bu, birçok öznitelik mevcut olduğunda faydalıdır.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|
|**İlk özniteliği başlangıç etiketiyle aynı satıra yerleştir**|İşaretlendiğinde, ilk öznitelik öğenin başlangıç etiketiyle aynı satırda görüntülenir.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|

## <a name="element-spacing"></a>Öğe aralığı
Öğelerin XAML belgenizde nasıl düzenlendiğini denetlemek için bu ayarı kullanın

|                                                               |                                                                                                                                                                                       |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **İçerikte yeni satırları koru**                             | Öğe içeriğindeki boş satırlar kaldırılmaz.<br /><br /> `<Grid>`<br /><br /><br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>\`   |
| **İçerikteki birden çok boş satırı tek bir satıra Daralt** | Öğe içeriğindeki boş satırlar tek bir satıra daraltılır.<br /><br /> `<Grid>`<br /><br /><br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /><br /><br /> `</Grid>` |
| **İçerikteki boş satırları kaldır**                             | Öğe içeriğindeki tüm boş satırlar kaldırılır.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`                                        |

## <a name="auto-insert"></a>Otomatik Ekle
Etiketlerin ve tekliflerin otomatik olarak ne zaman oluşturulduğunu denetlemek için bu ayarı kullanın.

|Name|Açıklama|
|-|-|
|**Kapatma etiketleri**|Açılış etiketini (>) karakterden daha uzun bir öğe kapatma etiketinin otomatik olarak oluşturulup oluşturulmayacağını belirtir.|
|**Öznitelik teklifleri**|Ekstre tamamlama açılan listesinden bir öznitelik değeri seçildiğinde kapsayan tekliflerin oluşturulup oluşturulmayacağını belirtir.|
|**MarkupExtensions için kapatma ayraçları**|Açma küme ayracı ({) yazdığınızda bir işaretleme uzantısının kapanış ayracı (}) otomatik olarak oluşturulup oluşturulmayacağını belirtir.|
|**MarkupExtension parametrelerini ayırmak için virgüller**|Bir biçimlendirme uzantısına birden fazla parametre yazdığınızda virgüllerin oluşturulup oluşturulmayacağını belirtir.|

## <a name="default-view"></a>Varsayılan Görünüm
XAML belgeleri yüklendiğinde Tasarım görünümü görünüp başlatılmayacağını denetlemek için bu ayarı kullanın.

|Name|Açıklama|
|-|-|
|**Belgeleri her zaman tam XAML görünümünde aç**|XAML belgelerinin Tasarım görünümü olmadan yalnızca XAML görünümünde görünüp görünmeyeceğini belirtir. Büyük belgeleri yüklemek için faydalıdır.|

## <a name="toolbox"></a>Araç Kutusu
Araç kutusunda Kullanıcı denetimleri ve özel denetimlerin gösterilip gösterilmeyeceğini belirtmek için bu ayarı kullanın.

|Name|Açıklama|
|-|-|
|**Araç kutusu öğelerini otomatik olarak doldur**|Geçerli çözümdeki Kullanıcı denetimlerinin ve özel denetimlerin araç kutusunda otomatik olarak gösterilip gösterilmeyeceğini belirtir.|

## <a name="see-also"></a>Ayrıca Bkz.
[WPF](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) 
 'de xaml [Nasıl yapılır: XAML görünüm ayarlarını değiştirme](https://msdn.microsoft.com/aee87c79-ca01-4f84-8fb7-a9e47048ee47) 
 [XAML ve kod talimatları](https://msdn.microsoft.com/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
