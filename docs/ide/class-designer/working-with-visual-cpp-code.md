---
title: C++ kodu ile çalışma (Sınıf Tasarımcısı)
description: C++ kod öğesini, sınıfları ve bir projedeki diğer türleri tasarlamak ve görselleştirmek için sınıf diyagramlarını nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: f1bfa6a64d8c48b92118d7a21fe9e10fce2e84c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041392"
---
# <a name="work-with-c-code-in-class-designer"></a>Sınıf Tasarımcısı C++ koduyla çalışma

**Sınıf Tasarımcısı** , projenizdeki kod öğelerinin görsel gösterimini sağlayan *sınıf diyagramı* adlı bir görsel tasarım yüzeyi görüntüler. Bir projedeki sınıfları ve diğer türleri tasarlamak ve görselleştirmek için sınıf diyagramlarını kullanabilirsiniz.

**Sınıf Tasarımcısı** aşağıdaki C++ kod öğelerini destekler:

- Sınıf (birden fazla devralma ilişkisine sahip olması dışında, yönetilen bir sınıf şekline benzer)

- Anonim Sınıf (Sınıf Görünümü, anonim tür için üretilen adı görüntüler)

- Şablon sınıfı

- Yapı

- Sabit listesi

- Makro (makronun işleme sonrası görünümünü görüntüler)

- Genişletiyor

> [!NOTE]
> Bu, modelleme Project oluşturabileceğiniz UML sınıf diyagramı ile aynı değildir. Daha fazla bilgi için bkz. [UML sınıf diyagramları: başvuru](../../modeling/what-s-new-for-design-in-visual-studio.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Tür çözümleme ve görüntüleme sorunlarını giderme

### <a name="location-of-source-files"></a>Kaynak dosyalarının konumu

**Sınıf Tasarımcısı** , kaynak dosyaların konumunu izlememez. Bu nedenle, proje yapınızı değiştirir veya kaynak dosyalarını projenize taşırsanız, **Sınıf Tasarımcısı** türü (özellikle bir typedef, Taban sınıfları veya ilişkilendirme türleri kaynak türü) kaybedebilir. **Sınıf Tasarımcısı bu tür görüntülenemiyor** gibi bir hata alabilirsiniz. Bunu yaparsanız, yeniden görüntülemek için değiştirilen veya yeniden konumlandırılan kaynak kodu yeniden sınıf diyagramına sürükleyin.

### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans sorunları

C++ projeleri için, kaynak dosyadaki bir değişikliğin sınıf diyagramında görünmesi 30 ila 60 saniye sürebilir. Bu gecikme **, seçimde hiçbir tür bulunamamış** bir hata **Sınıf Tasarımcısı** oluşturulmasına da neden olabilir. Bunun gibi bir hata alırsanız hata iletisindeki **iptal** ' e tıklayın ve kod öğesinin **sınıf görünümü** görünmesini bekleyin. Bunu yaptıktan sonra, **Sınıf Tasarımcısı** türü görüntüleyebilmelidir.

Bir sınıf diyagramı kodda yaptığınız değişikliklerle güncelleştirmezse, diyagramı kapatıp yeniden açmanız gerekebilir.

### <a name="type-resolution-issues"></a>Tür çözümleme sorunları

**Sınıf Tasarımcısı** , aşağıdaki nedenlerden dolayı türleri çözemeyebilir:

- Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede yer alır. Bu hatayı düzeltmek için, türü içeren proje veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../managing-references-in-a-project.md).

- Tür doğru kapsamda olmadığından **Sınıf Tasarımcısı** bulamıyor. Kodun bir `using` , veya bildiriminin eksik olmadığından emin olun `imports` `#include` . Ayrıca, türü (veya ilgili bir tür), başlangıçta bulunduğu ad alanından taşıdığınızdan emin olun.

- Tür yok (veya açıklama alındı). Bu hatayı düzeltmek için, türü açıklama veya silme yaptığınızdan emin olun.

- Tür, bir #import yönergesi tarafından başvurulan bir kitaplıkta bulunur. Olası bir geçici çözüm, oluşturulan kodu (. tlh dosyası) üst bilgi dosyasına bir #include yönergesine el ile eklemektir.

- **Sınıf Tasarımcısı** girdiğiniz türü desteklediğinden emin olun. [C++ kod öğelerine yönelik sınırlamalara](#limitations-for-c-code-elements)bakın.

**' \<element> ' Sınıf diyagramında bir veya daha fazla şekil için** bir tür çözümleme sorunu için görmeniz muhtemel olan hata, kod bulunamadı. Bu hata iletisi, kodunuzun hatalı olduğunu göstermez. Yalnızca bu sınıf tasarımcısının kodunuzun görüntülenemiyor olduğunu gösterir. Aşağıdaki ölçüleri deneyin:

- Türün var olduğundan emin olun. Kaynak kodu istemeyerek dışarı veya silmediğinden emin olun.

- Türü çözmeyi deneyin. Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede olabilir. Bu hatayı düzeltmek için, türü içeren proje veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../managing-references-in-a-project.md).

- Sınıf Tasarımcısı bulmak için türün doğru kapsamda olduğundan emin olun. Kodda bir `using` , veya ifadesinin eksik olmadığından emin olun `imports` `#include` . Ayrıca, türü (veya ilgili bir tür), başlangıçta bulunduğu ad alanından taşıdığınızdan emin olun.

### <a name="troubleshoot-other-error-messages"></a>Diğer hata iletileriyle ilgili sorunları giderme

Microsoft Developer Network (MSDN) ortak forumlarında sorun giderme hatalarıyla ve uyarılarla ilgili yardım bulabilirsiniz. [Visual Studio Sınıf Tasarımcısı forumuna](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner)bakın.

## <a name="limitations-for-c-code-elements"></a>C++ kod öğeleri için sınırlamalar

- Bir C++ projesi yüklendiğinde, **Sınıf Tasarımcısı** işlevleri salt okunurdur. Sınıf diyagramını değiştirebilirsiniz, ancak sınıf diyagramından değişiklikleri kaynak koda geri kaydedemezsiniz.

- **Sınıf Tasarımcısı** yalnızca yerel C++ semantiğini destekler. Yönetilen koda derlenen C++ projeleri için **Sınıf Tasarımcısı** yalnızca yerel türler olan kod öğelerini görselleştirir. Bu nedenle, bir projeye sınıf diyagramı ekleyebilirsiniz, ancak **Sınıf Tasarımcısı** `IsManaged` özelliğin `true` (yani, değer türleri ve başvuru türleri) ayarlandığı öğeleri görselleştirmenize izin vermez.

- C++ projeleri için **Sınıf Tasarımcısı** yalnızca türün tanımını okur. Örneğin, bir üstbilgi (. h) dosyasında bir tür tanımladığınızı ve üyelerini bir uygulama (. cpp) dosyasında tanımladığınızı varsayalım. Uygulama (. cpp) dosyasında "Görünüm sınıf diyagramını" çağırırsanız **Sınıf Tasarımcısı** hiçbir şey görüntülemez. Başka bir örnek olarak, `#include` diğer dosyaları dahil etmek için bir ifade kullanan ancak gerçek sınıf tanımları içermeyen bir. cpp dosyasında "Görünüm sınıf diyagramını" çağırırsanız, **Sınıf Tasarımcısı** hiçbir şey göstermez.

- COM arabirimlerini ve tür kitaplıklarını tanımlayan IDL (. IDL) dosyaları, yerel C++ koduna derlenmedikleri takdirde diyagramlarda görüntülenmez.

- **Sınıf Tasarımcısı** , genel işlevleri ve değişkenleri desteklemez.

- **Sınıf Tasarımcısı** birleşimler desteklemez. Bu, ayrılan belleğin yalnızca birleşimin en büyük veri üyesi için gereken miktarı olduğu özel bir sınıf türüdür.

- **Sınıf Tasarımcısı** , ve gibi temel veri türlerini görüntülemez `int` `char` .

- **Sınıf Tasarımcısı** , projenin bu türlere doğru başvuruları yoksa, geçerli projenin dışında tanımlanan türleri görüntülemez.

- **Sınıf Tasarımcısı** , iç içe geçmiş türler ve diğer türler arasındaki ilişkileri değil, iç içe geçmiş türleri görüntüleyebilir.

- **Sınıf Tasarımcısı** void olan veya void bir türden türetilen türleri görüntüleyemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve Türleri Tasarlama ve Görüntüleme (Sınıf Tasarımcısı)](designing-and-viewing-classes-and-types.md)
- [Sınıf Tasarımcısı Hataları Hakkında Ek Bilgiler](additional-information-about-errors.md)
- [Sınıf Tasarımcısı C++ sınıfları](visual-cpp-classes.md)
- [Sınıf Tasarımcısı 'de C++ yapıları](visual-cpp-structures.md)
- [Sınıf Tasarımcısı C++ numaralandırmalar](visual-cpp-enumerations.md)
- [Sınıf Tasarımcısı 'de C++ Typedefs](visual-cpp-typedefs.md)
