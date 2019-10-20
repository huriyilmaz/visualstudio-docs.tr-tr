---
title: Parametre bilgisi, liste üyeleri ve hızlı bilgi
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 011542bc45680f6fb5b7bd2b83283605922189ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647352"
---
# <a name="intellisense-in-visual-studio"></a>Visual Studio 'da IntelliSense

IntelliSense, bir dizi özelliği içeren bir kod tamamlama yardımıdır: liste üyeleri, parametre bilgileri, hızlı bilgi ve tam sözcük. Bu özellikler, kullanmakta olduğunuz kod hakkında daha fazla bilgi edinmenize, yazmakta olduğunuz parametreleri izlemenize ve yalnızca birkaç tuş vuruşu ile özelliklere ve yöntemlere çağrılar eklemenize yardımcı olur.

IntelliSense'in birçok yönü dile özgüdür. Farklı diller için IntelliSense hakkında daha fazla bilgi için [Ayrıca bkz](#see-also) . bölümünde listelenen konulara bakın.

## <a name="list-members"></a>Üyeleri Listeleme

Bir tür (veya ad alanı) için geçerli üyelerin listesi, bir tetikleyici karakteri (örneğin, Yönetilen koddaki bir nokta (`.`) veya içindeki C++`::`) yazdıktan sonra görüntülenir. Karakter yazmaya devam ederseniz, liste yalnızca bu karakterlerle başlayan üyeleri içerecek şekilde filtrelenir veya ad içindeki *herhangi bir* sözcüğün başlangıcı bu karakterlerle başlar. IntelliSense Ayrıca "Camel Case" eşleştirmesini da gerçekleştirir, bu nedenle eşleşmeleri görmek için üye adında her bir Camel sözcüğün ilk harfini yazmanız yeterlidir.

Bir öğeyi seçtikten sonra **sekme** tuşuna basarak veya bir boşluk yazarak kodunuzu kodunuza ekleyebilirsiniz. Öğeyi seçip bir nokta yazarsanız, bu noktanın arkasında başka üye listesini getiren bir öğe görüntülenir. Bir öğe seçtiğinizde, öğeyi eklemeden önce öğeye ilişkin Hızlı Bilgi alırsınız.

Üye listesinde, soldaki simge ad alanı, sınıf, işlev veya değişken gibi bir üye türünü temsil eder. Simgelerin listesi için bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Liste oldukça uzun olabilir, bu nedenle listede yukarı veya aşağı taşımak için **PgUp** ve **PgDn** tuşlarına basabilirsiniz.

![Visual Studio üye listesi](../ide/media/vs2015_intellisense.png)

**Ctrl** +**J**yazarak, üyeleri Listele ** >   > ** **Düzenle** **' yi seçerek**veya düzenleyicide **üyeleri Listele** düğmesini seçerek **liste üyeleri** özelliğini el ile çağırabilirsiniz. Toolbar. Boş bir satırda veya tanınabilir bir kapsamın dışında çağrıldığında, bu liste genel ad alanında simgeleri görüntüler.

Liste üyelerini varsayılan olarak devre dışı bırakmak için (özellikle çağrılmadıkça görünmez),**tüm diller**  >  **Araçlar**  > **Seçenekler** ' e gidin ve **otomatik liste üyeleri**' ni kaldırın. Yalnızca belirli bir dil için Liste üyelerini devre dışı bırakmak istiyorsanız bu dilin **genel** ayarlarına gidin.

Sadece yazdığınız metnin kodun içine eklendiği öneri moduna da geçebilirsiniz. Örneğin, listede olmayan bir tanımlayıcı girip **sekme**tuşuna basarsanız, tamamlama modunda giriş, yazılan tanımlayıcının yerini alır. Tamamlama modu ve öneri modu arasında geçiş yapmak için **Ctrl** +**alt** +**Space**tuşlarına basın veya  > **IntelliSense** ' i seçin  > **tamamlama modunu** **değiştirin.**

## <a name="parameter-info"></a>Parametre Bilgisi

Parametre Bilgisi; bir yöntem, öznitelik genel tür parametresi (C#) veya şablon (C++) tarafından istenen parametrelerin sayısı, adları ve türleri hakkında bilgi verir.

Kalın yazı tipli parametre, işlevi yazarken gerekli olan bir sonraki parametreyi gösterir. Aşırı yüklenmiş işlevler için, işlev aşırı yüklemeleri için alternatif parametre bilgilerini görüntülemek üzere **yukarı** ve **aşağı** ok tuşlarını kullanabilirsiniz.

![Parametre Bilgisi](../ide/media/vs2015_param_info.png)

XML Belgeleri yorumlarıyla işlevlere ve parametrelere ek açıklamalar koyduğunuzda, yorumlar Parametre Bilgisi olarak görüntülenir. Daha fazla bilgi için bkz. [XML kodu açıklamalarını sağlama](reference/generate-xml-documentation-comments.md).

Parametre bilgilerini düzenle  > **ıntellisense**  > **parametre bilgilerini** **Düzenle** ' yi seçerek, **CTRL** +**SHIFT** +**alanı**' na basarak veya **parametre bilgilerini** seçerek el ile çağırabilirsiniz. düğmesine basın.

## <a name="quick-info"></a>Hızlı Bilgi

Hızlı bilgi kodunuzdaki herhangi bir tanımlayıcı için bütün bildirimi görüntüler.

![Visual Studio hızlı bilgi](../ide/media/vs2015_quick_info.png)

**Liste üyeleri** kutusundan bir üye seçtiğinizde hızlı bilgi de görünür.

![C&#35; kod dosyasında parametre bilgisi](../ide/media/vs2015_paraminfo.png)

**Ctrl** +**i**tuşlarına basarak veya Düzenleyici araç çubuğunda **hızlı bilgi** düğmesini seçerek hızlı bilgileri **Düzenle**  > **IntelliSense**  > **hızlı**bilgi 'yi seçerek el ile çağırabilirsiniz.

Bir işlev aşırı yüklenmişse, IntelliSense, tüm aşırı yük biçimleri için bilgileri görüntülemeyebilir.

**@No__t_2** **Araçlar** için C++ hızlı bilgi ' yi,  > **metin Düzenleyicisi**  > **C/C++**   > **Gelişmiş**' e giderek ve **otomatik hızlı bilgi** 'yi 2 ayarlayarak devre dışı bırakabilirsiniz.

## <a name="complete-word"></a>Tam Sözcük

Bütün sözcük, dönemi belirsizliğini ortadan kaldırmak için yeterli sayıda karakter girdikten sonra değişken, komut veya işlev adının kalanını tamamlar. Tamam  >   > **IntelliSense** ' i seçerek, **CTRL** + alanı **' na**basarak veya Düzenleyici araç çubuğunda **sözcük Tamam** **düğmesini seçerek** tüm sözcüğü çağırabilirsiniz.

## <a name="intellisense-options"></a>IntelliSense seçenekleri

IntelliSense seçenekleri varsayılan olarak açıktır. Devre dışı bırakmak için **araçlar**  > **Seçenekler**  > **metin düzenleyici** ' yi seçin ve liste üyeleri özelliğini istemiyorsanız, **parametre bilgileri** ' ni veya **otomatik liste üyeleri** ' ni kaldırın.

## <a name="intellisense-icons"></a>IntelliSense simgeleri
IntelliSense 'deki simgeler simge değiştiricilerine ek anlam verebilir. Bunlar, sırasıyla korumalı, dahili veya özel bir şekilde ileten nesnenin simgesinin üzerine, yıldız, kupa ve kilitler katmanlıdır.

|    Simge    |    Erişilebilirlik    |    Açıklama    |
|------------|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Ortak simge değiştiricisi](../ide/media/intellisensePublicNoModifier.png)       |    Genel sınıf    |    Erişim kısıtlı değil.   |
| ![Korumalı simge değiştiricisi](../ide/media/intellisenseProtectedModifier.png)       |    Korumalı sınıf    |    Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.    |
| ![Korumalı Iç simge değiştiricisi](../ide/media/intellisenseProtectedInternalModifier.png)       |    Korumalı iç sınıf    |    Erişim, geçerli derleme veya kapsayan sınıftan türetilmiş türlerle sınırlıdır.    |
| ![İç simge değiştiricisi](../ide/media/intellisenseInternalModifier.png)       |    İç sınıf    |    Erişim, geçerli derleme ile sınırlıdır.    |
|![Özel simge değiştiricisi](../ide/media/intellisensePrivateModifier.png)        |    Özel sınıf    |    Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır. (7,2 tarihinden C# itibaren kullanılabilir.)    |

## <a name="troubleshoot-intellisense"></a>IntelliSense sorunlarını giderme

IntelliSense seçenekleri, belirli durumlarda beklediğiniz gibi çalışmayabilir.

**İmleç bir kod hatasının altında.** IntelliSense kod öğelerini ayrıştıramadığı için imlecin üzerindeki kodda eksik bir işlev veya başka bir hata varsa, IntelliSense 'i kullanmeyebilirsiniz. Uygulanabilir kodu açıklama olarak ekleyerek bu sorunu çözebilirsiniz.

**İmleç bir kod açıklamasındadır.** İmleç, kaynak dosyanızdaki bir açıklamada ise, IntelliSense kullanamazsınız.

**İmleç bir dize sabit değeri içinde.** İmleç, aşağıdaki örnekte olduğu gibi bir dize sabit değeri etrafında tırnak işaretlerinde ise IntelliSense kullanamazsınız:

```cpp
MessageBox( hWnd, "String literal|")
```

**Otomatik seçenekler kapalıdır.** Varsayılan olarak, IntelliSense otomatik olarak işe yarar, ancak devre dışı bırakabilirsiniz. Otomatik deyim tamamlama devre dışı olsa bile, bir IntelliSense özelliğini çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md)
- [C# IntelliSense](../ide/visual-csharp-intellisense.md)
- [JavaScript IntelliSense](../ide/javascript-intellisense.md)
- [Kodu yazma ve yeniden düzenlemeC++()](/cpp/ide/writing-and-refactoring-code-cpp)
- [XML kodu açıklamalarını sağlama](reference/generate-xml-documentation-comments.md)
