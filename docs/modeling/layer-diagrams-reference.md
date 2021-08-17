---
title: Bağımlılık Diyagramları Başvurusu
description: Bu Visual Studio, sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için bağımlılık diyagramını kullanabileceğinizi öğrenin.
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b08f2814fc20cf97da0e0c081ea2d8a6d49e0129
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055451"
---
# <a name="dependency-diagrams-reference"></a>Bağımlılık diyagramları: başvuru

Bu Visual Studio, sisteminizin üst *düzey,* mantıksal mimarisini görselleştirmek için bir bağımlılık diyagramı kullanabilirsiniz. Bağımlılık diyagramı, sisteminizdeki fiziksel yapıtları katmanlar olarak adlandırılan mantıksal ve soyut gruplar halinde *organize ediyor.* Bu katmanlar, yapıtların gerçekleştirecekleri önemli görevleri veya sisteminizin ana bileşenlerini açıklar. Her katman, daha ayrıntılı görevleri açıklayan iç içe katmanlar da içerebilir.

Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

> [!NOTE]
> .NET Core projeleri için bağımlılık diyagramları, 2019 Visual Studio 16.2 sürümünden itibaren de destekleni.

Katmanlar arasında hedeflenen veya mevcut bağımlılıkları belirtebilirsiniz. Ok olarak temsil edilen bu bağımlılıklar, hangi katmanların kullanabileceğini veya şu anda diğer katmanlar tarafından temsil edilen işlevselliği kullanabileceğini gösteriyor. Bir bağımlılık diyagramı, sisteminizi ayrı rolleri ve işlevleri açıklayan katmanlarda düzenleyerek kodunuzu daha kolay anlamanıza, yeniden kullanmanıza ve korumanıza yardımcı olabilir.

Aşağıdaki görevleri gerçekleştirmeye yardımcı olması için bir bağımlılık diyagramı kullanın:

- Sisteminizin mevcut veya hedeflenen mantıksal mimarisini iletir.

- Mevcut kodunuzla hedeflenen mimari arasındaki çakışmaları keşfedin.

- Sisteminizi yeniden düzenlemeniz, güncelleştirmeniz veya geliştirmeniz için değişikliklerin hedeflenen mimari üzerindeki etkisini görselleştirin.

- Giriş ve derleme işlemlerinizi doğrulamayı da dahil edin ve kodunuzun geliştirilmesi ve bakımı sırasında hedeflenen mimariyi pekiştirin.

Bu konuda, bağımlılık diyagramında kullanabileceğiniz öğeler açıklanmıştır. Bağımlılık diyagramları oluşturma ve çizme hakkında daha ayrıntılı bilgi için bkz. [Bağımlılık Diyagramları: Yönergeler.](../modeling/layer-diagrams-guidelines.md) Katmanlama desenleri hakkında daha fazla bilgi için [Patterns & Practices sitesini ziyaret edin.](https://archive.codeplex.com/?p=apparch)

## <a name="reading-dependency-diagrams"></a>Bağımlılık diyagramlarını okuma

![Bağımlılık diyagramlarında öğeler](../modeling/media/uml_layerrefreading.png)

Aşağıdaki tabloda bağımlılık diyagramında kullanabileceğiniz öğeler açık almaktadır.

|**Şekil**|**Öğe**|**Açıklama**|
|-|-|-|
|1|**Katman**|Sisteminize fiziksel yapıtlardan bir mantıksal grup. Bu yapıtlar ad alanları, projeler, sınıflar, yöntemler gibi olabilir.<br /><br /> Bir katmana bağlı yapıtları görmek için katmanın kısayol menüsünü  açın ve Ardından Katman Gezgini'ni açmak için Bağlantıları **Görüntüle'yi seçin.**<br /><br /> Daha fazla bilgi için [bkz. Katman Gezgini.](#Explorer)<br /><br /> -   **Yasak Ad Alanı Bağımlılıkları** - Bu katmanla ilişkili yapıtların belirtilen ad alanlarına bağımlı olayamaz.<br />-   **Yasak Ad Alanları** - Bu katmanla ilişkili yapıtların belirtilen ad alanlarına ait olması gerektiğini belirtir.<br />-   **Gerekli Ad Alanları** - Bu katmanla ilişkili yapıtların belirtilen ad alanlarından birinin ait olması gerektiğini belirtir.|
|2|**Bağımlılık**|Bir katmanın işlevselliği başka bir katmanda kullanabileceğini, ancak tam tersinin kullana olmadığını gösterir.<br /><br /> -   **Yön** - Bağımlılığın yönünü belirtir.|
|3|**Çift Yönlü Bağımlılık**|Bir katmanın işlevselliği başka bir katmanda kullanabileceğini ve tam tersinin de geçerli olduğunu gösterir.<br /><br /> -   **Yön** - Bağımlılığın yönünü belirtir.|
|4|**Yorum**|Diyagrama veya diyagramda öğelere genel notlar eklemek için kullanın.|
|5|**Açıklama Bağlantısı**|Diyagramda öğelere açıklama bağlantısı için kullanın.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Katman Gezgini

Her katmanı çözümünüzde projeler, sınıflar, ad alanları, proje dosyaları ve yazılım diğer bölümleri gibi yapıtlara bağabilirsiniz. Katmanda bulunan sayı, katmana bağlı yapıt sayısını gösterir. Ancak katmanda yapıt sayısını okurken şunları unutmayın:

- Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

- Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

Katmanları ve yapıtları bağlama hakkında daha fazla bilgi için bkz:

- [Bağımlılık diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Bağlantılı yapıtları inceleme

Bağımlılık diyagramında, bir veya daha fazla katman için kısayol menüsünü açın ve ardından Bağlantıları **Görüntüle'yi seçin.**

**Katman Gezgini** açılır ve seçili katmanlara bağlı yapıtları gösterir. **Katman Gezgini'nde** yapıt bağlantılarının özelliklerinin her biri gösteren bir sütun bulunur.

> [!NOTE]
> Bu özelliklerin hepsini görmüyorsanız Katman Gezgini **penceresini** genişletin.

|**Katman Gezgini'nde sütun**|**Açıklama**|
|-|-|
|**Kategoriler**|Yapıt türü; örneğin, sınıf, ad alanı, kaynak dosya ve diğer|
|**Katman**|Yapıya bağlantı olan katman|
|**Doğrulamayı destekler**|True **ise,** katman doğrulama işlemi projenin bu öğeye veya bu öğeden bağımlılıklara uygun olduğunu doğrular.<br /><br /> False **ise,** bağlantı katman doğrulama sürecine katılmaz.<br /><br /> Daha fazla bilgi için [bkz. Bağımlılık Diyagramları: Yönergeler.](../modeling/layer-diagrams-guidelines.md)|
|**Tanımlayıcı**|Bağlantılı yapıt başvurusu|

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
