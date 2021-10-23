---
title: Dosyalarda bulma ve değiştirme
description: Dosyalarda Değiştir özelliğini ve belirtilen dosya kümesi kodunda bir dize veya ifade aramanızı ve bulunan eşleşmelerin bir veya hepsini değiştirmenizi nasıl sağlar? hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3b26c84a0db97299ad7a5c0602551ba930722d00
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130212240"
---
# <a name="replace-in-files"></a>Dosyalarda Değiştir

**Dosyalarda Değiştir,** belirtilen dosya kümesinde bir dize veya ifade için arama ve bulunan eşleşmelerin bir veya hepsini değiştirmenize olanak sağlar. Bulunan eşleşmeler ve alınan eylemler Sonuç **seçenekleri'nde seçilen** Sonuçları Bul **penceresinde listelenir.**

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin  ayarlarınıza veya sürümünüze bağlı olarak Yardım'da açıklananlardan farklı olabilir. Ayarlarınızı değiştirmek için, örneğin  Genel veya genel Visual C++ Araçlar İçeri **ve Dışarı** Aktarma Ayarlar ve ardından Tüm  >  ayarları **sıfırla'yı seçin.**

Bul ve Değiştir penceresinde Dosyalarda  **Değiştir'i** görüntülemek için aşağıdaki yöntemlerden birini kullanabilir veya **Ctrl** Shift H tuşlarını +  + **kullanabilirsiniz.**

## <a name="to-display-replace-in-files"></a>Dosyalarda Değiştir'i görüntülemek için

::: moniker range=">=vs-2019"

1. **Ctrl** + **Q tuşlarına** basın ve ekranın üst kısmında yer alan arama kutusuna "değiştir" yazın.

1. Sonuçlar **listesinden Dosyalarda** değiştir'i seçin.

veya

::: moniker-end

1. Düzenle menüsünde **Bul** ve **Değiştir'i genişletin.**

2. Dosyalarda **Değiştir'i seçin.**

   — veya —

   Bul **ve Değiştir penceresi** zaten açıksa, araç çubuğunda Dosyalar'da **Değiştir'i seçin.**

:::moniker range="vs-2017"

## <a name="find-what"></a>Neyi bul

:::moniker-end

:::moniker range=">=vs-2019"

## <a name="find-textbox"></a>Metin kutusunu bulma

::: moniker-end

Yeni bir metin dizesi veya ifade aramak için kutuda belirtin. En son aramak istediğiniz 20 dizeden herhangi birini aramak için açılan listeyi açın ve dizeyi seçin. Arama **dizesinde bir** veya daha fazla normal ifade kullanmak için bitişik expression Builder düğmesini seçin. Daha fazla bilgi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md)

> [!NOTE]
> İfade **Oluşturucusu** düğmesi yalnızca Bul seçenekleri altında Normal **İfadeleri Kullan'ı** **seçtiydiyseniz etkinleştirilir.**

::: moniker range="vs-2017"

## <a name="replace-with"></a>Şununla Değiştir

Bul kutusunda dize örneklerini başka **bir** dizeyle değiştirmek için Replace With kutusuna değiştirme **dizesini** girin. Bul kutusunda dizenin örneklerini silmek **için** bu alanı boş bırakın. En son aranan 20 dizeyi görüntülemek için listeyi açın. Değiştirme **dizesinde bir** veya daha fazla normal ifade kullanmak için bitişik Expression Builder düğmesini seçin. Daha fazla bilgi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md)

::: moniker-end
::: moniker range=">=vs-2019"

## <a name="replace-textbox"></a>Metin kutusunu değiştirme

Bul metin kutusunda dize örneklerini başka **bir** dizeyle değiştirmek için Değiştir metin kutusuna değiştirme **dizesini** girin. Bul metin kutusunda dize örneklerini **silmek** için bu alanı boş bırakın. En son aranan 20 dizeyi görüntülemek için listeyi açın. Değiştirme **dizesinde bir** veya daha fazla normal ifade kullanmak için bitişik Expression Builder düğmesini seçin. Daha fazla bilgi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md)

::: moniker-end

## <a name="look-in"></a>Şuna bakın:

Görünüm açılan listesinden **seçilen seçenek,** Dosyalarda  Değiştir seçeneğinin yalnızca şu anda etkin olan dosyalarda mı yoksa belirli klasörlerde depolanan tüm dosyalarda mı arama yaptığına karar verilsin. Listeden bir arama kapsamı seçin, bir klasör yolu yazın veya Gözat  **(...) düğmesine** tıklayarak Arama Klasörlerini Seç iletişim kutusunu görüntüleyin ve aranecek bir klasör kümesi seçin. Ayrıca, Doğrudan Arama kutusuna bir **yol da girebilirsiniz.**

> [!NOTE]
> Girişe **bak** seçeneği seçiliyse, kaynak kodu denetiminden kullanıma alınmış bir dosyada aramanıza neden oluyorsa, yalnızca yerel makinenize indirilen dosyanın sürümü aranır.

## <a name="find-options"></a>Seçenekleri bulma

Seçenekleri bul bölümünü genişletebilirsiniz **veya daraltabilirsiniz.** Aşağıdaki seçenekler seçilebilir veya temiz olabilir:

**Eşleşme durumu**

Seçildiğinde, Sonuçları **Bul pencereleri** yalnızca arama dizesinin hem içerik hem de büyük/büyük/büyük harfle eşanmış örneklerini görüntüler. Örneğin, Eşleşme büyük/küçük harf  seçiliyken "MyObject" araması "MyObject" ifadesinin "myobject" veya "MYOBJECT" olarak dönüşmese de "MyObject" ifadesinin dönüşe neden olur.

**Tam sözcüğü eşle**

Seçildiğinde, Sonuçları **Bul** pencereleri yalnızca tam sözcüklerle eş değerine sahip arama dizesi örneklerini görüntüler. Örneğin, "MyObject" araması "MyObject" (Nesnem) ifadesinin "CMyObject" veya "MyObjectC" (MyObjectC) ifadesini değil" (MyObjectC) dönüşletir.

**Normal İfadeler Kullanma**

:::moniker range="vs-2017"
Bu onay kutusu seçildiğinde, Bul veya Değiştir metin kutuları içinde metin desenlerini tanımlamak **için özel** **notalar** kullanabilirsiniz. Bu ifadelerin listesi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md).
:::moniker-end
:::moniker range=">=vs-2019"
Bu onay kutusu seçildiğinde, Bul veya Değiştir metin kutularında metin desenlerini tanımlamak için **özel notalar** kullanabilirsiniz.  Bu ifadelerin listesi için [bkz. Normal ifadeleri Visual Studio.](../ide/using-regular-expressions-in-visual-studio.md).
:::moniker-end

**Bu dosya türlerine bakın**

Bu liste, Dizinlerde ara içinde aranan **dosya türlerini** gösterir. Bu alan boş bırakılırsa Dizinlerde ara **dizininde yer alan tüm** dosyalar aranır. Bu belirli türlerde dosyaları bulacak önceden yapılandırılmış bir arama dizesi girmek için listeden herhangi bir öğeyi seçin.

## <a name="result-options"></a>Sonuç seçenekleri

Sonuç seçenekleri bölümünü genişletebilirsiniz **veya daraltabilirsiniz.** Aşağıdaki seçenekler seçilebilir veya temiz olabilir:

**Sonuçları Bul 1** penceresi

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **1 penceresinin içeriğinin yerini** alar. Arama sonuçlarınızı görüntülemek için bu pencere otomatik olarak açılır. Bu pencereyi el ile açmak için Görünüm **menüsünden Diğer** **Windows'ı** seçin ve Sonuçları Bul **1'i seçin.**

**Sonuçları Bul 2** penceresi

Seçildiğinde, geçerli aramanın sonuçları Sonuçları Bul **2 penceresinin içeriğinin yerini** alar. Arama sonuçlarınızı görüntülemek için bu pencere otomatik olarak açılır. Bu pencereyi el ile açmak için Görünüm **menüsünden Diğer** **Windows'ı** seçin ve Sonuçları Bul **2'yi seçin.**

**Yalnızca dosya adlarını görüntüleme**

Bu onay kutusu seçildiğinde, Sonuçları **Bul** pencereleri, arama dizesini içeren tüm dosyaların tam adlarını ve yollarını listele. Ancak sonuçlar, dizenin göründüğü kod satırına dahil değildir. Bu onay kutusu yalnızca Dosyalarda **Bul için** kullanılabilir.

**Değiştirilen dosyaları, Hepsini Değiştir'den sonra açık tut**

Seçildiğinde, değişiklikleri geri almak veya kaydetmek için değiştirmelerin yapılmış olduğu tüm dosyaları açık bırakır. Bellek kısıtlamaları, değiştirme işlemi sonrasında açık kalabilirsiniz dosya sayısını sınırlayıcı olabilir.

> [!CAUTION]
> Geri **Al'a** yalnızca düzenleme için açık kalan dosyalarda kullanabilirsiniz. Bu seçenek seçilmezse, düzenleme için açık olan dosyalar kapalı  kalır ve bu dosyalarda Geri Al seçeneği kullanılamaz.

::: moniker range=">=vs-2022"
> [!NOTE]
> 2022'Visual Studio başlayarak, son sonuçlar kullanılabilir duruma gelmeden önce, önceden dizine ekli dosyalarda olduğu gibi kısmi sonuçlar göstererek arama performansı iyileştirilmiş olur. Ancak, değiştirme işlemlerini gerçekleştirdikten sonra bu performans avantajı geçerli değildir çünkü değiştirme işlemleri yalnızca tam arama sonuçları döndürüldikten sonra başlatıldı.
::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Metin bulma ve değiştirme](../ide/finding-and-replacing-text.md)
- [Dosyalarda bulma](../ide/find-in-files.md)
- [Visual Studio komutları](../ide/reference/visual-studio-commands.md)
