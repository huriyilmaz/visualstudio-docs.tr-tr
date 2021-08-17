---
title: Parametre bilgileri, liste üyeleri ve hızlı bilgiler
description: 'Şu IntelliSense özelliklerini kullanmayı öğrenin: Liste Üyeleri, Parametre Bilgileri, Hızlı Bilgi ve Tam Sözcük.'
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- Quick info
- Parameter info
- Complete word
- List members
- IntelliSense [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5d395a170a9daee3bfd4544b34fa1a203f6a9df9ba8d63d36266a7c588838548
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121399789"
---
# <a name="intellisense-in-visual-studio"></a>Visual Studio'de IntelliSense

IntelliSense, bir dizi özelliği içeren bir kod tamamlama yardımıdır: Liste Üyeleri, Parametre Bilgileri, Hızlı Bilgi ve Tam Sözcük. Bu özellikler, kullanmakta olduğunu kod hakkında daha fazla bilgi edinirken, yazdığınız parametreleri takip etmeye ve yalnızca birkaç tuş vuruşu ile özelliklere ve yöntemlere çağrılar eklemenize yardımcı olur.

IntelliSense'in birçok yönü dile özgüdür. Farklı diller için IntelliSense hakkında daha fazla bilgi için Ayrıca bkz. bölümünde [listelenen konulara](#see-also) bakın.

## <a name="list-members"></a>Üyeleri Listeleme

Yönetilen kodda veya C++'da bir tetikleyici karakteri (örneğin, nokta ( ) girdikten sonra bir türdeki (veya ad alanı) geçerli üyelerin listesi `.` `::` görüntülenir. Karakterleri yazmaya devam edersanız, liste yalnızca bu karakterlerle başlayan veya ad içindeki  herhangi bir sözcüğün başlangıcının bu karakterlerle başladığı üyeleri içerecek şekilde filtrelenmiş. IntelliSense ayrıca "büyük/küçük harf" eşleştirmesi de yapar, bu nedenle eşleşmeleri görmek için üye adına her bir büyük harfli sözcüğün ilk harfini yazman gerekir.

Bir öğeyi seçdikten sonra Sekme tuşuna basarak veya bir boşluk **yazarak** kodunıza ebilirsiniz. Öğeyi seçip bir nokta yazarsanız, bu noktanın arkasında başka üye listesini getiren bir öğe görüntülenir. Bir öğe seçtiğinizde, öğeyi eklemeden önce öğeye ilişkin Hızlı Bilgi alırsınız.

Üye listesinde, soldaki simge ad alanı, sınıf, işlev veya değişken gibi bir üye türünü temsil eder. Simgelerin listesi için bkz. [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri.](../ide/class-view-and-object-browser-icons.md) Liste oldukça uzun olabilir, bu nedenle listede yukarı veya aşağı taşımak için **PgUp** ve **PgDn'ye** basabilirsiniz.

![Visual Studio Üye Listesi](../ide/media/vs2015_intellisense.png)

**Ctrl** J  yazarak, +    >  **IntelliSense**  >    Liste Üyelerini Düzenle'yi seçerek veya düzenleyici araç çubuğundaKi Üyeleri Listele düğmesini seçerek Liste Üyeleri özelliğini el ile çağırabilirsiniz. Boş bir satırda veya tanınabilir bir kapsamın dışında çağrıldığında, bu liste genel ad alanında simgeleri görüntüler.

Liste Üyelerini varsayılan olarak kapatmak için (özellikle çağrılmadıkça görünmeysin) Araçlar Seçenekler Tüm Diller'e gidin ve Üyeleri otomatik  >    >   **listele seçeneğini kaldırın.** Yalnızca belirli bir dil için Liste Üyelerini kapatmak için ilgili dil için **Genel** ayarlar'a gidin.

Sadece yazdığınız metnin kodun içine eklendiği öneri moduna da geçebilirsiniz. Örneğin, listede yer alan bir tanımlayıcıyı girer ve **Sekme** tuşuna bassanız tamamlama modunda giriş, türü doğru olan tanımlayıcının yerini alar. Tamamlama modu ile öneri modu arasında geçiş yapmak için **Ctrl** Alt Ara Çubuğuna basın veya IntelliSense Tamamlama Modunu +  +    >    >  **Düzenle'yi seçin.**

## <a name="parameter-info"></a>Parametre Bilgisi

Parametre Bilgisi; bir yöntem, öznitelik genel tür parametresi (C#) veya şablon (C++) tarafından istenen parametrelerin sayısı, adları ve türleri hakkında bilgi verir.

Kalın yazı tipli parametre, işlevi yazarken gerekli olan bir sonraki parametreyi gösterir. Aşırı yüklenmiş işlevlerde, işlev aşırı  yüklemeleri **için** alternatif parametre bilgilerini görüntülemek üzere Yukarı ve Aşağı ok tuşlarını kullanabilirsiniz.

![Parametre Bilgisi](../ide/media/vs2015_param_info.png)

XML Belgeleri yorumlarıyla işlevlere ve parametrelere ek açıklamalar koyduğunuzda, yorumlar Parametre Bilgisi olarak görüntülenir. Daha fazla bilgi için [bkz. XML kod açıklamalarını girin.](reference/generate-xml-documentation-comments.md)

IntelliSense Parametre Bilgilerini Düzenle'yi seçerek,  >    >   **Ctrl** Shift Tuşu tuşlarına basarak veya düzenleyici araç çubuğunda Parametre Bilgisi düğmesini seçerek Parametre Bilgilerini el +  + ile çağırabilirsiniz. 

## <a name="quick-info"></a>Hızlı Bilgi

Hızlı bilgi kodunuzdaki herhangi bir tanımlayıcı için bütün bildirimi görüntüler.

![Visual Studio Hızlı Bilgi](../ide/media/vs2015_quick_info.png)

Üyeleri Listele kutusundan **bir üyeyi seçerek** Hızlı Bilgi de görünür.

![C kod dosyasında parametre&#35; bilgileri](../ide/media/vs2015_paraminfo.png)

IntelliSense Hızlı Bilgilerini Düzenle'yi seçerek, Ctrl K , Ctrl I tuşlarına basarak veya düzenleyici araç çubuğunda Hızlı Bilgi düğmesini seçerek Hızlı Bilgi'yi  >    >  el  +   + ile çağırabilirsiniz. 

Bir işlev aşırı yüklenmişse, IntelliSense, tüm aşırı yük biçimleri için bilgileri görüntülemeyebilir.

Araçlar Seçenekler Metin Düzenleyicisi C/C++ Gelişmiş 'e giderek ve Otomatik Hızlı Bilgi'yi olarak ayarerek C++ kodu için Hızlı  >    >    >    >   **Bilgi'yi kapatabilirsiniz.** `false`

## <a name="complete-word"></a>Tam Sözcük

Complete Word bir değişkenin, komutun veya işlev adının geri kalanını, terimin tam olarak ne olduğunu ortaya atacak kadar karakter girdikten sonra tamamlar. IntelliSense Tam Sözcüğü Düzenle'yi seçerek, Ctrl Ara Çubuğuna basarak veya düzenleyici araç çubuğundaKi Sözcüğü Tamamla düğmesini seçerek Tam  >    >    +  **Sözcük** çağırabilirsiniz.

## <a name="intellisense-options"></a>IntelliSense seçenekleri

IntelliSense seçenekleri varsayılan olarak açıktır. Bunları kapatmak için Araçlar Seçenekler **Metin Düzenleyicisi'ni** seçin ve Üyeleri Listele özelliğini istemiyorsanız Parametre  >    >   bilgileri'nin veya Otomatik liste üyelerinin  seçimini kaldırın. 

## <a name="intellisense-icons"></a>IntelliSense simgeleri
IntelliSense'in simgeleri, simge değiştiricileriyle ek anlamlar ifade ediyor olabilir. Bunlar, nesne simgesinin üzerine, sırasıyla korumalı, iç veya özel olarak aktaran yıldız, kalp ve kilitlerdir.

|    Simge    |    Erişilebilirlik    |    Açıklama    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Genel Simge Değiştiricisi](../ide/media/intellisensePublicNoModifier.png)       |    Genel sınıf    |    Erişim kısıtlanmaz.   |
| ![Korumalı Simge Değiştirici](../ide/media/intellisenseProtectedModifier.png)       |    Korumalı sınıf    |    Erişim, içeren sınıf veya içeren sınıftan türetilen türler ile sınırlıdır.    |
| ![Korumalı İç Simge Değiştiricisi](../ide/media/intellisenseProtectedInternalModifier.png)       |    Korumalı iç sınıf    |    Erişim, geçerli derleme veya içeren sınıftan türetilen türler ile sınırlıdır.    |
| ![İç Simge Değiştiricisi](../ide/media/intellisenseInternalModifier.png)       |    İç sınıf    |    Erişim geçerli derlemeyle sınırlıdır.    |
|![Özel Simge Değiştiricisi](../ide/media/intellisensePrivateModifier.png)        |    Özel sınıf    |    Erişim, içeren sınıf veya geçerli derleme içindeki içeren sınıftan türetilen türler ile sınırlıdır. (C# 7.2'den itibaren kullanılabilir.)    |

## <a name="troubleshoot-intellisense"></a>IntelliSense sorunlarını giderme

IntelliSense seçenekleri, belirli durumlarda beklediğiniz gibi çalışmayabilir.

**İmleç bir kod hatasının altında.** IntelliSense kod öğelerini ayrıştıramayabilecek olabileceği için imlecin üzerindeki kodda eksik bir işlev veya başka bir hata varsa IntelliSense'i kullanamayabilirsiniz. Uygulanabilir kodu açıklama olarak ekleyerek bu sorunu çözebilirsiniz.

**İmleç bir kod açıklamasındadır.** İmleç, kaynak dosyanız içinde bir açıklama içinde yer alırsa IntelliSense'i kullanılamaz.

**İmleç bir dize değişmez değeri içindedir.** Aşağıdaki örnekte olduğu gibi, imleç bir dize değişmez değeri çevresindeki tırnak işaretleri içinde ise IntelliSense'i kullanaazın:

```cpp
MessageBox( hWnd, "String literal|")
```

**Otomatik seçenekler kapalıdır.** Varsayılan olarak, IntelliSense otomatik olarak çalışır, ancak devre dışı abilirsiniz. Otomatik deyim tamamlama devre dışı olsa bile, bir IntelliSense özelliğini çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [Python IntelliSense](../python/editing-python-code-in-visual-studio.md#intellisense)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Kod yazma ve yeniden düzenleme (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [XML kod açıklamalarını girin](reference/generate-xml-documentation-comments.md)
