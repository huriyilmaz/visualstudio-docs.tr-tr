---
title: IntelliSense kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vc.tools.intellisense
helpviewer_keywords:
- IntelliSense, Complete Word
- IntelliSense, completion mode
- parameter information
- IntelliSense, List Members
- Quick Info
- Parameter Info
- IntelliSense [Visual Studio]
- IntelliSense, suggestion mode
- IntelliSense, Parameter Info
- IntelliSense, customizing
- Complete Word
- IntelliSense
- List Members
ms.assetid: 9fdb489b-8b46-4b92-9ccc-c8f8cc184081
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 735f93b2f900b8681a1e9fee490de8e4b697f9e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656441"
---
# <a name="using-intellisense"></a>IntelliSense Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense; Üyeleri Listeleme, Parametre Bilgisi, Hızlı Bilgi ve Tam Sözcük gibi bir dizi özellik için kullanılan genel bir terimdir. Bu özellikler, yalnızca birkaç tuş vuruşu ile kullandığınız kod hakkında daha fazla bilgi edinmenize, yazmakta olduğunuz parametreleri izlemenize ve özellik ve yöntem çağrıları eklemenize yardımcı olur.

 IntelliSense'in birçok yönü dile özgüdür. Farklı dillere yönelik IntelliSense hakkında daha fazla bilgi için Ayrıca Bkz. altında listelenen konulara bakın.

## <a name="list-members"></a>Üyeleri Listeleme
 Bir tür (veya ad alanı) için geçerli üyelerin listesi, bir tetikleyici karakteri (örneğin, `.` yönetilen kodda veya C++ ' da bir nokta () yazdığınızda görüntülenir `::` . Karakterleri yazmaya devam ederseniz, liste yalnızca bu karakterlerle başlayan üyeleri içerecek şekilde filtrelenir.

 Bir öğeyi seçtikten sonra SEKME tuşuna basarak veya bir boşluk girerek öğeyi kodunuza ekleyebilirsiniz. Öğeyi seçip bir nokta yazarsanız, bu noktanın arkasında başka üye listesini getiren bir öğe görüntülenir. Bir öğe seçtiğinizde, öğeyi eklemeden önce öğeye ilişkin Hızlı Bilgi alırsınız.

 Üye listesinde, soldaki simge ad alanı, sınıf, işlev veya değişken gibi bir üye türünü temsil eder. Simgelerin listesi için bkz. [sınıf görünümü ve nesne tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md). Liste oldukça uzun olabilir; bu yüzden listede yukarı veya aşağı gitmek için PAGE UP ve PAGE DOWN tuşlarına basabilirsiniz.

 ![Visual Studio üye listesi](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

 CTRL + J yazarak, **Düzenle/IntelliSense/üyeleri Listele**' ye tıklayarak veya Düzenleyici araç çubuğunda **üyeleri Listele** düğmesine tıklayarak, **üyeleri Listele** özelliğini el ile çağırabilirsiniz. Boş bir satırda veya tanınabilir bir kapsamın dışında çağrıldığında, bu liste genel ad alanında simgeleri görüntüler.

 Liste üyelerini varsayılan olarak devre dışı bırakmak için (özellikle çağrılmadıkça gözükmemesi için), **Araçlar/Seçenekler/tüm diller** ' e gidin ve **üyeleri otomatik Listele**seçeneğinin işaretini kaldırın. Yalnızca belirli bir dil için Liste üyelerini devre dışı bırakmak istiyorsanız bu dilin **genel** ayarlarına gidin.

 Sadece yazdığınız metnin kodun içine eklendiği öneri moduna da geçebilirsiniz. Örneğin, listede olmayan bir tanımlayıcı girip SEKME tuşuna basarsanız, tamamlama modunda bu giriş yazılan tanımlayıcının yerini alır. Tamamlama modu ve öneri modu arasında geçiş yapmak için CTRL + ALT + ara çubuğu tuşlarına basın veya **Düzenle/IntelliSense/tamamlama modu**' na tıklayın.

## <a name="parameter-info"></a>Parametre Bilgisi
 Parametre Bilgisi; bir yöntem, öznitelik genel tür parametresi (C#) veya şablon (C++) tarafından istenen parametrelerin sayısı, adları ve türleri hakkında bilgi verir.

 Kalın yazı tipli parametre, işlevi yazarken gerekli olan bir sonraki parametreyi gösterir. Aşırı yüklenmiş işlevler için, işlev aşırı yüklerine ilişkin alternatif parametre bilgilerini görüntülemek üzere YUKARI ve AŞAĞI ok tuşlarını kullanabilirsiniz.

 ![Parametre Bilgisi](../ide/media/vs2015-param-info.png "VS2015_param_Info")

 XML Belgeleri yorumlarıyla işlevlere ve parametrelere ek açıklamalar koyduğunuzda, yorumlar Parametre Bilgisi olarak görüntülenir. Daha fazla bilgi için bkz. [XML kodu açıklamaları sağlama](../ide/supplying-xml-code-comments.md).

 **IntelliSense/parametre bilgilerini düzenle**' ye TıKLAYARAK, CTRL + SHIFT + boşluk yazarak ya da Düzenleyici araç çubuğundaki **parametre bilgisi** düğmesine tıklayarak parametre bilgilerini el ile çağırabilirsiniz.

## <a name="quick-info"></a>Hızlı Bilgi
 Hızlı bilgi kodunuzdaki herhangi bir tanımlayıcı için bütün bildirimi görüntüler.

 ![Visual Studio hızlı bilgi](../ide/media/vs2015-quick-info.png "VS2015_Quick_info")

 **Liste üyeleri** kutusundan bir üye seçtiğinizde hızlı bilgi de görünür.

 ![C&#35; kod dosyasında parametre bilgisi](../ide/media/vs2015-paraminfo.png "VS2015_ParamInfo")

 Hızlı bilgi 'yi **Düzenle/IntelliSense/hızlı bilgi**'ye TıKLAYARAK, CTRL + I tuşlarına basarak veya Düzenleyici araç çubuğundaki **hızlı bilgi** düğmesine tıklayarak el ile çağırabilirsiniz.

 Bir işlev aşırı yüklenmişse, IntelliSense, tüm aşırı yük biçimleri için bilgileri görüntülemeyebilir.

 C++ ' da, **Araçlar/Seçenekler/metin düzenleyici/C/C++/Advanced/Auto hızlı bilgi** ' yi ayarlayarak hızlı bilgi 'yi kapatabilirsiniz `false` .

## <a name="complete-word"></a>Tam Sözcük
 Tam Sözcük, terim belirsizliğini ortadan kaldıracak yeterli sayıda karakter girdikten sonra değişken, komut veya işlev adının kalanını tamamlar. Tüm sözcüğü, **Düzenle/IntelliSense/Tamam**' a TıKLAYARAK, CTRL + boşluk yazarak veya Düzenleyici araç çubuğunda **sözcüğü Tamam** düğmesine tıklayarak çağırabilirsiniz.

## <a name="intellisense-options"></a>IntelliSense Seçenekleri
 IntelliSense seçenekleri varsayılan olarak açıktır. Devre dışı bırakmak için, **Araçlar/Seçenekler/metin düzenleyici** ' ye tıklayın ve liste üyeleri özelliğini Istemiyorsanız, **parametre bilgileri** veya **üyeleri otomatik Listele** seçimini kaldırın.

## <a name="troubleshooting-intellisense"></a>IntelliSense Sorunlarını Giderme
 IntelliSense seçenekleri, belirli durumlarda beklediğiniz gibi çalışmayabilir.

 **İmleç bir kod hatasının altında.** IntelliSense kod öğelerini ayrıştıramadığı için imlecin üzerindeki kodda eksik bir işlev veya başka bir hata varsa, IntelliSense 'i kullanmeyebilirsiniz. Uygulanabilir kodu açıklama olarak ekleyerek bu sorunu çözebilirsiniz.

 **İmleç bir kod açıklamasındadır.** İmleç, kaynak dosyanızdaki bir açıklamada ise, IntelliSense kullanamazsınız.

 **İmleç bir dize sabit değeri içinde.** İmleç, aşağıdaki örnekte olduğu gibi bir dize sabit değeri etrafında tırnak işaretlerinde ise IntelliSense kullanamazsınız:

```
MessageBox( hWnd, "String literal|") )
```

 **Otomatik seçenekler kapalıdır.** Varsayılan olarak, IntelliSense otomatik olarak işe yarar, ancak devre dışı bırakabilirsiniz. Otomatik deyim tamamlama devre dışı olsa bile, bir IntelliSense özelliğini çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Basic özel IntelliSense](../ide/visual-basic-specific-intellisense.md) [Visual C# ıNTELLISENSE](../ide/visual-csharp-intellisense.md) [JavaScript IntelliSense](../ide/javascript-intellisense.md) [XML kodu açıklamaları sağlama](../ide/supplying-xml-code-comments.md)
