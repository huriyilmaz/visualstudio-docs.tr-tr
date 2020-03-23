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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596443"
---
# <a name="toolbox-html-tab"></a>Araç Kutusu, HTML sekmesi

Araç Kutusunun **HTML** sekmesi, web sayfalarında ve web formlarında yararlı bileşenler sağlar. Bu sekmeyi görüntülemek için önce HTML tasarımcısında düzenlemek üzere bir belge açın. **Görünüm** menüsünde **Araç Kutusu'nu**tıklatın ve ardından Araç Kutusu'nun **HTML** sekmesini tıklatın.

**HTML** sekmesinde bir araç örneği oluşturmak için, geçerli ekleme noktasında belgenize eklemek için aracı çift tıklatın veya aracı seçin ve düzenleme yüzeyinde istenen konuma sürükleyin.

## <a name="ui-elements"></a>Kullanıcı arabirimi öğeleri

Aşağıdaki araçlar varsayılan olarak HTML sekmesinde kullanılabilir.

**Işaretçi**

![ASP.NET Mobil Tasarımcı HTMLpage Pointer](../../ide/reference/media/vxpointer.gif)

Bu araç, herhangi bir Araç Kutusu sekmesi açıldığında varsayılan olarak seçilir. Silinemez. İşaretçi, nesneleri Tasarım görünüm yüzeyine sürüklemenizi, yeniden boyutlandırmanızı ve sayfa veya formda yeniden konumlandırmanızı sağlar. Daha fazla bilgi için [Toolbox'a](../../ide/reference/toolbox.md)bakın.

**Giriş (Düğme)**

![HTML web sayfası düğmesi](../../ide/reference/media/vxbutton.gif)

`type="button"`Bir `input` öğe ekler. Görüntülenen metni değiştirmek için özelliği edin. `name` Varsayılan olarak, `id="Button1"` ilk düğme `id="Button2"` için, ikinci ve benzeri eklenir.

**Giriş (Düğme)** Giriş'i Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Giriş (Sıfırlama)**

![HTMLpageResetButton ekran görüntüsü](../../ide/reference/media/vxreset.gif)

`type="reset"`Bir `input` öğe ekler. Görüntülenen metni değiştirmek için özelliği edin. `name` Varsayılan olarak, `id="Reset1"` ilk sıfırlama düğmesi `id="Reset2"` için, ikinci ve benzeri eklenir.

**Giriş 'i (Sıfırlama)** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Giriş (Gönder)**

![HTMLpageToolbarSubmitButton ekran görüntüsü](../../ide/reference/media/vxsubmit.gif)

`type="submit"`Bir `input` öğe ekler. Görüntülenen metni değiştirmek için özelliği edin. `name` Varsayılan olarak, `id="Submit1"` ilk gönderme düğmesi için, `id="Submit2"` ikinci ve benzeri eklenir.

**Giriş (Gönder) Giriş'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Giriş (Metin)**

![HTMLpageToolbarTextField ekran görüntüsü](../../ide/reference/media/vxtextfield.gif)

Belgenize bir `input` öğe `type="text"` ekler. Görüntülenen varsayılan metni değiştirmek için özniteliği `value` değiştirin. Varsayılan olarak, `id="Text1"` ilk metin alanı için, `id="Text2"` ikinci ve benzeri eklenir.

**Giriş (Metin) Giriş'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Tüm kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için, [web sayfaları (Jilet) Sitelerine ASP.NET Kullanıcı Girişinin Doğrulanması'na](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)bakın.

**Giriş (Dosya)**

![HTML sayfası Dosya Alanı](../../ide/reference/media/vxfilefield.gif)

Belgenize bir `input` öğe `type="file"` ekler. Varsayılan olarak, `id="File1"` ilk dosya alanı için, `id="File2"` ikinci ve benzeri eklenir.

**Giriş (Dosya) Giriş'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Tüm kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için, [web sayfaları (Jilet) Sitelerine ASP.NET Kullanıcı Girişinin Doğrulanması'na](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)bakın.

**Giriş (Şifre)**

![Visual Studio Şifre Alanı](../../ide/reference/media/vxpassword.gif)

`type="password"`Bir `input` öğe ekler. Varsayılan olarak, `id="Password1"` ilk parola alanı için, `id="Password2"` ikinci ve benzeri eklenir.

**Giriş (Parola)** girişini Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Uygulamanız kullanıcı adları ve parolalar iletiyorsa, iletimi şifrelemek için web sitenizi Güvenli Soketkatmanı (SSL) kullanacak şekilde yapılandırmanız gerekir. Daha fazla bilgi için bağlantıları [güvence altına alma](/previous-versions/tn-archive/bb418917(v=technet.10))bilgisine bakın. Ayrıca, tüm kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için, [web sayfaları (Jilet) Sitelerine ASP.NET Kullanıcı Girişinin Doğrulanması'na](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)bakın.

**Giriş (Onay kutusu)**

![HTML web sayfası Araç Kutusu Onay Kutusu Seçeneği](../../ide/reference/media/vxcheckbox.gif)

`type="checkbox"`Bir `input` öğe ekler. Görüntülenen metni değiştirmek için özelliği edin. `name` Varsayılan olarak, `id="Checkbox1"` ilk onay kutusu için, `id="Checkbox2"` ikinci ve benzeri eklenir.

**Giriş 'i (Onay kutusu)** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Giriş (Radyo)**

![VisualStudioHTMLpageRadioButton ekran görüntüsü](../../ide/reference/media/vxradio.gif)

`type="radio"`Bir `input` öğe ekler. Görüntülenen metni değiştirmek için özelliği edin. `name` Varsayılan olarak, `id="Radio1"` ilk radyo düğmesi `id="Radio2"` için, ikinci ve benzeri eklenir.

**Giriş (Radyo) Giriş'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Giriş (Gizli)**

![HTML sayfası Gizli Öğe](../../ide/reference/media/vxhidden.gif)

`type="hidden"`Bir `input` öğe ekler. Varsayılan olarak, `id="Hidden1"` ilk gizli alan için, `id="Hidden2"` ikinci ve benzeri eklenir.

**Giriş (Gizli) Giriş'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Metin Alanı**

![HTMLpage Araç Çubuğu Metin Alanı](../../ide/reference/media/vxtextarea.gif)

Bir `textarea` öğe ekler. Metin alanını yeniden boyutlandırabilir veya görüntü alanının ötesine uzanan metni görüntülemek için kaydırma çubuklarını kullanabilirsiniz. Görüntülenen varsayılan metni değiştirmek için özniteliği `value` değiştirin. Varsayılan olarak, `id="textarea1"` ikinci metin alanı `id=" textarea 2"` için ilk metin alanı eklenir, ve benzeri.

**Textarea'yı** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Tüm kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için, [web sayfaları (Jilet) Sitelerine ASP.NET Kullanıcı Girişinin Doğrulanması'na](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)bakın.

**Tablo**

![HTMLpageToolbarTable ekran görüntüsü](../../ide/reference/media/vxtable.gif)

Bir `table` öğe ekler.

**Tablo'yu** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Görüntü**

![HTML sayfası Resim Öğesi](../../ide/reference/media/vximage.gif)

Bir `img` öğe ekler. Bu öğeyi ve `src` metnini `alt` belirtmek için edin.

**Görüntü'yi** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<img alt="" src="">
```

**Seç**

![HTML sayfası Toolbox Açılır](../../ide/reference/media/vxdropdown.gif)

Açılır bırakma `select` öğesi `size` (öznitelik olmadan) ekler. Varsayılan olarak, `id="select1"` ilk liste kutusu için, `id="select2"` ikinci ve benzeri eklenir.

**Seç'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Boyut özelliğinin değerini `select` artırarak çok satırlı bir öğe oluşturabilirsiniz.

**Yatay Kural**

![HTML sayfası Yatay Kural Öğesi](../../ide/reference/media/vxhorizontal.gif)

Bir `hr` öğe ekler. Çizginin kalınlığını artırmak için özniteliği düzenle. `size`

**Yatay Kural'ı** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<hr width="100%" size=1>
```

**Div**

![HTML sayfa Etiketi](../../ide/reference/media/vxlabel.gif)

Öznitelik içeren `div` bir `ms_positioning="FlowLayout"` öğe ekler. Genişlik ve yükseklik dışında, bu öğe Akış Düzen Paneli ile aynıdır. `div` Öğe içinde bulunan metni biçimlendirmek için `class="stylename"` açılış etiketine bir öznitelik ekleyin.

**Div'i** Tasarım görünüm yüzeyine sürüklediğinizde, belgenize aşağıdaki gibi HTML biçimlendirmesi eklenir:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araç Kutusu](../../ide/reference/toolbox.md)
