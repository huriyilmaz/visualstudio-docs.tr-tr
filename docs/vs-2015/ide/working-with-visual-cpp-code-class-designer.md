---
title: Visual C++ kodla çalışma (Sınıf Tasarımcısı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 020535ac73c48be74e56100c7b6f9c49b69e50dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851310"
---
# <a name="working-with-visual-c-code-class-designer"></a>Visual C++ Kodu ile Çalışma (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı, projenizdeki kod öğelerinin görsel gösterimini sağlayan *sınıf diyagramı* adlı bir görsel tasarım yüzeyi görüntüler. Bir projedeki sınıfları ve diğer türleri tasarlamak ve görselleştirmek için sınıf diyagramlarını kullanabilirsiniz.

 Sınıf Tasarımcısı aşağıdaki C++ kod öğelerini destekler:

- Sınıf (birden fazla devralma ilişkisine sahip olması dışında, yönetilen bir sınıf şekline benzer)

- Anonim Sınıf (Sınıf Görünümü, anonim tür için üretilen adı görüntüler)

- Şablon sınıfı

- Yapı

- Sabit listesi

- Makro (makronun işleme sonrası görünümünü görüntüler)

- Genişletiyor

> [!NOTE]
> Bu, modelleme projesinde oluşturabileceğiniz UML sınıf diyagramı ile aynı değildir. Daha fazla bilgi için bkz. [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md).

## <a name="troubleshooting-type-resolution-and-display-issues"></a>Tür çözümleme ve görüntüleme sorunlarını giderme

### <a name="location-of-source-files"></a>Kaynak dosyalarının konumu
 Sınıf Tasarımcısı, kaynak dosyaların konumunu izlememez. Bu nedenle, proje yapınızı değiştirir veya kaynak dosyalarını projenize taşırsanız, Sınıf Tasarımcısı türü (özellikle bir typedef, Taban sınıfları veya ilişkilendirme türleri kaynak türü) kaybedebilir. **Sınıf Tasarımcısı bu tür görüntülenemiyor**gibi bir hata alabilirsiniz. Bunu yaparsanız, yeniden görüntülemek için değiştirilen veya yeniden konumlandırılan kaynak kodu yeniden sınıf diyagramına sürükleyin.

### <a name="update-and-performance-issues"></a>Güncelleştirme ve performans sorunları
 Visual C++ projeler için, kaynak dosyadaki bir değişikliğin sınıf diyagramında görünmesi 30 ila 60 saniye sürebilir. Bu gecikme **, seçimde hiçbir tür bulunamamış**bir hata Sınıf Tasarımcısı oluşturulmasına da neden olabilir. Bunun gibi bir hata alırsanız hata iletisindeki **iptal** ' e tıklayın ve kod öğesinin sınıf görünümü görünmesini bekleyin. Bunu yaptıktan sonra, Sınıf Tasarımcısı türü görüntüleyebilmelidir.

 Bir sınıf diyagramı kodda yaptığınız değişikliklerle güncelleştirmezse, diyagramı kapatıp yeniden açmanız gerekebilir.

### <a name="type-resolution-issues"></a>Tür çözümleme sorunları
 Sınıf Tasarımcısı, aşağıdaki nedenlerden dolayı türleri çözemeyebilir:

- Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede yer alır. Bu hatayı düzeltmek için, türü içeren proje veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Tür doğru kapsamda olmadığından Sınıf Tasarımcısı bulamıyor. Kodun bir `using` , veya bildiriminin eksik olmadığından emin olun `imports` `#include` . Ayrıca, türü (veya ilgili bir tür), başlangıçta bulunduğu ad alanından taşıdığınızdan emin olun.

- Tür yok (veya açıklama alındı). Bu hatayı düzeltmek için, türü açıklama veya silme yaptığınızdan emin olun.

- Tür, bir #import yönergesi tarafından başvurulan bir kitaplıkta bulunur. Olası bir geçici çözüm, oluşturulan kodu (. tlh dosyası) üst bilgi dosyasına bir #include yönergesine el ile eklemektir.

  **' \<element> ' Sınıf diyagramında bir veya daha fazla şekil için**bir tür çözümleme sorunu için görmeniz muhtemel olan hata, kod bulunamadı. Bu hata iletisi, kodunuzun hatalı olduğunu göstermez. Yalnızca bu sınıf tasarımcısının kodunuzun görüntülenemiyor olduğunu gösterir. Aşağıdaki ölçüleri deneyin.

- Türün var olduğundan emin olun. Kaynak kodu istemeyerek dışarı veya silmediğinden emin olun.

- Sınıf Tasarımcısı girdiğiniz türü desteklediğinden emin olun. [C++ kod öğelerine yönelik sınırlamalara](#limitations)bakın.

- Türü çözmeyi deneyin. Tür, sınıf diyagramını içeren projeden başvurulmayan bir projede veya derlemede olabilir. Bu hatayı düzeltmek için, türü içeren proje veya derlemeye bir başvuru ekleyin. Daha fazla bilgi için bkz. [nib nasıl yapılır: Başvuru Ekle Iletişim kutusunu kullanarak başvuru ekleme veya kaldırma](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

- Sınıf Tasarımcısı bulmak için türün doğru kapsamda olduğundan emin olun. Kodda bir `using` , veya ifadesinin eksik olmadığından emin olun `imports` `#include` . Ayrıca, türü (veya ilgili bir tür), başlangıçta bulunduğu ad alanından taşıdığınızdan emin olun.

### <a name="troubleshooting-other-error-messages"></a>Diğer hata Iletileri sorunlarını giderme
 Microsoft Developer Network (MSDN) ortak forumlarında sorun giderme hatalarıyla ve uyarılarla ilgili yardım bulabilirsiniz. Bkz. [Visual Studio Sınıf Tasarımcısı Forumu](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1).

## <a name="limitations-for-c-code-elements"></a><a name="limitations"></a> C++ kod öğeleri için sınırlamalar

- Visual C++ bir proje yüklendiğinde, Sınıf Tasarımcısı işlevleri salt okunurdur. Sınıf diyagramını değiştirebilirsiniz, ancak sınıf diyagramından değişiklikleri kaynak koda geri kaydedemezsiniz.

- Sınıf Tasarımcısı yalnızca yerel C++ semantiğini destekler. Yönetilen koda derlenen Visual C++ projeleri için, Sınıf Tasarımcısı yalnızca yerel türler olan kod öğelerini görselleştirir. Bu nedenle, bir projeye sınıf diyagramı ekleyebilirsiniz, ancak Sınıf Tasarımcısı `IsManaged` özelliğin `true` (yani, değer türleri ve başvuru türleri) ayarlandığı öğeleri görselleştirmenize izin vermez.

- Visual C++ projeleri için Sınıf Tasarımcısı yalnızca türün tanımını okur. Örneğin, bir üstbilgi (. h) dosyasında bir tür tanımladığınızı ve üyelerini bir uygulama (. cpp) dosyasında tanımladığınızı varsayalım. Uygulama (. cpp) dosyasında "Görünüm sınıf diyagramını" çağırırsanız Sınıf Tasarımcısı hiçbir şey görüntülemez. Başka bir örnek olarak, `#include` diğer dosyaları dahil etmek için bir ifade kullanan ancak gerçek sınıf tanımları içermeyen bir. cpp dosyasında "Görünüm sınıf diyagramını" çağırırsanız, sınıf Tasarımcısı hiçbir şey göstermez.

- COM arabirimlerini ve tür kitaplıklarını tanımlayan IDL (. IDL) dosyaları, yerel C++ koduna derlenmedikleri takdirde diyagramlarda görüntülenmez.

- Sınıf Tasarımcısı, genel işlevleri ve değişkenleri desteklemez.

- Sınıf Tasarımcısı birleşimler desteklemez. Bu, ayrılan belleğin yalnızca birleşimin en büyük veri üyesi için gereken miktarı olduğu özel bir sınıf türüdür.

- Sınıf Tasarımcısı, ve gibi temel veri türlerini görüntülemez `int` `char` .

- Sınıf Tasarımcısı, projenin bu türlere doğru başvuruları yoksa, geçerli projenin dışında tanımlanan türleri görüntülemez.

- Sınıf Tasarımcısı, iç içe geçmiş türler ve diğer türler arasındaki ilişkileri değil, iç içe geçmiş türleri görüntüleyebilir.

- Sınıf Tasarımcısı void olan veya void bir türden türetilen türleri görüntüleyemez.

## <a name="see-also"></a>Ayrıca Bkz.
 Sınıflar ve türler ( [Sınıf Tasarımcısı) ile birlikte çalışan](../ide/working-with-classes-and-other-types-class-designer.md) sınıflar ve [türleri tasarlama ve görüntüleme](../ide/designing-and-viewing-classes-and-types.md) ( [Sınıf Tasarımcısı) sınıf diyagramları Ile çalışma](../ide/working-with-class-diagrams-class-designer.md) () sınıf [ve türleri tasarlama (sınıf Tasarımcısı](../ide/designing-classes-and-types-class-designer.md) [Sınıf Tasarımcısı](../ide/additional-information-about-class-designer-errors.md) ) [Visual C++ sınıf Tasarımcısı](../ide/visual-cpp-typedefs-in-class-designer.md) Numaralandırmaların [Visual C++ sınıf Tasarımcısı](../ide/visual-cpp-structures-in-class-designer.md) [numaralandırmalar](../ide/visual-cpp-enumerations-in-class-designer.md) [Visual C++ sınıf Tasarımcısı](../ide/visual-cpp-classes-in-class-designer.md)
