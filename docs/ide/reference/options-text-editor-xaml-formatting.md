---
title: Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d340a3b9468ea23c4cab23aabe19a7c1390955a3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568249"
---
# <a name="options-text-editor-xaml-formatting"></a>Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme

XAML belgelerinizde öğelerin ve özniteliklerin nasıl biçimlendiğini belirtmek için **Biçimlendirme** özelliği sayfasını kullanın. **Seçenekler** iletişim kutusunu açmak için **Araçlar** menüsünü tıklatın ve ardından **Seçenekler'i**tıklatın. **Biçimlendirme** özelliği sayfasına erişmek için **Metin Düzenleyicisi** > **XAML** > Biçimlendirme düğümlerini**genişletin.**

## <a name="auto-formatting-events"></a>Olayları Otomatik Biçimlendirme

Aşağıdaki olaylardan herhangi biri algılandığında otomatik biçimlendirme oluşabilir.

- Bir bitiş etiketinin veya basit etiketin tamamlanması.

- Başlangıç etiketinin tamamlanması.

- Panodan yapıştırma.

- Klavye komutlarını biçimlendirme.

Hangi olayların otomatik biçimlendirmeye neden olduğunu belirtebilirsiniz.

**Bitiş etiketi veya basit etiket tamamlandığında**

Otomatik biçimlendirme, bir son etiketi veya basit bir etiket yazmayı bitirdiğinizde gerçekleşir. Basit bir etiket, örneğin `<Button />`hiçbir öznitelikleri vardır.

**Başlangıç etiketinin tamamlanmasıüzerine**

Bir başlangıç etiketi yazmayı bitirdiğinizde otomatik biçimlendirme gerçekleşir.

**Panodan yapıştır'da**

Otomatik biçimlendirme, panodan XAML'yi XAML görünümüne yapıştırdığınızda gerçekleşir.

## <a name="quotation-mark-style"></a>Tırnak Stili

Bu ayar, öznitelik değerlerinin tek veya çift tırnak işaretleriyle mi ekte olduğunu gösterir. Autoformatter ve IntelliSense otomatik tamamlama hem bu ayarı kullanın.

Bu seçeneği ayarladıktan sonra, yalnızca tasarımcıyı kullanarak veya XAML görünümünde el ile eklenen öznitelikler etkilenir.

**Çift tırnak (")**

Öznitelik değerleri çift tırnak içinde eklenir.
`<Button Name="button1">Hello</Button>`

**Tek tırnak (')**

Öznitelik değerleri tek tırnak içinde eklenir.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Etiket Sarma

Etiket kaydırma için bir satır uzunluğu belirtebilirsiniz. Etiket kaydırma etkinleştirildiğinde, tasarımcı kullanılarak eklenen herhangi bir XAML uygun şekilde sarılır.

**Belirtilen uzunluğu aşan etiketleri kaydırma**

Çizgilerin **Uzunluk**tarafından belirtilen satır uzunluğuna sarıp sarılmadığını belirtir.

**Uzunluk**

Bir satırın içerebileceği karakter sayısı. Gerekirse, bazı XAML satırları belirtilen satır uzunluğunu aşabilir.

## <a name="attribute-spacing"></a>Öznitelik Aralığı

XAML belgenizde özniteliklerin nasıl düzenlenebildiğini denetlemek için bu ayarı kullanın

**Öznitelikler arasındaki yeni çizgileri ve boşlukları koruma**

Öznitelikler arasındaki yeni satırlar ve boşluklar otomatik biçimlendirmeden etkilenmez.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Öznitelikler arasında tek bir boşluk ekleme**

Öznitelikler, bitişik öznitelikleri ayıran bir boşlukla bir satırı kaplar. Etiket kaydırma ayarları uygulanır.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Her özniteliği ayrı bir satıra konumlandırma**

Her öznitelik, birçok öznitelik mevcut olduğunda yararlı olan kendi satır, kaplar.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**İlk özniteliği başlangıç etiketiyle aynı satıra yerleştirin**

İşaretlendiğinde, ilk öznitelik öğenin başlangıç etiketiyle aynı satırda görünür.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Eleman Aralığı

XAML belgenizde öğelerin nasıl düzenlenerek düzenlenebildiğini denetlemek için bu ayarı kullanın.

**İçerikteki yeni satırları koruma**

Öğe içeriğindeki boş satırlar kaldırılmaz.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikteki birden çok boş satırı tek bir satıra daraltma**

Öğe içeriğindeki boş satırlar tek bir satıra daraltılır.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikteki boş satırları kaldırma**

Öğe içeriğindeki tüm boş satırlar kaldırılır.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
