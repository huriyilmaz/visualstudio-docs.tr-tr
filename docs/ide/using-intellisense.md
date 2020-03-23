---
title: Parametre bilgileri, liste üyeleri ve hızlı bilgi
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34e038256d46909e135f8285cb1b3edc45d0ba3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565350"
---
# <a name="intellisense-in-visual-studio"></a>IntelliSense in Visual Studio

IntelliSense bir dizi özellik içeren bir kod tamamlama yardımıdır: Liste Üyeleri, Parametre Bilgileri, Hızlı Bilgi ve Tam Word. Bu özellikler, kullandığınız kod hakkında daha fazla bilgi edinmenize, yazmakta olduğunuz parametreleri izlemenize ve yalnızca birkaç tuş vuruşuyla özelliklere ve yöntemlere çağrılar eklemenize yardımcı olur.

IntelliSense'in birçok yönü dile özgüdür. Farklı diller için IntelliSense hakkında daha fazla bilgi [See also](#see-also) için bkz.

## <a name="list-members"></a>Üyeleri Listeleme

Bir tetikleyici karakter yazdıktan sonra (örneğin, yönetilen kodda veya`.` `::` C++'da bir dönem ) bir türdeki geçerli üyelerin listesi görüntülenir. Karakterleri yazmaya devam ederseniz, liste yalnızca bu karakterlerle başlayan veya ad içindeki herhangi *bir* sözcüğün başlangıcının bu karakterlerle başladığı üyeleri içerecek şekilde filtrelenir. IntelliSense de "deve durumda" eşleştirme gerçekleştirir, böylece sadece eşleşen görmek için üye adı her deve kasalı kelimenin ilk harfi yazabilirsiniz.

Bir öğe seçtikten sonra, **Sekme** tuşuna basarak veya bir boşluk yazarak kodunuzun içine ekleyebilirsiniz. Öğeyi seçip bir nokta yazarsanız, bu noktanın arkasında başka üye listesini getiren bir öğe görüntülenir. Bir öğe seçtiğinizde, öğeyi eklemeden önce öğeye ilişkin Hızlı Bilgi alırsınız.

Üye listesinde, soldaki simge ad alanı, sınıf, işlev veya değişken gibi bir üye türünü temsil eder. Simgelerin listesi için [Sınıf Görünümü ve Nesne Tarayıcı simgelerine](../ide/class-view-and-object-browser-icons.md)bakın. Liste oldukça uzun olabilir, bu nedenle listede yukarı veya aşağı taşımak için **PgUp** ve **PgDn** tuşuna basabilirsiniz.

![Visual Studio Üye Listesi](../ide/media/vs2015_intellisense.png)

**Liste Üyeleri** özelliğini **Ctrl**+**J**yazarak,**IntelliSense** > **Liste Üyelerini** **Edit'i** > seçerek veya düzenleyici araç çubuğundaki **Liste Üyeleri** düğmesini seçerek manuel olarak çağırabilirsiniz. Boş bir satırda veya tanınabilir bir kapsamın dışında çağrıldığında, bu liste genel ad alanında simgeleri görüntüler.

Liste Üyelerini varsayılan olarak kapatmak için (özellikle çağrılmadığı sürece görünmemesi için),**Tüm Dilleri** **AraçlarA** > Göre**Seçenekleri'ne** > gidin ve **Otomatik liste üyelerini**seçin. Liste Üyeleri'ni yalnızca belirli bir dil için kapatmak istiyorsanız, o dilin **Genel** ayarlarına gidin.

Sadece yazdığınız metnin kodun içine eklendiği öneri moduna da geçebilirsiniz. Örneğin, listede olmayan bir tanımlayıcı girer ve tamamlanma modunda **Tab**tuşuna baslarsanız, giriş yazılan tanımlayıcının yerini alır. Tamamlama modu ile öneri modu arasında geçiş yapmak için **Ctrl**+**Alt**+**Space'e**basın veya**IntelliSense** > **Geçiş Tamamlama Modunu** **Edit'i** > seçin.

## <a name="parameter-info"></a>Parametre Bilgisi

Parametre Bilgisi; bir yöntem, öznitelik genel tür parametresi (C#) veya şablon (C++) tarafından istenen parametrelerin sayısı, adları ve türleri hakkında bilgi verir.

Kalın yazı tipli parametre, işlevi yazarken gerekli olan bir sonraki parametreyi gösterir. Aşırı yüklü işlevler **için,** işlev aşırı yüklemeleri için alternatif parametre bilgilerini görüntülemek için Yukarı ve **Aşağı** ok tuşlarını kullanabilirsiniz.

![Parametre Bilgisi](../ide/media/vs2015_param_info.png)

XML Belgeleri yorumlarıyla işlevlere ve parametrelere ek açıklamalar koyduğunuzda, yorumlar Parametre Bilgisi olarak görüntülenir. Daha fazla bilgi için [Bkz. Kaynağı XML kodu açıklamaları.](reference/generate-xml-documentation-comments.md)

**IntelliSense** > **Parametre Bilgilerini** **Edit'i** > seçerek , **Ctrl**+**Shift**+**Space**tuşuna basarak veya düzenleyici araç çubuğundaki Parametre Bilgisi düğmesini seçerek **Parametre Bilgilerini** el ile arayabilirsiniz.

## <a name="quick-info"></a>Hızlı Bilgi

Hızlı bilgi kodunuzdaki herhangi bir tanımlayıcı için bütün bildirimi görüntüler.

![Visual Studio Hızlı Bilgi](../ide/media/vs2015_quick_info.png)

**Üye Listesi** kutusundan bir üye seçtiğinizde, Hızlı Bilgi de görüntülenir.

![C&#35; kod dosyasındaki Parametre Bilgileri](../ide/media/vs2015_paraminfo.png)

**IntelliSense** > **Hızlı Bilgi** **Edit'i** > seçerek , **Ctrl**+**I**tuşuna basarak veya düzenleyici araç çubuğundaki Hızlı Bilgi düğmesini seçerek Hızlı **Bilgi'yi** el ile arayabilirsiniz.

Bir işlev aşırı yüklenmişse, IntelliSense, tüm aşırı yük biçimleri için bilgileri görüntülemeyebilir.

**Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C/C++** > **Gelişmiş'e**gidip Otomatik Hızlı Bilgi'yi ayarlayarak C++ kodu için **Hızlı Bilgi'yi** `false`kapatabilirsiniz.

## <a name="complete-word"></a>Tam Sözcük

Tam Word, terimi birbirinden ayrıştıracak yeterli karakter girdikten sonra bir değişkenin, komutun veya işlev adının geri kalanını tamamlar. **IntelliSense** > **Complete Word'u** **Edit** > seçerek, **Ctrl**+**Space**tuşuna basarak veya düzenleyici araç çubuğundaki Tam Word düğmesini seçerek Tam **Word'u** çağırabilirsiniz.

## <a name="intellisense-options"></a>IntelliSense seçenekleri

IntelliSense seçenekleri varsayılan olarak açıktır. Bunları kapatmak **için, Araç** > **Seçenekleri** > Metin Düzenleyicisi'ni seçin ve Liste Üyeleri özelliğini istemiyorsanız **Parametre bilgilerini** veya **Otomatik liste üyelerini** seçin.**Text Editor**

## <a name="intellisense-icons"></a>IntelliSense simgeleri
IntelliSense'deki simgeler simge değiştiriciler ile ek anlam lar ifade edebilir. Bunlar, nesnenin simgesinin üzerine katmanlı yıldızlar, kalpler ve kilitlerdir ve sırasıyla korumalı, dahili veya özel olarak iletilir.

|    Simge    |    Erişilebilirlik    |    Açıklama    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Genel Simge Değiştirici](../ide/media/intellisensePublicNoModifier.png)       |    Genel sınıf    |    Erişim sınırlı değildir.   |
| ![Korumalı Simge Değiştirici](../ide/media/intellisenseProtectedModifier.png)       |    Korumalı sınıf    |    Erişim, içeren sınıfveya içeren sınıftan türetilen türlerle sınırlıdır.    |
| ![Korumalı İç Simge Değiştirici](../ide/media/intellisenseProtectedInternalModifier.png)       |    Korumalı dahili sınıf    |    Erişim, geçerli derleme yle veya içeren sınıftan türetilen türlerle sınırlıdır.    |
| ![İç Simge Değiştirici](../ide/media/intellisenseInternalModifier.png)       |    Dahili sınıf    |    Erişim geçerli derleme ile sınırlıdır.    |
|![Özel Simge Değiştirici](../ide/media/intellisensePrivateModifier.png)        |    Özel sınıf    |    Erişim, geçerli derleme içindeki içeren sınıftan türetilen sınıf veya türlerle sınırlıdır. (C# 7.2'den beri mevcuttur.)    |

## <a name="troubleshoot-intellisense"></a>Sorun Giderme IntelliSense

IntelliSense seçenekleri, belirli durumlarda beklediğiniz gibi çalışmayabilir.

**İmleç bir kod hatasının altındadır.** İmlecin üstündeki kodda eksik bir işlev veya başka bir hata varsa IntelliSense'i kullanamayabilirsiniz, çünkü IntelliSense kod öğelerini ayrışdıramayabilir. Uygulanabilir kodu açıklama olarak ekleyerek bu sorunu çözebilirsiniz.

**İmleç bir kod yorumundadır.** İmleç kaynak dosyanızdaki bir yorumdaysa IntelliSense'i kullanamazsınız.

**İmleç bir dize gerçek içindedir.** İmleç, aşağıdaki örnekte olduğu gibi, bir dize gerçek etrafında tırnak işaretleri ise IntelliSense kullanamazsınız:

```cpp
MessageBox( hWnd, "String literal|")
```

**Otomatik seçenekler kapatılır.** Varsayılan olarak, IntelliSense otomatik olarak çalışır, ancak devre dışı kullanabilirsiniz. Otomatik deyim tamamlama devre dışı olsa bile, bir IntelliSense özelliğini çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Yazma ve yeniden düzenleme kodu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Tedarik XML kod açıklamaları](reference/generate-xml-documentation-comments.md)
