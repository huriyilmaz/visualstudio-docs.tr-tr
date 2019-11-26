---
title: Uygulamanız için modeller oluşturun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9f20629c39bc37ca20550c3b88d8ecb2aca470f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300248"
---
# <a name="create-models-for-your-app"></a>Uygulamanız için model oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelleme diyagramları, kodunuz ve yazılım sisteminizin desteklemesi gereken kullanıcı gereksinimleri hakkındaki fikirleri anlamanıza, açıklığa kavuşturmanıza ve iletmeye yardımcı olur. Örneğin, Kullanıcı gereksinimlerini anlatmak ve iletmek için Birleşik Modelleme Dili (UML) kullanım örneği, etkinlik, sınıf ve sıra diyagramlarını kullanabilirsiniz. Sisteminizin işlevselliğini anlatmak ve iletmek için UML bileşeni, sınıf, etkinlik ve sıra diyagramlarını kullanabilirsiniz.

 Bkz. [Channel 9 videosu: modelleme aracılığıyla mimariyi geliştirme](https://go.microsoft.com/fwlink/?LinkID=252078).

 Bu sürümde aşağıdaki UML diyagramlarını oluşturabilirsiniz:

|**Çizimindeki**|**Gösterilir**|
|-----------------|---------------|
|[UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)|Bir iş işlemindeki eylemler ve katılımcılar arasındaki iş akışı|
|[UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)|Sistemin bileşenleri, arabirimleri, bağlantı noktaları ve ilişkileri|
|[UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)|Sistemi ve bunların ilişkilerini depolamak ve veri alışverişi yapmak için kullanılan türler|
|[UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)|Nesneler, bileşenler, sistemler veya aktörler arasındaki etkileşim dizileri|
|[UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)|Bir sistemin desteklediği Kullanıcı hedefleri ve görevleri|

 Visual Studio 'nun hangi sürümlerinin her diyagram türünü desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir sistemin veya varolan kodun mimarisini görselleştirmek için aşağıdaki diyagramları oluşturun:

|**Çizimindeki**|**Gösterilir**|
|-----------------|---------------|
|[Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)|Sistemin üst düzey mimarisi|
|Kod eşlemeleri<br /><br /> [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)|Mevcut koddaki bağımlılıklar ve diğer ilişkiler|
|Kod tarafından oluşturulan sınıf diyagramları<br /><br /> [Sınıf Diyagramları ile Çalışma (Sınıf Tasarımcısı)](../ide/working-with-class-diagrams-class-designer.md)|.NET Code 'da türler ve ilişkileri|

## <a name="common-tasks"></a>Ortak Görevler

|**İlerde**|**Görevinin**|
|---------------|--------------|
|[UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Modeller oluşturun** ve diyagramlar ekleyin.|
|[UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md)|Modeli düzenlemek için **diyagramlar çizin** .|
|[Paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md)|Bir modeli farklı takım üyelerinin üzerinde çalışabileceği birimlere bölmek için **paketler oluşturun** .|
|[UML sınıf diyagramları aracılığıyla kod oluşturma](../modeling/generate-code-from-uml-class-diagrams.md)|Uygulamanızı başlatmak için **Sınıf Diyagramlarından Kod oluşturun C#**  .|
|[Modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|Standart UML model öğelerini belirli amaçlarla genişletmek için stereotipler kullanarak **model öğelerini özelleştirin** .|
|[Model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md)|Görevleri, test çalışmalarını, hataları, gereksinimleri, sorunları veya modelinizin belirli bölümleriyle ilişkili diğer iş türlerini izlemenize yardımcı olması için **model öğeleri ve iş öğeleri arasında bağlantılar oluşturun** .|
|[Diyagramları görüntü olarak dışarı aktarma](../modeling/export-diagrams-as-images.md)|**Modelinizi ve diyagramlarınızı** , [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]kullanmayan kullanıcılar da dahil diğer kullanıcılarla paylaşmanız için kaydedin.|

## <a name="related-tasks"></a>İlgili görevler

|**İlerde**|**Görevinin**|
|---------------|--------------|
|[Kodu görselleştirme](../modeling/visualize-code.md)|Bilmediğiniz kodu daha iyi anlamak için kod haritaları ve katman diyagramları oluşturun.|
|[Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)|Kullanıcıların ihtiyaçlarını netleştirmek ve iletmek için modeller kullanın.|
|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|Sisteminizin genel yapısını ve davranışını ve kullanıcıların ihtiyaçlarını karşıladığından emin olmak için modelleri kullanın.|
|[Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)|Yazılımınızın kullanıcılarınızın ihtiyaçlarına ve sisteminizin genel mimarisine uygun olduğundan emin olun.|
|[Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)<br /><br /> [Çevik geliştirmede modelleri kullanma](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Geliştirme sırasında sisteminizi anlamanıza ve değiştirmenize yardımcı olması için modeller kullanın.|
|[Modelleme çözümünüzün yapısını oluşturma](../modeling/structure-your-modeling-solution.md)|Büyük veya orta ölçekli bir projede modelleri düzenleyin.|

## <a name="external-resources"></a>Dış Kaynaklar

|**Alan**|**Köprü**|
|------------------|---------------|
|**Forumları**|-   [Visual Studio görselleştirme & modelleme araçları](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://go.microsoft.com/fwlink/?LinkId=184721)|
