---
title: Bağımlılık diyagramları başvurusu
description: Visual Studio 'da, sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için bir bağımlılık diyagramı kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
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
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f173e27588538c806d075e0a6b010fbd848f2690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917006"
---
# <a name="dependency-diagrams-reference"></a>Bağımlılık diyagramları: başvuru

Visual Studio 'da, sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için bir *bağımlılık diyagramı* kullanabilirsiniz. Bağımlılık diyagramı, sisteminizdeki fiziksel yapıtları *Katman* olarak adlandırılan mantıksal, soyut gruplar halinde düzenler. Bu katmanlar, yapıtların gerçekleştirdiği ana görevleri veya sisteminizin ana bileşenlerini anlatmaktadır. Her katman, daha ayrıntılı görevleri tanımlayan iç içe katmanlar da içerebilir.

Hangi Visual Studio sürümlerini bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> .NET Core projeleri için bağımlılık diyagramları, Visual Studio 2019 sürüm 16,2 ' den itibaren desteklenmektedir.

Katmanlar arasında amaçlanan veya var olan bağımlılıkları belirtebilirsiniz. Oklar olarak temsil edilen bu bağımlılıklar, hangi katmanların diğer katmanlar tarafından temsil edilen işlevselliği kullanılacağını veya şu anda hangi katmanlarda kullanılabilir olduğunu gösterir. Sisteminizi ayrı roller ve işlevleri tanımlayan katmanlarla düzenleyerek, bir bağımlılık diyagramı, kodunuzu anlamanıza, yeniden kullanmanıza ve bakımını yapmanıza yardımcı olabilir.

Aşağıdaki görevleri gerçekleştirmenize yardımcı olması için bir bağımlılık diyagramı kullanın:

- Sisteminizin mevcut veya amaçlanan mantıksal mimarisine iletişim kurun.

- Mevcut kodunuz ile amaçlanan mimari arasındaki çakışmaları bulur.

- Sisteminizi yeniden düzenleme, güncelleştirme veya geliştirerek hedeflenen mimarideki değişikliklerin etkisini görselleştirin.

- İade etme ve oluşturma işlemlerinizin doğrulanmasını ekleyerek kodunuzun geliştirilmesi ve bakımı sırasında amaçlanan mimariyi güçle zorlayın.

Bu konu başlığı altında, bir bağımlılık diyagramında kullanabileceğiniz öğeler açıklanmaktadır. Bağımlılık diyagramları oluşturma ve çizme hakkında daha ayrıntılı bilgi için bkz. [bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md). Katman desenleri hakkında daha fazla bilgi için, [desenler & uygulamalar sitesini](https://archive.codeplex.com/?p=apparch)ziyaret edin.

## <a name="reading-dependency-diagrams"></a>Bağımlılık diyagramlarını okuma

![Bağımlılık diyagramlarındaki öğeler](../modeling/media/uml_layerrefreading.png)

Aşağıdaki tabloda, bir bağımlılık diyagramında kullanabileceğiniz öğeler açıklanmaktadır.

|**Şeklinin**|**Öğe**|**Açıklama**|
|-|-|-|
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

- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Bağlantılı yapıtları inceleyin

Bağımlılık diyagramında bir veya daha fazla katmanın kısayol menüsünü açın ve **bağlantıları görüntüle**' yi seçin.

**Katman Gezgini** açılır ve seçili katmanlarla bağlantılı yapıtları gösterir. **Katman Gezgini** , yapıt bağlantılarının her bir özelliğini gösteren bir sütun içerir.

> [!NOTE]
> Bu özelliklerin tümünü göremiyorsanız, **Katman Gezgini** penceresini genişletin.

|**Katman Gezgini 'ndeki sütun**|**Açıklama**|
|-|-|
|**Kategoriler**|Sınıf, ad alanı, kaynak dosya vb. gibi yapıt türü|
|**Katman**|Yapıtı bağlayan katman|
|**Doğrulamayı destekler**|**Doğru** ise, katman doğrulama işlemi projenin bu öğeden veya bu öğeden bağımlılıklara uygun olduğunu doğrulayabilirler.<br /><br /> **Yanlışsa**, bağlantı katman doğrulama işlemine katılmaz.<br /><br /> Daha fazla bilgi için bkz. [bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md).|
|**Tanımlayıcı**|Bağlı yapıt başvurusu|

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
