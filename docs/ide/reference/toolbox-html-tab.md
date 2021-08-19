---
title: Araç Kutusu, HTML Sekmesi
description: Araç kutusu penceresinin HTML sekmesinde bulacağınız HTML bileşenleri hakkında bilgi edinin.
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
ms.openlocfilehash: e650cc4d3bdcb9d7f0043c80e60620cdacae3e83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048771"
---
# <a name="toolbox-html-tab"></a>Araç kutusu, HTML sekmesi

Araç kutusunun **HTML** sekmesi, Web sayfaları ve Web formlarında yararlı olan bileşenleri sağlar. Bu sekmeyi görüntülemek için önce HTML tasarımcısında düzenlenecek bir belgeyi açın. **Görünüm** menüsünde, **araç kutusu**' na tıklayın ve ardından araç kutusunun **HTML** sekmesine tıklayın.

**HTML** sekmesinde bir aracın örneğini oluşturmak için araca çift tıklayarak geçerli ekleme noktasındaki belgenize ekleyin ya da aracı seçin ve düzen yüzeyi üzerinde istediğiniz konuma sürükleyin.

## <a name="ui-elements"></a>Kullanıcı arabirimi öğeleri

Aşağıdaki araçlar HTML sekmesinde varsayılan olarak kullanılabilir.

**Çağrısı**

![ASP.NET Mobile Designer HTMLpage Işaretçisi](../../ide/reference/media/vxpointer.gif)

Araç kutusu sekmesi açıldığında bu araç varsayılan olarak seçilidir. Silinemez. İşaretçi, nesneleri Tasarım görünümü yüzeyi üzerine sürüklemenize, yeniden boyutlandırmanıza ve sayfa ya da form üzerinde yeniden konumlandırmanıza olanak sağlar. Daha fazla bilgi için bkz. [araç kutusu](../../ide/reference/toolbox.md).

**Giriş (düğme)**

![HTML Web sayfası düğmesi](../../ide/reference/media/vxbutton.gif)

Öğesi ekler `input` `type="button"` . Görüntülenen metni değiştirmek için, `name` özelliğini düzenleyin. Varsayılan olarak, `id="Button1"` ilk düğme için, `id="Button2"` İkincisi, vb. için eklenmiştir.

**Giriş (düğme)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Giriş (sıfırlama)**

![HTMLpageResetButton ekran görüntüsü](../../ide/reference/media/vxreset.gif)

Öğesi ekler `input` `type="reset"` . Görüntülenen metni değiştirmek için, `name` özelliğini düzenleyin. Varsayılan olarak, `id="Reset1"` ilk sıfırlama düğmesine, `id="Reset2"` ikincisi için eklenir ve bu şekilde devam eder.

**Girişi (sıfırlama)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Giriş (Gönder)**

![HTMLpageToolbarSubmitButton ekran görüntüsü](../../ide/reference/media/vxsubmit.gif)

Öğesi ekler `input` `type="submit"` . Görüntülenen metni değiştirmek için, `name` özelliğini düzenleyin. Varsayılan olarak, `id="Submit1"` ilk Gönder düğmesine, `id="Submit2"` ikincisi için eklenir ve bu şekilde devam eder.

**Girişi (Gönder)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Giriş (metin)**

![HTMLpageToolbarTextField ekran görüntüsü](../../ide/reference/media/vxtextfield.gif)

Belgenize bir `input` öğesi ekler `type="text"` . Görüntülenen varsayılan metni değiştirmek için `value` özniteliği düzenleyin. Varsayılan olarak, `id="Text1"` ikinci için ilk metin alanı için eklenir `id="Text2"` ve bu şekilde devam eder.

**Girişi (metin)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Tüm Kullanıcı girişlerini doğrulamanız önerilir. daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (dosya)**

![HTML sayfa dosyası alanı](../../ide/reference/media/vxfilefield.gif)

Belgenize bir `input` öğesi ekler `type="file"` . Varsayılan olarak, `id="File1"` ikinci için ilk dosya alanı için eklenir `id="File2"` ve bu şekilde devam eder.

**Giriş (dosya)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (parola)**

![Visual Studio Parola alanı](../../ide/reference/media/vxpassword.gif)

Öğesi ekler `input` `type="password"` . Varsayılan olarak, `id="Password1"` ilk parola alanı için, `id="Password2"` ikincisi için eklenir ve bu şekilde devam eder.

**Giriş (parola)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Uygulamanız kullanıcı adlarını ve parolaları iletitirse, Web sitenizi, iletimi şifrelemek için Güvenli Yuva Katmanı (SSL) kullanacak şekilde yapılandırmanız gerekir. Daha fazla bilgi için bkz. [bağlantıları güvenli hale getirme](/previous-versions/tn-archive/bb418917(v=technet.10)). Ayrıca, tüm kullanıcı girişlerini doğrulamanız önerilir. daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (onay kutusu)**

![HTML Web sayfası araç kutusu seçeneği](../../ide/reference/media/vxcheckbox.gif)

Öğesi ekler `input` `type="checkbox"` . Görüntülenen metni değiştirmek için, `name` özelliğini düzenleyin. Varsayılan olarak, `id="Checkbox1"` ilk onay kutusu için, `id="Checkbox2"` ikincisi için eklenmiştir ve bu şekilde devam eder.

**Girişi (onay kutusu)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Giriş (radyo)**

![VisualStudioHTMLpageRadioButton ekran görüntüsü](../../ide/reference/media/vxradio.gif)

Öğesi ekler `input` `type="radio"` . Görüntülenen metni değiştirmek için, `name` özelliğini düzenleyin. Varsayılan olarak, `id="Radio1"` ilk radyo düğmesine, `id="Radio2"` ikincisi için eklenir ve bu şekilde devam eder.

**Girişi (radyo)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Giriş (gizli)**

![HTML sayfası gizli öğesi](../../ide/reference/media/vxhidden.gif)

Öğesi ekler `input` `type="hidden"` . Varsayılan olarak, `id="Hidden1"` ilk gizli alan için, `id="Hidden2"` ikincisi için eklenir ve bu şekilde devam eder.

**Girişi (gizli)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Metin Alanı**

![HTMLpage araç çubuğu metin alanı](../../ide/reference/media/vxtextarea.gif)

Bir `textarea` öğesi ekler. Metin alanını yeniden boyutlandırabilir veya görüntüleme alanının ötesinde genişleyen metni görüntülemek için kaydırma çubuklarını kullanabilirsiniz. Görüntülenen varsayılan metni değiştirmek için `value` özniteliği düzenleyin. Varsayılan olarak, `id="textarea1"` ikinci için ilk metin alanı eklenir `id=" textarea 2"` ve bu şekilde devam eder.

**Textarea** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tablo**

![HTMLpageToolbarTable ekran görüntüsü](../../ide/reference/media/vxtable.gif)

Bir `table` öğesi ekler.

**Tabloyu** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Görüntü**

![HTML sayfası resim öğesi](../../ide/reference/media/vximage.gif)

Bir `img` öğesi ekler. Kendi metnini belirtmek için bu öğeyi düzenleyin `src` `alt` .

**Görüntüyü** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<img alt="" src="">
```

**Seç**

![HTML sayfası araç kutusu açılan kutusu](../../ide/reference/media/vxdropdown.gif)

Bir açılan `select` öğe ekler (özniteliği olmadan `size` ). Varsayılan olarak, `id="select1"` ilk liste kutusu için, `id="select2"` ikinci için eklenmiştir ve bu şekilde devam eder.

**Seçimi** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKILER gibi HTML biçimlendirmesi eklenir:

```html
<select id="select1" name="select1"><option selected></option></select>
```

`select`Boyut özelliğinin değerini artırarak çok satırlı bir öğe oluşturabilirsiniz.

**Yatay kural**

![HTML sayfası yatay kural öğesi](../../ide/reference/media/vxhorizontal.gif)

Bir öğe `hr` ekler. Çizginin kalınlığını artırmak için özniteliğini `size` düzenleyin.

Yatay **Kural'ı Tasarım görünümü,** belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<hr width="100%" size=1>
```

**Div**

![HTML sayfası Etiketi](../../ide/reference/media/vxlabel.gif)

Özniteliği içeren `div` bir öğe `ms_positioning="FlowLayout"` ekler. Genişlik ve yükseklik dışında, bu öğe Flow Düzeni Paneli ile aynıdır. öğesinin içinde yer alan metni biçimlendirmek `div` için açılış `class="stylename"` etiketine bir özniteliği ekleyin.

**Div'i** Tasarım görünümü sürükleyerek belgenize aşağıdaki gibi HTML işaretlemesi eklenir:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
