---
title: 'Katman diyagramları: başvuru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 448a74b739bbb339d5f3b3e56c0ba59072994109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850624"
---
# <a name="layer-diagrams-reference"></a>Katman Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için bir *Katman diyagramı* kullanabilirsiniz. Katman diyagramı, sisteminizdeki fiziksel yapıtları *Katman*olarak adlandırılan mantıksal, soyut gruplar halinde düzenler. Bu katmanlar, yapıtların gerçekleştirdiği ana görevleri veya sisteminizin ana bileşenlerini anlatmaktadır. Her katman, daha ayrıntılı görevleri tanımlayan iç içe katmanlar da içerebilir.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Katmanlar arasında amaçlanan veya var olan bağımlılıkları belirtebilirsiniz. Oklar olarak temsil edilen bu bağımlılıklar, hangi katmanların diğer katmanlar tarafından temsil edilen işlevselliği kullanılacağını veya şu anda hangi katmanlarda kullanılabilir olduğunu gösterir. Sisteminizi ayrı roller ve işlevleri tanımlayan katmanlarla düzenleyerek bir katman diyagramı, kodunuzu anlamanıza, yeniden kullanmanıza ve bakımını yapmanıza yardımcı olabilir.

 Aşağıdaki görevleri gerçekleştirmenize yardımcı olması için bir katman diyagramı kullanın:

- Sisteminizin mevcut veya amaçlanan mantıksal mimarisine iletişim kurun.

- Mevcut kodunuz ile amaçlanan mimari arasındaki çakışmaları bulur.

- Sisteminizi yeniden düzenleme, güncelleştirme veya geliştirerek hedeflenen mimarideki değişikliklerin etkisini görselleştirin.

- İade etme ve oluşturma işlemlerinizin doğrulanmasını ekleyerek kodunuzun geliştirilmesi ve bakımı sırasında amaçlanan mimariyi güçle zorlayın.

  Bu konu başlığı altında, bir katman diyagramında kullanabileceğiniz öğeler açıklanmaktadır. Katman diyagramları oluşturma ve çizme hakkında daha ayrıntılı bilgi için bkz. [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md). Katman desenleri hakkında daha fazla bilgi için, [desenler & uygulamalar sitesini](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home)ziyaret edin.

## <a name="reading-layer-diagrams"></a>Katman diyagramlarını okuma
 ![Katman diyagramlarındaki öğeler](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 Aşağıdaki tabloda bir katman diyagramında kullanabileceğiniz öğeler açıklanmaktadır.

|**Şekil**|**Öğe**|**Açıklama**|
|---------------|-----------------|---------------------|
|1|**Katman**|Sisteminizdeki fiziksel yapıların mantıksal grubu. Bu yapıtlar ad alanları, projeler, sınıflar, yöntemler vb. olabilir.<br /><br /> Bir katmana bağlı yapıtları görmek için katmanın kısayol menüsünü açın ve sonra **Katman Gezgini**'ni açmak Için **bağlantıları görüntüle** ' yi seçin.<br /><br /> Daha fazla bilgi için bkz. [Katman Gezgini](#Explorer).<br /><br /> -   **Yasak ad alanı bağımlılıkları** -bu katmanla ilişkili yapıtların belirtilen ad alanlarına bağlı olduğunu belirtir.<br />-   **Yasak ad alanları** -bu katman ile ilişkili yapıtların belirtilen ad alanlarına ait olmaması gerektiğini belirtir.<br />-   **Gerekli ad alanları** -bu katman ile ilişkili yapıtların belirtilen ad alanlarından birine ait olması gerektiğini belirtir.|
|2|**Bağımlılık**|Bir katmanın işlevselliği başka bir katmanda kullanabilir, ancak tersi anlamına gelir.<br /><br /> -   **Yön** -bağımlılığın yönünü belirtir.|
|3|**Çift yönlü bağımlılık**|Bir katmanın başka bir katmandaki işlevleri kullanacağını ve bunun tersini gösterir.<br /><br /> -   **Yön** -bağımlılığın yönünü belirtir.|
|4|**Yorum**|Diyagramdaki diyagrama veya öğelere genel notlar eklemek için kullanın.|
|5|**Açıklama bağlantısı**|Diyagramdaki öğelere açıklama bağlamak için kullanın.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Katman Gezgini
 Çözümünüzde projeler, sınıflar, ad alanları, proje dosyaları ve yazılımınızın diğer kısımları gibi her bir katmanı çözümünüzdeki yapıtlara bağlayabilirsiniz. Katmandaki sayı katmana bağlı yapıların sayısını gösterir. Ancak, bir katmandaki yapıt sayısını okurken, aşağıdakileri unutmayın:

- Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

   Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

- Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

  Katman ve yapıt bağlama hakkında daha fazla bilgi için bkz.:

- [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Bağlantılı yapıtları incelemek için

- Katman diyagramında bir veya daha fazla katmanın kısayol menüsünü açın ve **bağlantıları görüntüle**' yi seçin.

     **Katman Gezgini** açılır ve seçili katmanlarla bağlantılı yapıtları gösterir. **Katman Gezgini** , yapıt bağlantılarının her bir özelliğini gösteren bir sütun içerir.

    > [!NOTE]
    > Bu özelliklerin tümünü göremiyorsanız, **Katman Gezgini** penceresini genişletin.

    |**Katman Gezgini 'ndeki sütun**|**Açıklama**|
    |----------------------------------|---------------------|
    |**Kategoriler**|Sınıf, ad alanı, kaynak dosya vb. gibi yapıt türü|
    |**Katman**|Yapıtı bağlayan katman|
    |**Doğrulamayı destekler**|**Doğru**ise, katman doğrulama işlemi projenin bu öğeden veya bu öğeden bağımlılıklara uygun olduğunu doğrulayabilirler.<br /><br /> **Yanlışsa**, bağlantı katman doğrulama işlemine katılmaz.<br /><br /> Daha fazla bilgi için bkz. [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md).|
    |**Tanımlayıcı**|Bağlı yapıt başvurusu|

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
