---
title: UML sınıf diyagramlarındaki ilişkilerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c5c914d87f0740dcd7b0f71190a4c2f54727f66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652087"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sınıf diyagramında herhangi bir tür çifti arasında *ilişkiler* çizebilirsiniz. Tür bir sınıf, arabirim veya sabit listesi.

 Bir ilişkilendirme, geliştirmekte olduğunuz sistemin, ilişkili türlerin örnekleri arasında bazı tür bağlantıları depoladığını gösterir. Genellikle, bağlantıların uygulanmasıyla ilgili hiçbir şey göstermez. Örneğin, bunlar işaretçiler, tablodaki satırlar, XML 'deki çapraz başvuru adları ve benzeri olabilir.

 İlişkilendirme bir özniteliği veya öznitelik çiftini gösteren diagrammatik bir yöntemidir. Örneğin, menü türünde bir özniteliğe sahip olacak bir sınıf restoran tanımladıysanız, Restoran ve menü arasında bir ilişki çizerek aynı tanımlamayı belirtebilirsiniz.

 Bir ilişki çizmek için, araç kutusunda **ilişki** ' e tıklayın, ilk türe ve sonra ikinci öğesine tıklayın. Örneklerin aynı türdeki diğer örneklerle bağlantılandırılarını göstermek için aynı türe iki kez tıklayabilirsiniz.

## <a name="properties"></a>Özellikler
 Bunlar, UML sınıf diyagramı üzerindeki bir ilişkilendirmenin özellikleridir.

 Bir ilişkinin özelliklerini görmek için ilişkiye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler Özellikler penceresi görüntülenir.

 Bazı özellikler, aşağıdaki çizimde gösterildiği gibi diyagramda de görünür.

 ![Assoa üzerindeki Özellikler](../modeling/media/uml-classprop.png "UML_ClassProp")

|**Özellik**|Description|
|------------------|-----------------|
|**Ad (1)**|İlişkilendirmeyi tanımlar. Ayrıca, diyagramda ilişkilendirmenin orta noktasında da görünür.|
|**Tam ad**|İlişkilendirmeyi benzersiz olarak tanımlar. İlişkilendirmenin ilk rolünü içeren paketin tam adı önekli.|
|**İş öğeleri**|Bu ilişkiye bağlı iş öğelerinin sayısı. İş öğelerini bağlamak için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).|
|**Color**|Bağlayıcının rengi. Diğer özelliklerden farklı olarak, bu, modeldeki temel ilişkinin bir özelliği değil, ilişkilendirmenin bu görünümünün bir özelliğidir.|
|**İlk rol**<br /><br /> **İkinci rol**|İlişkilendirmenin her sonuna bir rol denir. Her rol, ilişkinin ters sonundaki sınıfta denk özniteliğin özelliklerini açıklar.<br /><br /> Örnek diyagramda, menü ve menü öğesi arasındaki ilişkilendirmenin menü ve Içerik adlı rolleri vardır.<br /><br /> İçerik, menü sınıfındaki bir özniteliğin adıdır.|

### <a name="properties-of-each-role"></a>Her rolün özellikleri
 Her rolün özelliklerini görmek için, **Ilk rol** veya **ikinci rol** özelliğini genişletin.

|     **Özellik**     |          **Varsayılanını**          |                                                                                                                                                                                                                                                                                                                                        Description                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Rol adı (2)**   | Bu roldeki türün adı |                                                                                                                                                                                                                                                                                                       Rolün adı. Diyagramda ilişkilendirmenin sonuna yakın görünür.                                                                                                                                                                                                                                                                                                        |
|   **Toplama**    |             Hiçbiri              |                                                                        **Hiçbiri** (4)-sınıfların örnekleri arasındaki genel ilişkiyi temsil eder.<br /><br /> **Bileşik** (5)-Bu roldeki nesne, karşıt roldeki nesneyi içerir. Bileşik bir toplama ile bir ilişki oluşturmak için **bileşik** aracı kullanabilirsiniz.<br /><br /> **Shared** (6)-Bu roldeki nesne, diğer roldeki nesneye başvuruları içerir. **Toplama** aracını, paylaşılan toplama ile bir ilişki oluşturmak için kullanabilirsiniz.<br /><br /> Tam yorumlama, yerel kurala açıktır.                                                                         |
|    **Türetilir**    |             Yanlış             |                                                                                                                                                                                                                          True ise bağlantının bu sonundaki nesne diğer özniteliklerden ve ilişkilerden hesaplanır. Örneğin, MyWorkPlace MyEmployer. WorkPlace öğesinden hesaplanır. Ayrıntılar açıklamasında veya iliştirilmiş bir açıklamaya yazılmalıdır.                                                                                                                                                                                                                           |
| **Türetilmiş birleşim** |             Yanlış             |                                                                                                                                                                                                                                                                                                             True ise, rol türetilmiş türlerde bir rol kümesinin birleşimidir.                                                                                                                                                                                                                                                                                                             |
|   **Gezinilebilir**   |             Doğru              |                                                 İlişki bu yönde okunabilir. Karşıt rolün bir örneği verildiğinde, açıkladığınız yazılım bu roldeki ilişkili örneği etkin bir şekilde belirleyebilir.<br /><br /> Bir rol gezinilebilir ise ve diğeri değilse, gezinilebilir yöndeki ilişki üzerinde (7) bir ok belirir.<br /><br /> Varsayılan olarak, ilişkilendirme aracı bir yönde gezinilebilir bir ilişki oluşturur. Çift yönlü bir ilişkiye dönüştürmek için, ilişkilendirmeyi seçebilir, görüntülenen eylem etiketine tıklayabilir ve **çift yönlü yap**' a tıklayabilirsiniz.                                                 |
|   **Salt okunurdur**   |             Yanlış             |                                                                                                                                                                                                                                                                                   True ise, ilişkilendirmenin bir örneği oluşturulduktan sonra değiştirilemez. Bağlantı her zaman aynı nesneye gönderilir.                                                                                                                                                                                                                                                                                    |
| **Çokluk (3)** |               1               | **1** -ilişkilendirmenin bu sonu her zaman bir nesneye bağlanır. Şekilde, her menü öğesinde bir menü bulunur.<br /><br /> **0.. 1** -ilişkilendirmenin bu sonu bir nesneye bağlanır ya da bağlantı yok.<br /><br /> **\\**\* -ilişkilendirmenin diğer sonundaki her nesne bu uçtaki bir nesne koleksiyonuna bağlanır ve koleksiyon boş olabilir.<br /><br /> **1.. \\ ** \* -ilişkilendirmenin diğer sonundaki her nesne bu uçta en az bir nesneye bağlanır. Şekilde, her menünün en az bir menü öğesi vardır.<br /><br /> *n* **..** *a* -diğer uçtaki her nesnenin bu uçtaki nesnelere *n* ile *e* bağlantıları arasında bir koleksiyonu vardır. |
|    **Sıralanmıştır**    |             Yanlış             |                                                                                                                                                                                                                                                                                                  True ise, döndürülen koleksiyon sıralı bir liste oluşturur. 1 ' den fazla çokluk için.                                                                                                                                                                                                                                                                                                   |
|    **Benzersizdir**     |             Yanlış             |                                                                                                                                                                                                                                                                                              True ise, döndürülen koleksiyonda yinelenen değer yoktur. 1 ' den fazla çokluk için.                                                                                                                                                                                                                                                                                              |
|    **Görünürlük**    |            Genel             |                                                                                                                                                                                                                                 Genel-genel görünür<br /><br /> Özel-sahip türünün dışında görünmez<br /><br /> Korumalı-sahibinden türetilen türlere görünür<br /><br /> Package-aynı paket içindeki diğer türlere görünür.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sınıf diyagramları:](../modeling/uml-class-diagrams-reference.md) UML sınıf diyagramları ' nın UML sınıf [diyagramları özelliklerinde](../modeling/properties-of-attributes-on-uml-class-diagrams.md) başvuru [özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md) UML sınıf [diyagramları UML sınıf](../modeling/properties-of-operations-on-uml-class-diagrams.md) [diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)
