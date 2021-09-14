---
title: Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme
description: XAML'de programlama yapmak için kod düzenleyicisinde kod biçimlendirme seçeneklerini ayarlamak için Biçimlendirme seçenekleri sayfasını ve alt sayfasını kullanmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628641"
---
# <a name="options-text-editor-xaml-formatting"></a>Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme

Öğelerin ve **özniteliklerin** XAML belgelerinize nasıl biçimlendiril olduğunu belirtmek için Biçimlendirme özellik sayfasını kullanın. Seçenekler iletişim **kutusunu açmak** için Araçlar menüsüne ve **ardından** Seçenekler'e **tıklayın.** Biçimlendirme özellik sayfasına **erişmek** için Metin Düzenleyici  >  **XAML Biçimlendirme**  >  **düğümünü** genişletin.

## <a name="auto-formatting-events"></a>Olayları Otomatik Biçimlendirme

Aşağıdaki olaylardan herhangi biri algılandığında otomatik biçimlendirme oluşabilir.

- Bir bitiş etiketinin veya basit etiketin tamamlanması.

- Başlangıç etiketinin tamamlanması.

- Panodan yapıştırma.

- Klavye komutlarını biçimlendirme.

Hangi olayların otomatik biçimlendirmeye neden olduğunu belirterek.

**Bitiş etiketi veya basit etiket tamamlandığında**

Otomatik biçimlendirme, bir bitiş etiketi veya basit bir etiket yazmayı bitirladığınızda gerçekleşir. Basit bir etiketin özniteliği yoktur, örneğin `<Button />` .

**Başlangıç etiketi tamamlandığında**

Otomatik biçimlendirme, bir başlangıç etiketi yazmayı tamamladığınızda gerçekleşir.

**Panodan yapıştır**

Panodan XAML'i XAML görünümüne yapıştırırken otomatik biçimlendirme gerçekleşir.

## <a name="quotation-mark-style"></a>Tırnak İşareti Stili

Bu ayar, öznitelik değerlerinin tek veya çift tırnak içinde olup olmadığını gösterir. Hem otomatik biçimlendiren hem de IntelliSense otomatik tamamlama bu ayarı kullanır.

Bu seçeneği ayar verdiktan sonra yalnızca tasarımcı kullanılarak veya XAML görünümünde el ile eklenen öznitelikler etkilenir.

**Çift tırnak (")**

Öznitelik değerleri çift tırnak içine alınır.
`<Button Name="button1">Hello</Button>`

**Tek tırnak (')**

Öznitelik değerleri tek tırnak içine alınır.
`<Button Name='button1'>Hello</Button>`

## <a name="tag-wrapping"></a>Etiket Sarmalama

Etiket sarmalama için bir satır uzunluğu belirtebilirsiniz. Etiket sarmalama etkinleştirildiğinde, tasarımcı kullanılarak daha sonra eklenen tüm XAML'ler uygun şekilde sarmalar.

**Belirtilen uzunluğu aşan etiketleri sarmala**

Satırların Length tarafından belirtilen satır uzunluğuna sarmalanmış olup olmadığını **belirtir.**

**Uzunluk**

Bir satırda yer alan karakter sayısı. Gerekirse, bazı XAML satırları belirtilen satır uzunluğunu aş olabilir.

## <a name="attribute-spacing"></a>Öznitelik Aralığı

Özniteliklerin XAML belgesinde nasıl düzenlenmiş olduğunu kontrol etmek için bu ayarı kullanın

**Öznitelikler arasındaki yeni çizgileri ve boşlukları koruma**

Öznitelikler arasındaki yeni satırlar ve boşluklar otomatik biçimlendirmeden etkilenmez.

```xml
<Button Height="23"   Name="button1"
Width="75">Hello</Button>
```

**Öznitelikler arasında tek bir boşluk ekleme**

Öznitelikler bir satırı kaplar ve bitişik öznitelikleri ayıran bir boşluk içerir. Etiket sarmalama ayarları uygulanır.

```xml
<Button Height="23" Name="button1" Width="75">Hello</Button>
```

**Her özniteliği ayrı bir satıra konumlandırma**

Her öznitelik kendi çizgisini kaplar ve bu da birçok öznitelik mevcut olduğunda kullanışlıdır.

```xml
<Button
Height="23"
Name="button1"
Width="75">Hello</Button>
```

**İlk özniteliği başlangıç etiketiyle aynı satıra konumlandırma**

İşaretlendiğinde, ilk öznitelik öğenin başlangıç etiketiyle aynı satırda görünür.

```xml
<Button Height="23"
Name="button1"
Width="75">Hello</Button>
```

## <a name="element-spacing"></a>Öğe Aralığı

Öğelerin XAML belgeniz içinde nasıl düzenlenmiş olduğunu kontrol etmek için bu ayarı kullanın.

**İçerikte yeni satırları koruma**

Öğe içeriğinde boş satırlar kaldırılamaz.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikte birden çok boş satırı tek satıra daralt**

Öğe içeriğinde boş satırlar tek satıra daraltılmış.

```xml
<Grid>

<Button Name="button1">Hello</Button>

</Grid>
```

**İçerikte boş satırları kaldırma**

Öğe içeriğinde tüm boş satırlar kaldırılır.

```xml
<Grid>
<Button Name="button1">Hello</Button>
</Grid>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
