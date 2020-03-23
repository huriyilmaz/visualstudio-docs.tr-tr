---
title: C++ Kodu (Sınıf Tasarımcısı) ile çalışma
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
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 54087a719b0079ba32ff08ff1e08ad01f5e64ed0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596755"
---
# <a name="work-with-c-code-in-class-designer"></a>Sınıf Tasarımcısı'nda C++ koduyla çalışma

**Sınıf Tasarımcısı,** projenizdeki kod öğelerinin görsel bir gösterimini sağlayan *sınıf diyagramı* adı verilen görsel bir tasarım yüzeyi görüntüler. Bir projedeki sınıfları ve diğer türleri tasarlamak ve görselleştirmek için sınıf diyagramlarını kullanabilirsiniz.

**Sınıf Tasarımcısı** aşağıdaki C++ kod öğelerini destekler:

- Sınıf (birden çok devralma ilişkisi olması dışında yönetilen sınıf şekline benzer)

- Anonim sınıf (Sınıf Görünümü'nün oluşturulan adını anonim tür için görüntüler)

- Şablon sınıfı

- Yapı

- Sabit Listesi

- Makro (makronun işlenme sonrası görünümünü görüntüler)

- Typedef

> [!NOTE]
> Bu, modelleme Projesi'nde oluşturabileceğiniz UML sınıf diyagramıile aynı değildir. Daha fazla bilgi için [UML Sınıf Diyagramları: Başvuru.](../../modeling/what-s-new-for-design-in-visual-studio.md)

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Sorun giderme türü çözümü ve görüntü sorunları

### <a name="location-of-source-files"></a>Kaynak dosyaların konumu

**Sınıf Tasarımcısı** kaynak dosyaların konumunu izlemez. Bu nedenle, proje yapınızı değiştirir veya projenizde kaynak dosyaları taşırsanız, **Sınıf Tasarımcısı** türü (özellikle bir typedef, temel sınıflar veya ilişkilendirme türleri kaynak türü) izleme kaybedebilir. **Sınıf Tasarımcısı bu tür görüntüleyemiyor**gibi bir hata alabilirsiniz. Bunu yaparsanız, değiştirilen veya değiştirilen kaynak kodu yeniden görüntülemek için sınıf diyagramına sürükleyin.

### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans sorunları

C++ projeleri için kaynak dosyadaki bir değişikliğin sınıf diyagramında görünmesi 30 ila 60 saniye sürebilir. Bu gecikme, **Sınıf Tasarımcısı'nın** **seçimde no türü bulunmayan**hatayı atamasını da gerek. Bunun gibi bir hata alırsanız, hata iletisinde **İptal'i** tıklatın ve kod öğesinin **Sınıf Görünümü'nde**görünmesini bekleyin. Bunu yaptıktan sonra, **Sınıf Tasarımcısı** türünü görüntüleyebilir.

Bir sınıf diyagramı kodda yaptığınız değişikliklerle güncelleştirmezse, diyagramı kapatıp yeniden açmanız gerekebilir.

### <a name="type-resolution-issues"></a>Tür çözümleme sorunları

**Sınıf Tasarımcısı** aşağıdaki nedenlerle türleri çözümlenemeyebilir:

- Tür, sınıf diyagramını içeren projeden başvurulmayan bir proje veya derlemededir. Bu hatayı düzeltmek için, türü içeren projeye veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için [bkz.](../managing-references-in-a-project.md)

- Tür doğru kapsamda değildir, bu nedenle **Sınıf Tasarımcısı** onu bulamıyor. Kodun bir `using`, veya `imports` `#include` deyimi eksik olmadığından emin olun. Ayrıca, türü (veya ilgili bir türü) ilk bulunduğu ad alanından çıkarmadığınızdan da emin olun.

- Türü yok (veya yorumlandı). Bu hatayı düzeltmek için, yazının dışına çıkmadığınızdan veya türünü silmediğinizden emin olun.

- Tür, bir #import yönergesi tarafından başvurulan bir kitaplıkta bulunur. Olası bir geçici çözüm, oluşturulan kodu (.tlh dosyası) üstbilgi dosyasına #include bir yönergeye el ile eklemektir.

- Sınıf **Tasarımcısı'nın** girdiğiniz türü desteklediğinden emin olun. [Bkz. C++ Kod Öğeleri için Sınırlamalar.](#limitations-for-c-code-elements)

Bir tür çözümlemesi sorunu için görme olasılığınız en yüksek olan **hata, Kod'un sınıf diyagramındaki bir veya daha fazla şekil için bulunamamasıdır '\<öğesi>'**. Bu hata iletisi mutlaka kodunuzu hata olduğunu göstermez. Yalnızca sınıf tasarımcısının kodunuzu görüntüleyemediğini gösterir. Aşağıdaki önlemleri deneyin:

- Türün var olduğundan emin olun. Kaynak kodu istemeden açıklamadığınızdan veya silmediğinizden emin olun.

- Türünü çözmeye çalışın. Tür, sınıf diyagramını içeren projeden başvurulmayan bir proje veya derlemede olabilir. Bu hatayı düzeltmek için, türü içeren projeye veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için [bkz.](../managing-references-in-a-project.md)

- Sınıf Tasarımcısı'nın bulabilmesini sağlamak için türün doğru kapsamda olduğundan emin olun. Kodun bir `using`, veya `imports` `#include` deyimi eksik olmadığından emin olun. Ayrıca, türü (veya ilgili bir türü) ilk bulunduğu ad alanından çıkarmadığınızdan da emin olun.

### <a name="troubleshoot-other-error-messages"></a>Diğer hata iletilerini sorun giderme

Microsoft Geliştirici Ağı (MSDN) genel forumlarında sorun giderme hataları ve uyarıları yla ilgili yardım bulabilirsiniz. Visual [Studio Sınıf Tasarımcısı Forumu'na](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner)bakın.

## <a name="limitations-for-c-code-elements"></a>C++ kod öğeleri için sınırlamalar

- Bir C++ projesi yüklendiğinde, **Sınıf Tasarımcısı** salt okunur şekilde çalışır. Sınıf diyagramını değiştirebilirsiniz, ancak sınıf diyagramından kaynak koduna değişiklikleri kaydedemezsiniz.

- **Sınıf Tasarımcısı** yalnızca yerel C++ semantikini destekler. Yönetilen kodda derlenen C++ projeleri için **Sınıf Tasarımcısı** yalnızca yerel türlerdeki kod öğelerini görselleştirir. Bu nedenle, bir projeye sınıf diyagramı ekleyebilirsiniz, ancak **Sınıf Tasarımcısı** özelliğin `IsManaged` ayarlandığı öğeleri `true` (diğer bir deyişle değer türleri ve başvuru türleri) görselleştirmenize izin vermez.

- C++ projeleri için **Sınıf Tasarımcısı** yalnızca türün tanımını okur. Örneğin, üstbilgi (.h) dosyasında bir tür tanımladığınızı ve bir uygulama (.cpp) dosyasında üyelerini tanımladığınızı varsayalım. Uygulama (.cpp) dosyasında "Sınıf Diyagramını Görüntüle" dosyasını çağırırsanız, **Sınıf Tasarımcısı** hiçbir şey görüntülemez. Başka bir örnek olarak, diğer dosyaları eklemek için bir deyim `#include` kullanan ancak gerçek sınıf tanımları içermeyen bir .cpp dosyasında "Sınıf Diyagramı Görüntüle"yi çağırırsanız, **Sınıf Tasarımcısı** yine hiçbir şey göstermez.

- COM arabirimlerini ve tür kitaplıklarını tanımlayan IDL (.idl) dosyaları, yerel C++ koduna derlenmedikçe diyagramlarda görüntülenmez.

- **Sınıf Tasarımcısı** genel işlevleri ve değişkenleri desteklemez.

- **Sınıf Tasarımcısı** sendikaları desteklemez. Bu, ayrılan belleğin yalnızca birliğin en büyük veri üyesi için gereken miktar olduğu özel bir sınıf türüdür.

- **Sınıf Tasarımcısı** gibi `int` temel veri türlerini görüntülemez. `char`

- **Sınıf Tasarımcısı,** projede bu türlere doğru başvurular yoksa, geçerli proje dışında tanımlanan türleri görüntülemez.

- **Sınıf Tasarımcısı** iç içe geçen türleri görüntüleyebilir, ancak iç içe geçen türlerle diğer türler arasındaki ilişkileri görüntüleyebilir.

- **Sınıf Tasarımcısı** geçersiz olan veya geçersiz bir türden türemiş türleri görüntüleyemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve Türleri Tasarlama ve Görüntüleme (Sınıf Tasarımcısı)](designing-and-viewing-classes-and-types.md)
- [Sınıf Tasarımcısı Hataları Hakkında Ek Bilgiler](additional-information-about-errors.md)
- [Sınıf Tasarımcıc++ Sınıfları](visual-cpp-classes.md)
- [Sınıf Tasarımcıc++ Yapıları](visual-cpp-structures.md)
- [Sınıf Tasarımcıc++ Eumerations](visual-cpp-enumerations.md)
- [Sınıf Tasarımcısıc++ Typedefs](visual-cpp-typedefs.md)
