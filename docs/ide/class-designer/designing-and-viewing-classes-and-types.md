---
title: Sınıf Tasarımcısı
description: Kod içinde sınıf tasarlamayı, görselleştirmeyi ve kodundaki diğer türleri yeniden düzenlemeyi ve Sınıf Tasarımcısı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
- vs.classdesigner.enum
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85921343ac52c066735d607ce32635e953cf2e6a
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254789"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Sınıf Tasarımcısı ile sınıfları ve türleri tasarlama ve Sınıf Tasarımcısı

Kod kodundaki sınıflarla sınıfları ve diğer türleri tasarla, görselleştir **ve Sınıf Tasarımcısı** ve Visual Studio. C#, Visual Basic veya C++ projesinde sınıflar oluşturmak ve düzenlemek için sınıf diyagramlarını kullanın. Proje yapınızı daha iyi anlamak veya kodunuzu yeniden düzenlemek için sınıf diyagramlarını da kullanabilirsiniz.

>[!NOTE]
>Sınıf Tasarımcısı .NET Core projelerinde kullanılamaz.

## <a name="what-you-can-do-with-class-diagrams"></a>Sınıf diyagramları ile neler yapabilirsiniz?

- **Tasarım:** Sınıf diyagramını düzenleyerek projenizin kodunu düzenleyin. Yeni öğeler ekleyin ve istenmeyen öğeleri silin. Değişiklikleriniz koda yansıtıldı.

- **Görselleştirin:** Projenizin yapısını anlamak için projenizin sınıflarını diyagramda görüntüebilirsiniz. Diyagramınızı özelleştirin, böylece en çok önemle önem istediğiniz proje ayrıntılarına odaklanabilirsiniz. Daha sonra gösterim veya belgeler için kullanmak üzere diyagramınızı kaydedin.

- **Yeniden düzenleme:** Yöntemleri geçersiz kılın, tanımlayıcıları yeniden adlandır, parametreleri yeniden düzenleme ve arabirimleri ve soyut sınıfları uygulama.

## <a name="view-types-and-relationships"></a>Türleri ve ilişkileri görüntüleme

Sınıf diyagramları türlerin ayrıntılarını ( örneğin, onların kurucu üyelerini ve aralarındaki ilişkileri) gösterir. Bu varlıkların görselleştirmesi, koda dinamik bir görünüm sağlar. Bu, tasarımcıda türleri düzenleyemez ve sonra düzenlemelerinizi varlığın kaynak koduna yansıtıldı olarak göreceğiniz anlamına gelir. Benzer şekilde, sınıf diyagramı kod dosyalarında yaptığınız değişikliklerle eşit olarak tutulur.

> [!NOTE]
> Projeniz bir sınıf diyagramı içeriyorsa ve projeniz başka bir projede bulunan bir türe başvurursa, sınıf diyagramı o tür için projeyi derlemeden başvurulan türü göstermez. Benzer şekilde, siz bu varlık için projeyi yeniden oluşturmadan diyagramda dış varlığın kodunda yapılan değişiklikler görüntülenmez.

## <a name="class-diagram-workflow"></a>Sınıf diyagramı iş akışı

Sınıf diyagramları, projelerin sınıf yapısını anlamanıza yardımcı olabilir. Bu projeler diğer geliştiriciler tarafından oluşturulmuş olabilir veya yalnızca kendi oluşturduğunuz bir projeyle ilgili bir yenilemeye ihtiyacınız olabilir. Proje bilgilerini başkalarını özelleştirmek, paylaşmak ve sunmak için sınıf diyagramlarını kullanabilirsiniz.

Proje bilgilerini göstermenin ilk adımı, göstermek istediğiniz öğeleri görüntüleyen bir sınıf diyagramı oluşturmaktır. Daha fazla bilgi için [bkz. Sınıf diyagramı ekleme.](how-to-add-class-diagrams-to-projects.md) Projenin ayrı bir görünümünü, proje türlerinin belirli bir alt kümesini veya türlerin üyelerinin seçilen bir alt kümesini görüntülemek için kullanılmaktadır bir proje için birden çok sınıf diyagramı oluşturabilirsiniz.

Her sınıf diyagramının ne göster gösteresini tanımlamaya ek olarak, bilgilerin nasıl sunlsa da değişmesini de sebilirsiniz; Daha fazla bilgi için [bkz. Nasıl 2. Sınıf diyagramlarını özelleştirme.](how-to-customize-class-diagrams.md)

Bir veya daha fazla sınıf diyagramında ince ayarlamalar yaptıktan sonra, bunları Microsoft Office belgelerine kopyalayıp yazdırabilirsiniz veya görüntü dosyası olarak dışarı aktarabilirsiniz. Daha fazla bilgi için bkz. Nasıl [kullanılır:](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md)Sınıf diyagramı öğelerini bir Microsoft Office belgesine kopyalama, [Nasıl kullanılır:](how-to-print-class-diagrams.md) Sınıf diyagramlarını yazdırma ve Nasıl kullanılır: Sınıf [diyagramlarını görüntü olarak dışarı aktarma.](how-to-export-class-diagrams-as-images.md)

> [!NOTE]
> Sınıf Tasarımcısı kaynak dosyalarınızın konumunu izlemez, bu nedenle proje yapınızı değiştirmek veya projede kaynak dosyaları taşımak, Sınıf Tasarımcısı'nin türü, özellikle de typedef, temel sınıflar veya ilişkilendirme türlerinin kaynak türünü kaybetmelerine neden olabilir. Bu tür bir Sınıf Tasarımcısı **gibi bir hata alabilirsiniz.** Bunu yaparsanız, değiştirilmiş veya yeniden konumlu kaynak kodunu yeniden oynatmak için yeniden sınıf diyagramına sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../writing-code-in-the-code-and-text-editor.md)
- [Çözümlerinizdeki bağımlılıkları eşleme](../../modeling/map-dependencies-across-your-solutions.md)
