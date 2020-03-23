---
title: Sınıf Tasarımcısı nı Kullanma
ms.date: 05/08/2018
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.diagram
helpviewer_keywords:
- Class Designer [Visual Studio]
- Class Designer, about Class Designer
- types [Visual Studio], viewing
- classes [Visual Studio], viewing
- class designer
ms.assetid: 40ed2c9d-0ce0-4b95-ad78-5dec2065ccea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c65be2b5afe91f9ee20a5eecde57d790a0cbcb2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590403"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Sınıf Tasarımcısı ile sınıfları ve türleri tasarlama ve görüntüleme

Visual Studio'da **Sınıf Tasarımcısı** ile kodunuzda sınıfları ve diğer türleri tasarlayın, görselleştirin ve yeniden kedin. C#, Visual Basic veya C++ projenizde sınıflar oluşturmak ve bunları diziniçin sınıf diyagramlarını kullanın. Proje yapınızı daha iyi anlamak veya kodunuzu yeniden düzenlemek için sınıf diyagramlarını da kullanabilirsiniz.

## <a name="what-you-can-do-with-class-diagrams"></a>Sınıf diyagramları ile yapabilecekler

- **Tasarım**: Sınıf diyagramını düzenleyerek projenizin kodunu düzenleyin. Yeni öğeler ekleyin ve istenmeyen öğeleri silin. Değişiklikleriniz koda yansıtılır.

- **Visualize**: Projenizdeki sınıfları diyagramda görüntüleyerek projenizin yapısını anlayın. Diyagramınızı en çok önem verdiğiniz proje ayrıntılarına odaklanabilmeniz için özelleştirin. Diyagramınızı daha sonra gösteri veya belgeleme için kullanmak üzere kaydedin.

- **Refactor**: Geçersiz kılma yöntemleri, yeniden adlandırma tanımlayıcıları, refactor parametreleri ve arayüzleri ve soyut sınıflar uygulayın.

## <a name="view-types-and-relationships"></a>Türleri ve ilişkileri görüntüleme

Sınıf diyagramları, örneğin, kurucu üyelerinin ve aralarındaki ilişkilerin ayrıntılarını gösterir. Bu varlıkların görselleştirilmesi koda dinamik bir görünümdür. Bu, tasarımcıdaki türleri ve ardından edindiğiniz denetimlerinizin varlığın kaynak koduna yansıtTığını görebileceğiniz anlamına gelir. Benzer şekilde, sınıf diyagramı kod dosyalarında yaptığınız değişikliklerle eşit tutulur.

> [!NOTE]
> Projeniz bir sınıf diyagramı içeriyorsa ve projeniz başka bir projede bulunan bir türe başvuruyorsa, bu tür için proje oluşturana kadar sınıf diyagramı başvurulan türü göstermez. Aynı şekilde, diyagram, siz bu varlık için projeyi yeniden yapılandırana kadar dış varlığın kodundaki değişiklikleri görüntülemez.

## <a name="class-diagram-workflow"></a>Sınıf diyagramı iş akışı

Sınıf diyagramları, projelerin sınıf yapısını anlamanıza yardımcı olabilir. Bu projeler diğer geliştiriciler tarafından oluşturulmuş olabilir veya kendi oluşturduğunuz bir projede yenileyiciye ihtiyacınız olabilir. Proje bilgilerini özelleştirmek, paylaşmak ve başkalarıyla sunmak için sınıf diyagramlarını kullanabilirsiniz.

Proje bilgilerini sunmanın ilk adımı, göstermek istediğiniz şeyi görüntüleyen bir sınıf diyagramı oluşturmaktır. Daha fazla bilgi için bkz. [sınıf diyagramı ekle.](how-to-add-class-diagrams-to-projects.md) Projenin farklı bir görünümünü, proje türlerinin seçilmiş bir alt kümesini veya türlerin üyelerinin seçilen bir alt kümesini görüntülemek için kullanılabilecek bir proje için birden çok sınıf diyagramı oluşturabilirsiniz.

Her sınıf diyagramında ne göstereceğini tanımlamaya ek olarak, bilgilerin sunulma biçimini de değiştirebilirsiniz; daha fazla bilgi için [bkz: Sınıf diyagramlarını özelleştirin.](how-to-customize-class-diagrams.md)

Bir veya daha fazla sınıf diyagramında ince ayar yaptıktan sonra, bunları Microsoft Office belgelerine kopyalayabilir ve yazdırabilir veya resim dosyaları olarak dışa aktarabilirsiniz. Daha fazla bilgi için [bkz: Sınıf diyagramı öğelerini Microsoft Office belgesine kopyala](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [Nasıl kullanılır: Sınıf diyagramlarını yazdırma](how-to-print-class-diagrams.md) ve [nasıl yazdırılır: Sınıf diyagramlarını resim olarak dışa](how-to-export-class-diagrams-as-images.md)aktarma.

> [!NOTE]
> Sınıf Tasarımcısı kaynak dosyalarınızın konumunu izlemez, bu nedenle proje yapınızı değiştirmek veya projedeki kaynak dosyalarınızı taşımak Sınıf Tasarımcısı'nın özellikle bir türdef, temel sınıflar veya ilişkilendirme türlerinin kaynak türünü kaybetmesine neden olabilir. **Sınıf Tasarımcısı'nın bu türü görüntüleyememesi**gibi bir hata alabilirsiniz. Bunu yaparsanız, değiştirilen veya değiştirilen kaynak kodu yeniden görüntülemek için sınıf diyagramına sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../writing-code-in-the-code-and-text-editor.md)
- [Çözümlerinizdeki bağımlılıkları eşleme](../../modeling/map-dependencies-across-your-solutions.md)
