---
title: Sınıf Tasarımcısı kullan
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 80668f3b999d9e022de3d22abb383f2dbd10730a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87507917"
---
# <a name="design-and-view-classes-and-types-with-class-designer"></a>Sınıf Tasarımcısı sınıfları ve türleri tasarlama ve görüntüleme

Visual Studio 'da **Sınıf Tasarımcısı** kodunuzda sınıfları ve diğer türleri tasarlayın, görselleştirin ve yeniden düzenleyin. C#, Visual Basic veya C++ projenizdeki sınıfları oluşturmak ve düzenlemek için sınıf diyagramlarını kullanın. Ayrıca, proje yapınızı daha iyi anlamak veya kodunuzu yeniden düzenlemek için sınıf diyagramlarını kullanabilirsiniz.

## <a name="what-you-can-do-with-class-diagrams"></a>Sınıf diyagramlarıyla yapabilecekleriniz

- **Tasarım**: sınıf diyagramını düzenleyerek projenizin kodunu düzenleyin. Yeni öğeler ekleyin ve istenmeyen olanları silin. Değişiklikleriniz kodda yansıtılır.

- **Görselleştirin**: projenizdeki sınıfları bir diyagram üzerinde görüntüleyerek projenizin yapısını anlayın. En çok önem verdiğiniz proje ayrıntılarına odaklanabilmeniz için diyagramınızı özelleştirin. Daha sonra tanıtım veya belgeler için kullanmak üzere diyagramınızı kaydedin.

- Yeniden **Düzenle**: yöntemleri geçersiz kılın, tanımlayıcıları yeniden düzenleyin, parametreleri yeniden düzenleyin ve arabirimleri ve soyut sınıfları uygulayın.

## <a name="view-types-and-relationships"></a>Türleri ve ilişkileri görüntüleme

Sınıf diyagramlarında türlerin ayrıntıları, örneğin bağlı üyeleri ve aralarındaki ilişkiler gösterilmektedir. Bu varlıkların görselleştirmesi kodun içinde dinamik bir görünümdir. Bu, tasarımcıda türleri düzenleyebileceğiniz ve daha sonra düzenlerinizin varlığın kaynak kodunda yansıtıldığı anlamına gelir. Benzer şekilde, sınıf diyagramı kod dosyalarında yaptığınız değişikliklerle eşitlenmiş olarak tutulur.

> [!NOTE]
> Projeniz bir sınıf diyagramı içeriyorsa ve projeniz başka bir projede bulunan bir türe başvuruyorsa, bu tür için proje oluşturuluncaya kadar sınıf diyagramı başvurulan türü göstermez. Benzer şekilde, diyagram, söz konusu varlık için projeyi yeniden oluşturulana kadar dış varlığın kodundaki değişiklikleri görüntülemez.

## <a name="class-diagram-workflow"></a>Sınıf diyagramı iş akışı

Sınıf diyagramları, projelerin sınıf yapısını anlamanıza yardımcı olabilir. Bu projeler diğer geliştiriciler tarafından oluşturulmuş olabilir veya sizin oluşturduğunuz bir projede bir yenileyici olması yeterlidir. Proje bilgilerini başkalarıyla özelleştirmek, paylaşmak ve sunmak için sınıf diyagramlarını kullanabilirsiniz.

Proje bilgilerini sunarken ilk adım, göstermek istediğiniz şeyi görüntüleyen bir sınıf diyagramı oluşturmaktır. Daha fazla bilgi için bkz. [sınıf diyagramı ekleme](how-to-add-class-diagrams-to-projects.md). Projenin ayrı bir görünümünü, projenin türlerin seçili bir alt kümesini veya türlerin üyelerinin seçili bir alt kümesini görüntülemek için kullanılabilecek bir proje için birden çok sınıf diyagramı oluşturabilirsiniz.

Her bir sınıf diyagramının ne gösterdiğini tanımlamaya ek olarak, bilgilerin sunulma şeklini de değiştirebilirsiniz; daha fazla bilgi için bkz. [nasıl yapılır: sınıf diyagramlarını özelleştirme](how-to-customize-class-diagrams.md).

Bir veya daha fazla sınıf diyagramına ince ayar yaptıktan sonra, bunları Microsoft Office belgelerine kopyalayabilir ve yazdırabilir ya da resim dosyası olarak dışarı aktarabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: sınıf diyagramı öğelerini Microsoft Office bir belgeye kopyalama](how-to-copy-class-diagram-elements-to-a-microsoft-office-document.md), [nasıl yapılır: sınıf diyagramlarını yazdırma](how-to-print-class-diagrams.md) ve [nasıl yapılır: sınıf diyagramlarını görüntü olarak dışarı aktarma](how-to-export-class-diagrams-as-images.md).

> [!NOTE]
> Sınıf Tasarımcısı, kaynak dosyalarınızın konumunu izlememez, bu yüzden proje yapınızı değiştirmek veya projede kaynak dosyaları taşımak Sınıf Tasarımcısı, özellikle bir typedef, taban sınıf veya ilişki türlerinin kaynak türü olan türün izini kaybetmesine neden olabilir. **Sınıf Tasarımcısı, bu tür görüntülenemiyor**gibi bir hata alabilirsiniz. Bunu yaparsanız, yeniden görüntülemek için değiştirilen veya yeniden konumlandırılan kaynak kodu yeniden sınıf diyagramına sürükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod düzenleyicisinin özellikleri](../writing-code-in-the-code-and-text-editor.md)
- [Çözümlerinizdeki bağımlılıkları eşleme](../../modeling/map-dependencies-across-your-solutions.md)
