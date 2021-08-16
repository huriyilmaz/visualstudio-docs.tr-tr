---
title: C++ Koduyla Çalışma (Sınıf Tasarımcısı)
description: Projedeki C++ kod öğesini, sınıfları ve diğer türleri tasarlamak ve görselleştirmek için sınıf diyagramlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- C++, Class Designer
- Class Designer, C++ support
- Class Designer, limitations
- Class Designer, tasks in C++
- C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 15026141a091b56c930628978007fa93833b80f0ded64df86d23eb091acfce06
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358291"
---
# <a name="work-with-c-code-in-class-designer"></a>Sınıf Tasarımcısı'de C++ koduyla çalışma

**Sınıf Tasarımcısı** projenizin kod öğelerinin görsel bir *gösterimini* sağlayan sınıf diyagramı adlı bir görsel tasarım yüzeyi görüntüler. Sınıf diyagramlarını kullanarak proje içinde sınıfları ve diğer türleri tasarlar ve görselleştirebilirsiniz.

**Sınıf Tasarımcısı** C++ kod öğelerini destekler:

- Sınıf (birden çok devralma ilişkisine sahip olmak dışında yönetilen sınıf şekline benzer)

- Anonim sınıf (Sınıf Görünümü türü için oluşturulan adı görüntüler)

- Şablon sınıfı

- Yapı

- Sabit listesi

- Makro (makronun işlenen görünümünü görüntüler)

- Typedef

> [!NOTE]
> Bu, modelleme çalışmalarında oluşturabilirsiniz UML sınıf diyagramıyla aynı Project. Daha fazla bilgi için bkz. [UML Sınıf Diyagramları: Başvuru.](../../modeling/what-s-new-for-design-in-visual-studio.md)

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Tür çözümleme ve görüntüleme sorunlarını giderme

### <a name="location-of-source-files"></a>Kaynak dosyaların konumu

**Sınıf Tasarımcısı,** kaynak dosyaların konumunu izlemez. Bu nedenle, proje yapınızı değiştirir veya projenizin kaynak dosyalarını taşısanız, **Sınıf Tasarımcısı** türünü (özellikle typedef, temel sınıflar veya ilişkilendirme türlerinin kaynak türü) izleyebilirsiniz. Bu tür bir Sınıf Tasarımcısı **gibi bir hata alabilirsiniz.** Bunu yaptıysanız, değiştirilmiş veya yeniden konumlu kaynak kodu yeniden oynatmak için yeniden sınıf diyagramına sürükleyin.

### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans sorunları

C++ projelerinde, kaynak dosyada yapılan bir değişikliğin sınıf diyagramında görünmesi 30 ile 60 saniye arasında sürebilir. Bu gecikme, **seçimde Sınıf Tasarımcısı** tür bulunamadı **hatasını da neden olabilir.** Bunun gibi bir hata alırsanız, hata iletisinde **İptal'e** tıklayın ve kod öğesinin öğesinde **Sınıf Görünümü.** Bunu tamamladikten **Sınıf Tasarımcısı** türü görüntüleye Sınıf Tasarımcısı gerekir.

Sınıf diyagramı kodda yaptığınız değişikliklerle güncelleştirilene kadar güncelleştirilene kadar diyagramı kapatıp yeniden açmanız gerekir.

### <a name="type-resolution-issues"></a>Tür çözümleme sorunları

**Sınıf Tasarımcısı** aşağıdaki nedenlerle türleri çözümleyeyemeyler:

- Tür, sınıf diyagramını içeren projeden başvurulmayan bir proje veya derlemededir. Bu hatayı düzeltmek için, türü içeren projeye veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için [bkz. Projedeki başvuruları yönetme.](../managing-references-in-a-project.md)

- Tür doğru kapsamda değildir, bu nedenle **Sınıf Tasarımcısı** bulunamaz. Kodun , veya deyimi eksik `using` olduğundan `imports` emin `#include` olur. Ayrıca, türünün (veya ilgili türün) ilk bulunduğu ad alanının dışında taşınmamalarını da sağlar.

- Tür yok (veya açıklamaya alındı). Bu hatayı düzeltmek için türü açıklama veya silmemiş olduğundan emin olun.

- Tür, bir #import yönergesi tarafından başvurulan kitaplıkta bulunur. Olası bir geçici çözüm, oluşturulan kodu (.tlh dosyası) bir #include yönergesine el ile eklemektir.

- Giriş **Sınıf Tasarımcısı** türünü desteklediğini emin olmak. Bkz. [C++ Kod Öğeleri için Sınırlamalar.](#limitations-for-c-code-elements)

Tür çözümleme sorunu için büyük olasılıkla gördüğünüz hata, ' ' sınıf diyagramındaki bir veya daha fazla şekil için **Kod bulunamadı' \<element> hatasıdır.** Bu hata iletisi kodunuzun hatada olduğunu belirtmek zorunda değildir. Yalnızca sınıf tasarımcısının kodunuzu görüntüleyene olduğunu gösterir. Aşağıdaki ölçüleri deneyin:

- Türün mevcut olduğundan emin olun. Kaynak kodun açıklamalarını insorarak açıklama olarak almama veya silmemelerini sağlar.

- Türü çözümlemeyi deneyin. Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede olabilir. Bu hatayı düzeltmek için, türü içeren projeye veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için [bkz. Projedeki başvuruları yönetme.](../managing-references-in-a-project.md)

- Türün doğru kapsamda olduğundan emin olun, böylece Sınıf Tasarımcısı bulun. Kodun , veya deyimi eksik olduğundan `using` `imports` emin `#include` olun. Ayrıca, türünün (veya ilgili türün) ilk bulunduğu ad alanının dışında taşınmamalarını da sağlar.

### <a name="troubleshoot-other-error-messages"></a>Diğer hata iletileriyle ilgili sorunları giderme

Hataları ve uyarıları giderme konusunda yardım almak için Microsoft Geliştirici Network (MSDN) genel forumlarında bulabilirsiniz. Bkz. [Visual Studio Sınıf Tasarımcısı Forumu.](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner)

## <a name="limitations-for-c-code-elements"></a>C++ kod öğelerine ilişkin sınırlamalar

- Bir C++ projesi **yüklendiğinde,** Sınıf Tasarımcısı salt okunur bir şekilde işlev gösterir. Sınıf diyagramını değiştirebilirsiniz, ancak sınıf diyagramındaki değişiklikleri kaynak koda geri kaydedesiniz.

- **Sınıf Tasarımcısı** yerel C++ semantiği destekler. Yönetilen kodda derlenmiş C++ projeleri için **Sınıf Tasarımcısı** yalnızca yerel türler olan kod öğelerini görselleştireceğiz. Bu nedenle, bir projeye sınıf diyagramı eklersiniz, **ancak Sınıf Tasarımcısı** özelliğinin ayar olduğu öğeleri (değer türleri ve başvuru türleri) görselleştirmenize `IsManaged` izin `true` vermez.

- C++ projeleri için **Sınıf Tasarımcısı** türün tanımını okur. Örneğin, bir üst bilgi (.h) dosyasında bir tür tanımladığınız ve bu dosyanın üyelerini bir uygulama (.cpp) dosyasında tanımladığınız varsayalım. Uygulama (.cpp) dosyasında "Sınıf Diyagramını Görüntüle" çağrılarını **Sınıf Tasarımcısı** hiçbir şey görüntülemez. Başka bir örnek olarak, bir .cpp dosyasında diğer dosyaları eklemek için deyimini kullanan ancak gerçek sınıf tanımları içermeden "Sınıf Diyagramını Görüntüle" `#include` Sınıf Tasarımcısı çağırırsanız, **Sınıf Tasarımcısı** bir daha hiçbir şey görüntülemez.

- COM arabirimlerini ve tür kitaplıklarını tanımlayan IDL (.idl) dosyaları, yerel C++ koduna derlenmiş olmadıkça diyagramlarda görüntülenmez.

- **Sınıf Tasarımcısı** genel işlevleri ve değişkenleri desteklemez.

- **Sınıf Tasarımcısı,** birlikteliği desteklemez. Bu, ayrılan belleğin yalnızca birliğin en büyük veri üyesi için gereken miktarın olduğu özel bir sınıf t t'tir.

- **Sınıf Tasarımcısı** ve gibi temel veri türlerini `int` `char` görüntülemez.

- **Sınıf Tasarımcısı,** projenin bu türlere doğru başvuruları yoksa geçerli proje dışında tanımlanan türleri görüntülemez.

- **Sınıf Tasarımcısı** türler görüntüleniyor ancak iç içe tür ile diğer türler arasındaki ilişkiler görüntüleniyor.

- **Sınıf Tasarımcısı** geçersiz olan veya void türünden türeyen türleri görüntüleyemzin.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve Türleri Tasarlama ve Görüntüleme (Sınıf Tasarımcısı)](designing-and-viewing-classes-and-types.md)
- [Sınıf Tasarımcısı Hataları Hakkında Ek Bilgiler](additional-information-about-errors.md)
- [Sınıf Tasarımcısı'de C++ Sınıfları](visual-cpp-classes.md)
- [Sınıf Tasarımcısı'de C++ Yapıları](visual-cpp-structures.md)
- [Sınıf Tasarımcısı'de C++ Sınıf Tasarımcısı](visual-cpp-enumerations.md)
- [Sınıf Tasarımcısı'da C++ Typedefs](visual-cpp-typedefs.md)
