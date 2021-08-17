---
title: Araç Kutusu, HTML Sekmesi
description: Araç Kutusu penceresinin HTML sekmesinde öğreneceğiz HTML bileşenleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 672bf1c73aa132cd07f6851256038c56a053359b2131ec224c5387c2289179bc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121232412"
---
# <a name="toolbox-html-tab"></a>Araç kutusu, HTML sekmesi

Araç **Kutusunun HTML** sekmesi, web sayfalarında ve web formlarında yararlı bileşenler sağlar. Bu sekmeyi görüntülemek için önce HTML tasarımcısında düzenlemek için bir belge açın. Görünüm **menüsünde** Araç **Kutusu'na ve** ardından Araç Kutusunun **HTML** sekmesine tıklayın.

**HTML** sekmesinde bir araç örneği oluşturmak için, aracı geçerli ekleme noktasında belgenize eklemek için çift tıklayın veya aracı seçin ve düzenleme yüzeyinde istenen konuma sürükleyin.

## <a name="ui-elements"></a>Kullanıcı arabirimi öğeleri

Aşağıdaki araçlar HTML sekmesinde varsayılan olarak kullanılabilir.

**Işaretçi**

![ASP.NET Mobil Tasarımcı HTML Sayfası İşaretçisi](../../ide/reference/media/vxpointer.gif)

Herhangi bir Araç Kutusu sekmesi açıldığında bu araç varsayılan olarak seçilir. Silinemez. İşaretçi nesneleri sayfa veya forma sürükleyerek Tasarım görünümü, yeniden boyutlandırmanıza ve yeniden konumlandırmanıza olanak sağlar. Daha fazla bilgi için [bkz. Araç Kutusu.](../../ide/reference/toolbox.md)

**Giriş (Düğme)**

![HTML web sayfası düğmesi](../../ide/reference/media/vxbutton.gif)

öğesinin `input` bir öğesini `type="button"` ekler. Görüntülenen metni değiştirmek için özelliğini `name` düzenleyin. Varsayılan `id="Button1"` olarak, ilk düğme için, `id="Button2"` ikinci düğme için eklenir ve bu şekilde devam edin.

Giriş **(Düğme) girişini Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Giriş (Sıfırlama)**

![HTMLpageResetButton ekran görüntüsü](../../ide/reference/media/vxreset.gif)

öğesinin `input` bir öğesini `type="reset"` ekler. Görüntülenen metni değiştirmek için özelliğini `name` düzenleyin. Varsayılan `id="Reset1"` olarak, ilk sıfırlama düğmesi için `id="Reset2"` ikinciye eklenir ve bu şekilde devam edin.

Giriş **(Sıfırla) girişini Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Giriş (Gönder)**

![HTMLpageToolbarSubmitButton ekran görüntüsü](../../ide/reference/media/vxsubmit.gif)

öğesinin `input` bir öğesini `type="submit"` ekler. Görüntülenen metni değiştirmek için özelliğini `name` düzenleyin. Varsayılan `id="Submit1"` olarak, ilk gönder düğmesi için, `id="Submit2"` ikinci düğme için eklenir ve bu şekilde devam edin.

Giriş **(Gönder) girişini Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Giriş (Metin)**

![HTMLLpageToolbarTextField ekran görüntüsü](../../ide/reference/media/vxtextfield.gif)

öğesini `input` `type="text"` belgenize ekler. Görüntülenen varsayılan metni değiştirmek için özniteliğini `value` düzenleyin. Varsayılan olarak, ilk metin alanı için, ikinci metin alanı için eklenir ve `id="Text1"` `id="Text2"` bu şekilde devam ediyor.

Giriş **(Metin) girişini Tasarım görünümü** yüzeyine sürüklerken, belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Tüm kullanıcı girişini doğrulamanızı öneririz. Daha fazla bilgi için [bkz. Web Sayfaları (Razor) ASP.NET Kullanıcı Girişini Doğrulama.](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Giriş (Dosya)**

![HTML sayfası Dosya Alanı](../../ide/reference/media/vxfilefield.gif)

öğesini `input` `type="file"` belgenize ekler. Varsayılan `id="File1"` olarak, ilk dosya alanı için, `id="File2"` ikinci alan için eklenir ve bu şekilde devam ediyor.

Giriş **(Dosya) girişini Tasarım görünümü** yüzeyine sürüklerken, belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Tüm kullanıcı girişini doğrulamanızı öneririz. Daha fazla bilgi için [bkz. Web Sayfaları (Razor) ASP.NET Kullanıcı Girişini Doğrulama.](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Giriş (Parola)**

![Visual Studio Parola Alanı](../../ide/reference/media/vxpassword.gif)

öğesinin `input` bir öğesini `type="password"` ekler. Varsayılan `id="Password1"` olarak, ilk parola alanı için, `id="Password2"` ikinci için eklenir ve bu şekilde devam ediyor.

Giriş **(Parola) girişini Tasarım görünümü** yüzeyine sürüklerseniz, belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Uygulamanız kullanıcı adları ve parolalar iletirse, web sitenizi aktarımı şifrelemek için Güvenli Yuva Katmanı (SSL) kullanmak üzere yapılandırmanız gerekir. Daha fazla bilgi için bkz. [Bağlantıların Güvenliğini Sağlama.](/previous-versions/tn-archive/bb418917(v=technet.10)) Ayrıca, tüm kullanıcı girişini doğrulamanızı öneririz. Daha fazla bilgi için [bkz. Web Sayfaları (Razor) ASP.NET Kullanıcı Girişini Doğrulama.](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Giriş (Onay kutusu)**

![HTML web sayfası Araç Kutusu Onay Kutusu Seçeneği](../../ide/reference/media/vxcheckbox.gif)

öğesinin `input` bir öğesini `type="checkbox"` ekler. Görüntülenen metni değiştirmek için özelliğini `name` düzenleyin. Varsayılan `id="Checkbox1"` olarak, ilk onay kutusu için, ikinci onay kutusu için eklenir `id="Checkbox2"` ve bu şekilde devam etmek için kullanılır.

Giriş **(Onay kutusu) girişini Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Giriş (Radyo)**

![VisualStudioHTMLpageRadioButton ekran görüntüsü](../../ide/reference/media/vxradio.gif)

öğesinin `input` bir öğesini `type="radio"` ekler. Görüntülenen metni değiştirmek için özelliğini `name` düzenleyin. Varsayılan `id="Radio1"` olarak, ilk radyo düğmesi için, ikinci radyo düğmesi için eklenir `id="Radio2"` ve bu şekilde devam edin.

Giriş **(Radyo) girişini Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Giriş (Gizli)**

![HTML sayfası Gizli Öğe](../../ide/reference/media/vxhidden.gif)

öğesinin `input` bir öğesini `type="hidden"` ekler. Varsayılan `id="Hidden1"` olarak, ilk gizli alan için, `id="Hidden2"` ikinci için eklenir ve bu şekilde devam ediyor.

Giriş **(Gizli) girişini Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Metin Alanı**

![HTMLpage Araç Çubuğu Metin Alanı](../../ide/reference/media/vxtextarea.gif)

Bir öğe `textarea` ekler. Metin alanını yeniden boyutlandırabilir veya kaydırma çubuklarını kullanarak görüntüleme alanını aşan metinleri görüntüebilirsiniz. Görüntülenen varsayılan metni değiştirmek için özniteliğini `value` düzenleyin. Varsayılan `id="textarea1"` olarak, ikinci için ilk metin `id=" textarea 2"` alanı eklenir ve bu şekilde devam ediyor.

**Textarea'yı Tasarım görünümü** yüzeyine sürüklerken, aşağıdaki gibi HTML işaretlemesi belgenize eklenir:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Tüm kullanıcı girişini doğrulamanızı öneririz. Daha fazla bilgi için [bkz. Web Sayfaları (Razor) ASP.NET Kullanıcı Girişini Doğrulama.](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Tablo**

![HTMLpageToolbarTable ekran görüntüsü](../../ide/reference/media/vxtable.gif)

Bir öğe `table` ekler.

**Tablo'Tasarım görünümü** sürükleyerek belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Görüntü**

![HTML sayfası Görüntü Öğesi](../../ide/reference/media/vximage.gif)

Bir öğe `img` ekler. Öğesini ve metnini belirtmek için `src` bu öğeyi `alt` düzenleyin.

**Görüntü'leri** Tasarım görünümü sürüklerken, belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<img alt="" src="">
```

**Seç**

![HTML sayfası Araç Kutusu Açılan Kutusu](../../ide/reference/media/vxdropdown.gif)

Bir açılan öğe ekler `select` (öznitelik `size` olmadan). Varsayılan `id="select1"` olarak, ilk liste kutusu için, `id="select2"` ikinci için eklenir ve bu şekilde devam edin.

**Seç'i** Tasarım görünümü sürükleyerek belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Size özelliğinin değerini `select` artırarak çok satırlı bir öğe oluşturabilirsiniz.

**Yatay Kural**

![HTML sayfası Yatay Kural Öğesi](../../ide/reference/media/vxhorizontal.gif)

Bir `hr` öğesi ekler. Çizginin kalınlığını artırmak için `size` özniteliği düzenleyin.

**Yatay kuralı** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<hr width="100%" size=1>
```

**DIV**

![HTML sayfa etiketi](../../ide/reference/media/vxlabel.gif)

`div`Özniteliği içeren bir öğesi ekler `ms_positioning="FlowLayout"` . genişlik ve yükseklik dışında, bu öğe Flow düzen paneliyle aynıdır. Öğe içinde bulunan metni biçimlendirmek için `div` , `class="stylename"` açma etiketine bir öznitelik ekleyin.

**Div** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
