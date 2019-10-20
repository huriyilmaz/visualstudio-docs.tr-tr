---
title: Araç kutusu, HTML sekmesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3d6eafbafbf9b373028a7ba052ba9e8df62511c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661609"
---
# <a name="toolbox-html-tab"></a>Araç Kutusu, HTML Sekmesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Araç kutusunun **HTML** sekmesi, Web sayfaları ve Web formlarında yararlı olan bileşenleri sağlar. Bu sekmeyi görüntülemek için önce HTML tasarımcısında düzenlenecek bir belgeyi açın. **Görünüm** menüsünde, **araç kutusu**' na tıklayın ve ardından araç kutusunun **HTML** sekmesine tıklayın.

 **HTML** sekmesinde bir aracın örneğini oluşturmak için araca çift tıklayarak geçerli ekleme noktasındaki belgenize ekleyin ya da aracı seçin ve düzen yüzeyi üzerinde istediğiniz konuma sürükleyin.

## <a name="tasks"></a>Görevler

- [Nasıl yapılır: araç kutusu penceresini yönetme](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [Nasıl yapılır: araç kutusu sekmelerini Işleme](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>UI öğeleri
 Aşağıdaki araçlar HTML sekmesinde varsayılan olarak kullanılabilir.

 **İşaretçi** ![ASP.NET mobil tasarımcı HTMLPage işaretçisi](../../ide/reference/media/vxpointer.gif "vxPointer")

 Araç kutusu sekmesi açıldığında bu araç varsayılan olarak seçilidir. Silinemez. İşaretçi, nesneleri Tasarım görünümü yüzeyi üzerine sürüklemenize, yeniden boyutlandırmanıza ve sayfa ya da form üzerinde yeniden konumlandırmanıza olanak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: araç kutusu penceresini yönetme](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) ve [nasıl yapılır: araç kutusu sekmelerini işleme](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 **Giriş (düğme)** ![HTML Web sayfası düğmesi](../../ide/reference/media/vxbutton.gif "vxButton")

 @No__t_1 bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Button1"` ilk düğme için eklenir, ikincisi için `id="Button2"` ve bu şekilde devam eder.

 **Giriş (düğme)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputbutton sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [nib: nasıl yapılır: komut dosyaları oluşturma ve olay Işleyicilerini düzenleme](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Düğme Web sunucusu içerik haritasını](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton> ve @no_ _t_6.

 **Giriş (sıfırlama)** ![HTMLpageResetButton ekran görüntüsü](../../ide/reference/media/vxreset.gif "vxReset")

 @No__t_1 bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Reset1"` ilk sıfırlama düğmesine eklenir, ikincisi için `id="Reset2"` ve bu şekilde devam eder.

 **Girişi (sıfırlama)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputreset sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton> ve <xref:System.Web.UI.WebControls.Button>.

 **Input (Gönder)** ![HTMLpageToolbarSubmitButton ekran görüntüsü](../../ide/reference/media/vxsubmit.gif "Vxgönder")

 @No__t_1 bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Submit1"` ilk Gönder düğmesine eklenir, ikincisi için `id="Submit2"` ve bu şekilde devam eder.

 **Girişi (Gönder)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputgönderim sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton> ve <xref:System.Web.UI.WebControls.Button>.

 **Input (metin)** ![HTMLpageToolbarTextField ekran görüntüsü](../../ide/reference/media/vxtextfield.gif "vxTextfield")

 Belgenize `type="text"` `input` öğesi ekler. Görüntülenen varsayılan metni değiştirmek için `value` özniteliğini düzenleyin. Varsayılan olarak, `id="Text1"` ilk metin alanı için eklenir, ikincisi için `id="Text2"` ve bu şekilde devam eder.

 **Girişi (metin)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputtext sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [TextBox Web Server control Overview](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText> ve <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web sayfalarındaki Kullanıcı girişini doğrulama](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Giriş (dosya)** ![HTML sayfası dosya alanı](../../ide/reference/media/vxfilefield.gif "vxFilefield")

 Belgenize `type="file"` `input` öğesi ekler. Varsayılan olarak, `id="File1"` ilk dosya alanı için eklenir, ikincisi için `id="File2"` ve bu şekilde devam eder.

 **Giriş (dosya)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="File1" type="file" name="File1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputfile sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6)ve <xref:System.Web.UI.HtmlControls.HtmlInputFile>.

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web sayfalarındaki Kullanıcı girişini doğrulama](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Giriş (parola)** ![Visual Studio parolası alanı](../../ide/reference/media/vxpassword.gif "vxPassword")

 @No__t_1 bir `input` öğesi ekler. Varsayılan olarak, `id="Password1"` ilk parola alanı için eklenir, ikincisi için `id="Password2"` ve bu şekilde devam eder.

 **Giriş (parola)** Tasarım görünümü yüzeyine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Password1" type="password" name="Password1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputpassword sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [nasıl yapılır: parola girişi Için metin kutusu Web sunucusu denetimi ayarlama](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310)ve [Izlenecek yol: Web Forms sayfasında Kullanıcı girişini doğrulama](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).

> [!IMPORTANT]
> Uygulamanız kullanıcı adlarını ve parolaları iletitirse, Web sitenizi, iletimi şifrelemek için Güvenli Yuva Katmanı (SSL) kullanacak şekilde yapılandırmanız gerekir. Daha fazla bilgi için [IIS Işlemler Kılavuzu](http://go.microsoft.com/fwlink/?linkid=47856)'NDAKI "SSL Ile bağlantıları güvenli hale getirme" konusuna bakın. Ayrıca, tüm kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web sayfalarındaki Kullanıcı girişini doğrulama](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Giriş (onay kutusu)** ![HTML Web sayfası araç kutusu seçeneği](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

 @No__t_1 bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Checkbox1"` ilk onay kutusu için eklenir, ikincisi için `id="Checkbox2"` ve bu şekilde devam eder.

 **Girişi (onay kutusu)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputcheckbox sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [CheckBox ve CheckBoxList Web Server denetimlerine genel bakış](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox> ve <xref:System.Web.UI.WebControls.CheckBox>.

 **Input (Radio)** ![VisualStudioHTMLpageRadioButton ekran görüntüsü](../../ide/reference/media/vxradio.gif "vxRadio")

 @No__t_1 bir `input` öğesi ekler. Görüntülenen metni değiştirmek için `name` özelliğini düzenleyin. Varsayılan olarak, `id="Radio1"` ilk radyo düğmesi için eklenir, ikincisi için `id="Radio2"` ve bu şekilde devam eder.

 **Girişi (radyo)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Radio1" type="radio" name="Radio1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [Htmlputradiobutton sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton ve RadioButtonList Web sunucusu denetimlerine genel bakış](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton> ve <xref:System.Web.UI.WebControls.RadioButton>.

 **Giriş (gizli)** ![HTML sayfası gizli öğesi](../../ide/reference/media/vxhidden.gif "vxhidden")

 @No__t_1 bir `input` öğesi ekler. Varsayılan olarak, `id="Hidden1"` ilk gizli alan için eklenir, ikincisi için `id="Hidden2"` ve bu şekilde devam eder.

 **Girişi (gizli)** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 Daha fazla bilgi için bkz. [HTML giriş denetimleri](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [htmlputhidden sunucu denetimi bildirim temelli sözdizimi](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9)ve <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.

 **TextArea** ![HTMLPage araç çubuğu metin alanı](../../ide/reference/media/vxtextarea.gif "vxTextarea")

 Bir `textarea` öğesi ekler. Metin alanını yeniden boyutlandırabilir veya görüntüleme alanının ötesinde genişleyen metni görüntülemek için kaydırma çubuklarını kullanabilirsiniz. Görüntülenen varsayılan metni değiştirmek için `value` özniteliğini düzenleyin. Varsayılan olarak, `id="textarea1"` ilk metin alanının eklendiği, ikincisi için `id=" textarea 2"` ve bu şekilde devam eder.

 **Textarea** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 Daha fazla bilgi için bkz. [HtmlTextArea sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea> ve <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> Tüm Kullanıcı girişlerini doğrulamanız önerilir. Daha fazla bilgi için bkz. [ASP.NET Web sayfalarındaki Kullanıcı girişini doğrulama](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Tablo** ![HTMLpageToolbarTable ekran görüntüsü](../../ide/reference/media/vxtable.gif "vxTable")

 Bir `table` öğesi ekler.

 **Tabloyu** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 Daha fazla bilgi için bkz. [HtmlTable sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [tablo, TableRow ve TableCell Web sunucusu denetimine genel bakış](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable> ve <xref:System.Web.UI.WebControls.Table>.

 **Görüntü** ![HTML sayfası resim öğesi](../../ide/reference/media/vximage.gif "Vxımage")

 Bir `img` öğesi ekler. @No__t_0 ve `alt` metnini belirtmek için bu öğeyi düzenleyin.

 **Görüntüyü** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```
<img alt="" src="">
```

 Daha fazla bilgi için bkz. [HtmlImage sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Görüntü Web sunucusu denetimine genel bakış](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage> ve <xref:System.Web.UI.WebControls.Image>.

 ![HTML sayfası araç kutusu açılır menüsünü](../../ide/reference/media/vxdropdown.gif "vxDropdown") seçin

 Bir açılan `select` öğesi ekler (`size` özniteliği olmadan). Varsayılan olarak, `id="select1"` ilk liste kutusu için eklenir, ikincisi için `id="select2"` ve bu şekilde devam eder.

 **Seçimi** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKILER gibi HTML biçimlendirmesi eklenir:

```
<select id="select1" name="select1"><option selected></option></select>
```

 Boyut özelliğinin değerini artırarak çok satırlı `select` öğesi oluşturabilirsiniz.

 Daha fazla bilgi için bkz. [HtmlSelect sunucu denetimi bildirime dayalı sözdizimi](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [nib: nasıl yapılır: betik oluşturma ve olay işleyicilerini düzenleme](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [DropDownList Web sunucusu denetimine genel bakış](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [ListBox Web Server denetimine genel bakış](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect> ve  <xref:System.Web.UI.WebControls.DropDownList>.

 **Yatay kural** ![HTML sayfası yatay kural öğesi](../../ide/reference/media/vxhorizontal.gif "Vxyatay")

 Bir `hr` öğesi ekler. Çizginin kalınlığını artırmak için `size` özniteliğini düzenleyin.

 **Yatay kuralı** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, AŞAĞıDAKI gibi HTML biçimlendirmesi belgenize eklenir:

```
<hr width="100%" size=1>
```

 Daha fazla bilgi için bkz. [HTML yatay kural denetimi](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).

 **Div** ![HTML sayfa etiketi](../../ide/reference/media/vxlabel.gif "vxLabel")

 Bir `ms_positioning="FlowLayout"` özniteliği içeren bir `div` öğesi ekler. Genişlik ve Yükseklik dışında, bu öğe bir akış düzeni paneliyle aynıdır. @No__t_0 öğesi içinde bulunan metni biçimlendirmek için, açma etiketine bir `class="stylename"` özniteliği ekleyin.

 **Div** Tasarım görünümü yüzeyi üzerine sürüklediğinizde, belgenize AŞAĞıDAKI gibi HTML biçimlendirmesi eklenir:

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 Daha fazla bilgi için bkz. [HTML div Control](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Label Web Server Control Overview](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac)ve <xref:System.Web.UI.WebControls.Label>.

## <a name="see-also"></a>Ayrıca Bkz.
 [Araç kutusu](../../ide/reference/toolbox.md) [Standart sekmesi, araç kutusu](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870) [HTML denetimleri](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)
