---
title: Araç Kutusu, HTML Sekmesi
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0489f534466149a437384d4f21e34f1fa9e98c5b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596443"
---
# <a name="toolbox-html-tab"></a>Araç kutusu, HTML sekmesi

Araç kutusunun **HTML** sekmesi, Web sayfaları ve Web formlarında yararlı olan bileşenleri sağlar. Bu sekmeyi görüntülemek için önce HTML tasarımcısında düzenlenecek bir belgeyi açın. **Görünüm** menüsünde, **araç kutusu**' na tıklayın ve ardından araç kutusunun **HTML** sekmesine tıklayın.

**HTML** sekmesinde bir aracın örneğini oluşturmak için araca çift tıklayarak geçerli ekleme noktasındaki belgenize ekleyin ya da aracı seçin ve düzen yüzeyi üzerinde istediğiniz konuma sürükleyin.

## <a name="ui-elements"></a>UI öğeleri

Aşağıdaki araçlar HTML sekmesinde varsayılan olarak kullanılabilir.

**Çağrısı**

![ASP.NET Mobile Designer HTMLpage Işaretçisi](../../ide/reference/media/vxpointer.gif)

Araç kutusu sekmesi açıldığında bu araç varsayılan olarak seçilidir. Silinemez. İşaretçi, nesneleri Tasarım görünümü yüzeyi üzerine sürüklemenize, yeniden boyutlandırmanıza ve sayfa ya da form üzerinde yeniden konumlandırmanıza olanak sağlar. Daha fazla bilgi için [araç kutusu](../../ide/reference/toolbox.md).

**Giriş (düğme)**

![HTML Web sayfası düğmesi](../../ide/reference/media/vxbutton.gif)

`type="button"`bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Button1"` ilk düğme için eklenir, ikincisi için `id="Button2"` ve bu şekilde devam eder.

**Giriş (düğme)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Giriş (sıfırlama)**

![HTMLpageResetButton ekran görüntüsü](../../ide/reference/media/vxreset.gif)

`type="reset"`bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Reset1"` ilk sıfırlama düğmesine eklenir, ikincisi için `id="Reset2"` ve bu şekilde devam eder.

**Girişi (sıfırlama)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Giriş (Gönder)**

![HTMLpageToolbarSubmitButton ekran görüntüsü](../../ide/reference/media/vxsubmit.gif)

`type="submit"`bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Submit1"` ilk Gönder düğmesine eklenir, ikincisi için `id="Submit2"` ve bu şekilde devam eder.

**Girişi (Gönder)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Giriş (metin)**

![HTMLpageToolbarTextField ekran görüntüsü](../../ide/reference/media/vxtextfield.gif)

Belgenize `type="text"` `input` öğesi ekler. Görüntülenen varsayılan metni değiştirmek için `value` özniteliğini düzenleyin. Varsayılan olarak, `id="Text1"` ilk metin alanı için eklenir, ikincisi için `id="Text2"` ve bu şekilde devam eder.

**Girişi (metin)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Tüm Kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (dosya)**

![HTML sayfa dosyası alanı](../../ide/reference/media/vxfilefield.gif)

Belgenize `type="file"` `input` öğesi ekler. Varsayılan olarak, `id="File1"` ilk dosya alanı için eklenir, ikincisi için `id="File2"` ve bu şekilde devam eder.

**Giriş (dosya)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (parola)**

![Visual Studio parolası alanı](../../ide/reference/media/vxpassword.gif)

`type="password"`bir `input` öğesi ekler. Varsayılan olarak, `id="Password1"` ilk parola alanı için eklenir, ikincisi için `id="Password2"` ve bu şekilde devam eder.

**Giriş (parola)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Uygulamanız kullanıcı adlarını ve parolaları iletitirse, Web sitenizi, iletimi şifrelemek için Güvenli Yuva Katmanı (SSL) kullanacak şekilde yapılandırmanız gerekir. Daha fazla bilgi için bkz. [bağlantıları güvenli hale getirme](/previous-versions/tn-archive/bb418917(v=technet.10)). Ayrıca, tüm kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Giriş (onay kutusu)**

![HTML Web sayfası araç kutusu seçeneği](../../ide/reference/media/vxcheckbox.gif)

`type="checkbox"`bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Checkbox1"` ilk onay kutusu için eklenir, ikincisi için `id="Checkbox2"` ve bu şekilde devam eder.

**Girişi (onay kutusu)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Giriş (radyo)**

![VisualStudioHTMLpageRadioButton ekran görüntüsü](../../ide/reference/media/vxradio.gif)

`type="radio"`bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Radio1"` ilk radyo düğmesi için eklenir, ikincisi için `id="Radio2"` ve bu şekilde devam eder.

**Girişi (radyo)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Giriş (gizli)**

![HTML sayfası gizli öğesi](../../ide/reference/media/vxhidden.gif)

`type="hidden"`bir `input` öğesi ekler. Varsayılan olarak, `id="Hidden1"` ilk gizli alan için eklenir, ikincisi için `id="Hidden2"` ve bu şekilde devam eder.

**Girişi (gizli)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Metin Alanı**

![HTMLpage araç çubuğu metin alanı](../../ide/reference/media/vxtextarea.gif)

Bir `textarea` öğesi ekler. Metin alanını yeniden boyutlandırabilir veya görüntüleme alanının ötesinde genişleyen metni görüntülemek için kaydırma çubuklarını kullanabilirsiniz. Görüntülenen varsayılan metni değiştirmek için `value` özniteliğini düzenleyin. Varsayılan olarak, `id="textarea1"` ilk metin alanının eklendiği, ikincisi için `id=" textarea 2"` ve bu şekilde devam eder.

**Textarea** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web Pages (Razor) sitelerindeki kullanıcı girişini doğrulama](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tablo**

![HTMLpageToolbarTable ekran görüntüsü](../../ide/reference/media/vxtable.gif)

Bir `table` öğesi ekler.

**Tabloyu** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Görüntü**

![HTML sayfası resim öğesi](../../ide/reference/media/vximage.gif)

Bir `img` öğesi ekler. `src` ve `alt` metnini belirtmek için bu öğeyi düzenleyin.

**Görüntüyü** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<img alt="" src="">
```

**Seçin**

![HTML sayfası araç kutusu açılan kutusu](../../ide/reference/media/vxdropdown.gif)

Bir açılan `select` öğesi ekler (`size` özniteliği olmadan). Varsayılan olarak, `id="select1"` ilk liste kutusu için eklenir, ikincisi için `id="select2"` ve bu şekilde devam eder.

**Seçimi** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKILER gibi HTML biçimlendirmesi eklenir:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Boyut özelliğinin değerini artırarak çok satırlı `select` öğesi oluşturabilirsiniz.

**Yatay kural**

![HTML sayfası yatay kural öğesi](../../ide/reference/media/vxhorizontal.gif)

Bir `hr` öğesi ekler. Çizginin kalınlığını artırmak için `size` özniteliğini düzenleyin.

**Yatay kuralı** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```html
<hr width="100%" size=1>
```

**DIV**

![HTML sayfa etiketi](../../ide/reference/media/vxlabel.gif)

Bir `ms_positioning="FlowLayout"` özniteliği içeren bir `div` öğesi ekler. Genişlik ve Yükseklik dışında, bu öğe bir akış düzeni paneliyle aynıdır. `div` öğesi içinde bulunan metni biçimlendirmek için, açma etiketine bir `class="stylename"` özniteliği ekleyin.

**Div** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
