---
title: Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme
description: XAML 'de programlarken kod düzenleyicisinde biçimlendirme kodu seçeneklerini ayarlamak için biçimlendirme seçenekleri sayfasını ve alt sayfalarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- uwp
ms.openlocfilehash: 47311af7eee476ac4beea2c73bfa5ab00ed19ea6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069395"
---
# <a name="options-text-editor-xaml-formatting"></a>Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme

Öğelerin ve özniteliklerin XAML belgelerinizde nasıl biçimlendirileceğini belirtmek için **biçimlendirme** özelliği sayfasını kullanın. **Seçenekler** iletişim kutusunu açmak için **Araçlar** menüsüne ve ardından **Seçenekler**' e tıklayın. **Biçimlendirme** özelliği sayfasına erişmek için, **metin düzenleyici**  >  **xaml**  >  **biçimlendirme** düğümünü genişletin.

## <a name="auto-formatting-events"></a>Otomatik biçimlendirme olayları

Aşağıdaki olaylardan herhangi biri algılandığında, oto biçimlendirme gerçekleşebilir.

- Bitiş etiketi veya basit etiket tamamlama.

- Başlangıç etiketinin tamamlanması.

- Panodan yapıştırılıyor.

- Klavye komutları biçimlendiriliyor.

Hangi olayların, hangi olayların bu şekilde olduğunu belirtebilirsiniz.

**Bitiş etiketi veya basit etiket tamamlandığında**

Bir bitiş etiketi veya basit bir etiket yazmayı bitirdiğinizde otomatik biçimlendirme oluşur. Basit bir etiketin öznitelikleri yoktur, örneğin `<Button />` .

**Başlangıç etiketi tamamlandığında**

Başlangıç etiketi yazmayı bitirdiğinizde otomatik biçimlendirme oluşur.

**Panodan yapıştırılırken**

Panodaki XAML 'yi XAML görünümüne yapıştırdığınızda, oto biçimlendirme gerçekleşir.

## <a name="quotation-mark-style"></a>Tırnak Işareti stili

Bu ayar, öznitelik değerlerinin tek veya çift tırnak işareti içine alınmış olup olmadığını gösterir. Otomatik biçimlendirici ve IntelliSense otomatik tamamlama bu ayarı kullanır.

Bu seçeneği ayarladıktan sonra, yalnızca Tasarımcı kullanılarak veya XAML görünümünde el ile eklenen öznitelikler etkilenir.

**Çift tırnak işareti (")**

Öznitelik değerleri çift tırnak içine alınır.
`<Button Name="button1">Hello</Button>`

**Tek tırnak (')**

Öznitelik değerleri tek tırnak içine alınır.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Etiket sarmalama

Etiket sarmalama için bir satır uzunluğu belirtebilirsiniz. Etiket kaydırma etkinleştirildiğinde, daha sonra tasarımcı kullanılarak eklenen XAML, uygun şekilde sarmalanır.

**Belirtilen uzunluğu aşan etiketleri sarın**

Çizgilerin, **uzunluğa** göre belirtilen satır uzunluğuna kaydırılıp kaydırılmayacağını belirtir.

**Uzunluk**

Bir çizginin içerebileceği karakter sayısı. Gerekirse, bazı XAML satırları belirtilen satır uzunluğunu aşabilir.

## <a name="attribute-spacing"></a>Öznitelik aralığı

Özniteliklerin XAML belgenizde nasıl düzenlendiğini denetlemek için bu ayarı kullanın

**Öznitelikler arasındaki newlines ve boşlukları koru**

Öznitelikler arasındaki yeni satırlar ve boşluklar, oto biçimlendirmeden etkilenmez.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Öznitelikler arasına tek boşluk Ekle**

Öznitelikler bir satır kaplar ve bitişik öznitelikleri ayıran bir alandır. Etiket kaydırma ayarları uygulanır.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Her özniteliği ayrı bir satıra yerleştir**

Her öznitelik kendi satırını kaplar, bu da birçok öznitelik mevcut olduğunda yararlı olur.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**İlk özniteliği başlangıç etiketiyle aynı satıra yerleştir**

İşaretlendiğinde, ilk öznitelik öğenin başlangıç etiketiyle aynı satırda görüntülenir.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Öğe aralığı

Öğelerin XAML belgenizde nasıl düzenlendiğini denetlemek için bu ayarı kullanın.

**İçerikte yeni satırları koru**

Öğe içeriğindeki boş satırlar kaldırılmaz.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikteki birden çok boş satırı tek bir satıra Daralt**

Öğe içeriğindeki boş satırlar tek bir satıra daraltılır.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikteki boş satırları kaldır**

Öğe içeriğindeki tüm boş satırlar kaldırılır.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
