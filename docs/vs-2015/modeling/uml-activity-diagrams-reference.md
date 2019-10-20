---
title: 'UML etkinlik diyagramları: başvuru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a882867720e9cca2d51419643ebe60e692817a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658448"
---
# <a name="uml-activity-diagrams-reference"></a>UML Etkinlik Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir *etkinlik diyagramı* , bir dizi eylem aracılığıyla iş akışı olarak iş sürecini veya yazılım işlemini gösterir. Kişiler, yazılım bileşenleri veya bilgisayarlar bu eylemleri gerçekleştirebilir.

 Aşağıdaki örnekler gibi çeşitli türlerde süreçler için bir etkinlik diyagramı kullanabilirsiniz:

- Kullanıcılar ve sisteminiz arasındaki iş süreci veya iş akışı. Daha fazla bilgi için bkz. [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

- Kullanım durumunda gerçekleştirilen adımlar. Daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

- Bir yazılım protokolü, diğer bir deyişle, bileşenler arasında etkileşimlerin izin verilen dizileri.

- Yazılım algoritması.

  Bu konuda, etkinlik diyagramlarında kullanabileceğiniz öğeler açıklanmaktadır. Etkinlik diyagramlarını çizme hakkında daha ayrıntılı bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md). Bir UML etkinlik diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın. Modelleme diyagramlarını genel olarak çizme hakkında daha fazla bilgi için bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Etkinlik diyagramlarını okuma
 Aşağıdaki bölümlerde yer alan tablolar bir etkinlik diyagramında ve bunların ana özelliklerinde kullanabileceğiniz öğeleri anlatmaktadır. Öğelerin özelliklerinin tam listesi için bkz. [UML Etkinlik diyagramlarındaki öğelerin özellikleri](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Etkinlik diyagramında görünen eylemler ve diğer öğeler bir etkinlik oluşturur. Etkinliği UML Model Gezgini 'nde görebilirsiniz. Diyagrama ilk öğe eklediğinizde oluşturulur.

 Bir diyagramı okumak için, bir belirteç veya denetim iş parçacığının, bağlayıcılar üzerinde bir eylemden sonrakine geçirdiğinin olduğunu düşünün.

### <a name="simple-control-flows"></a>Basit denetim akışları
 Dallar ve döngüler içeren bir dizi eylemi gösterebilirsiniz. Burada açıklanan öğelerin nasıl kullanılacağı hakkında daha fazla bilgi için [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)konusunun denetim akışını açıklama bölümüne bakın.

 ![Basit bir denetim akışı](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

||||
|-|-|-|
|**Şeklinin**|**Öğe**|**Açıklama ve ana Özellikler**|
|1\.|**Ön**|Etkinliğin Kullanıcı veya yazılımın bir görevi gerçekleştirdiği bir adım.<br /><br /> Eylem, tüm gelen akışlara bir belirteç ulaştığında başlayabilir. Bu tamamlandığında, tüm giden akışlara belirteç gönderilir.<br /><br /> -   **gövdesi** -eylemi ayrıntılı olarak belirtir.<br />-   **Language** -Gövdedeki ifadenin dili.<br />**Yerel Postconditions** -   , yürütme sona erdiğinde karşılanması gereken kısıtlamalar. Eylem tarafından elde edilen hedef.<br />**Yerel önkoşulları** -   , yürütme başlamadan önce karşılanması gereken kısıtlamalar.|
|2|**Denetim Akışı**|Eylemler arasındaki denetim akışını gösteren bir bağlayıcı. Diyagramı yorumlamak için bir belirtecin bir eylemden sonrakine akmasını düşünün.<br /><br /> Bir denetim akışı oluşturmak için **bağlayıcı** aracını kullanın.|
|3|**İlk düğüm**|Etkinlikteki ilk eylemi veya eylemleri gösterir. Etkinlik başladığında, bir belirteç ilk düğümden akar.|
|4|**Etkinlik son düğümü**|Etkinliğin bitişi. Bir belirteç geldiğinde etkinlik sonlanır.|
|5|**Karar düğümü**|Akıştaki koşullu dal. Bir giriş ve iki veya daha fazla çıkışı vardır. Gelen bir belirteç çıktılardan yalnızca birinde oluşur.|
|6|**Guard**|Bir belirtecin bağlayıcı üzerinde akabilir olup olmadığını belirten bir koşul. Bir karar düğümünün giden akışlarında en sık kullanılan.<br /><br /> Bir koruyucu ayarlamak için bir akışa sağ tıklayın, **Özellikler** ' e tıklayın ve ardından **Guard** özelliğini ayarlayın.|
|7|**Birleştirme düğümü**|Bir karar düğümüyle bölünen akışları birleştirmek için gereklidir. İki veya daha fazla girişe ve bir çıkışa sahiptir. Herhangi bir girişte bir belirteç çıktıda ortaya çıkar.|
|8|**Yorum**|Bağlandığı öğeler hakkında ek bilgi sağlar.|
|9|**Çağrı davranışı eylemi**|Başka bir etkinlik diyagramı üzerinde daha ayrıntılı olarak tanımlanmış bir eylem.<br /><br /> -   **IsSynchronous** -true ise eylem, etkinlik sonlanana kadar bekler.<br />-   **davranış** -çağrılan etkinlik.|
|(gösterilmez)|**Çağrı Işlemi eylemi**|Bir sınıf örneği üzerinde bir işlem çağıran bir eylem.|
||**Etkinlik**|Bir etkinlik diyagramı tarafından gösterilen iş akışı. Etkinliğin özelliklerini görmek için **UML Model Gezgini**' nde seçmeniz gerekir.<br /><br /> -   **salt okunurdur** -true ise etkinlik herhangi bir nesnenin durumunu değiştirmemelidir.<br />-   **tek yürütme** -true ise, bu diyagramda aynı anda en fazla bir yürütme vardır.|
||**UML etkinlik diyagramı**|Etkinlik görüntüleyen diyagram. Özelliklerini görmek için diyagramın boş bir kısmına tıklayın. **Note:**  Etkinlik diyagramının adları, diyagramı içeren dosya ve diyagram tarafından görüntülenen etkinlik farklı olabilir.|

### <a name="concurrent-flows"></a>Eş zamanlı Akışlar
 Aynı anda yürütülen eylem dizilerini tanımlayabilirsiniz. Daha fazla bilgi için bkz. eşzamanlı akışları çizme.

 ![Eşzamanlı akışı gösteren etkinlik diyagramı](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

||||
|-|-|-|
|**Şeklinin**|**Öğe**|**Açıklama**|
|11|**Çatal düğümü**|Tek bir akışı eşzamanlı akışlara böler. Her gelen belirteç, giden bağlayıcıda bir belirteç üretir.|
|12|**Düğüm Birleştir**|Eşzamanlı akışları tek bir akışta birleştirir. Her gelen akış için bekleyen bir belirteç olduğunda, çıktıda bir belirteç oluşturulur.|
|13|**Sinyal gönderme eylemi**|Başka bir etkinliğe veya aynı etkinlik içindeki eşzamanlı bir iş parçacığına ileti veya sinyal gönderen bir eylem. İletinin türü ve içeriği, eylemin başlığı tarafından kapsanır veya ek açıklamalarda belirtilir.<br /><br /> Eylem, bir nesne akışında veya giriş sabitinde (16) eyleme geçirilebilen, sinyalde veri gönderebilir.|
|14|**Olay kabul etme eylemi**|Eyleme devam etmeden önce bir ileti veya sinyal bekleyen bir eylem. Eylemin alabileceği ileti türü, başlık tarafından ima edilir veya ek açıklamalarda belirtilir.<br /><br /> Eylemin gelen denetim akışı yoksa, ileti her aldığında bir belirteç üretir.<br /><br /> Eylem, bir nesne akışına veya çıkış iğnesine (17) geçirilebilen, sinyalde veri alabilir.<br /><br /> -   **IsUnmarshall** -true ise, birkaç tür çıkış iğnesi olabilir ve veriler bunlar üzerinde sıradan çıkar. Yanlış ise, tüm veriler bir PIN üzerinde görünür.|

### <a name="DataFlow"></a>Veri akışları
 Verilerin akışını bir eylemden diğerine tanımlayabilirsiniz. Bu bölümde kullanılan öğeler hakkında daha fazla bilgi için, bir etkinlik diyagramı çizmek için Konu Kılavuzu konusunun veri akışları çizme bölümüne bakın.

 ![Veri akışını gösteren etkinlik diyagramı](../modeling/media/uml-actovdata.png "UML_ActOvData")

||||
|-|-|-|
|**Şeklinin**|**Öğe**|**Açıklama**|
|15|**Nesne düğümü**|Bir akış üzerinde geçen verileri temsil eder.<br /><br /> -   **sıralaması** -birden çok belirteç nasıl depolanır.<br />-   **seçimi** -bir işlemi çağırır, bu, verileri filtreleyerek başka bir diyagramda tanımlanabilir.<br />-   **üst sınır** -0 verilerin akış üzerinde doğrudan geçmesi gerektiğini belirtir;  \*, verilerin akışta depolanabileceğini belirtir.<br />-   **türü** -depolanan ve aktarılan nesnelerin türü.|
|16|**Giriş PIN 'ı**|Bir eylemin yürütüldüğünde alabileceği verileri temsil eder.<br /><br /> -   **türü** -aktarılan nesnelerin türü.|
|17|**Çıkış Iğnesi**|Bir eylemin yürütüldüğünde oluşturduğu verileri temsil eder.<br /><br /> -   **türü** -aktarılan nesnelerin türü.|
|18|**Etkinlik parametresi düğümü**|Etkinlik tarafından verilerin alınabileceği veya üretilebileceği bir nesne düğümü.<br /><br /> Diyagram tarafından temsil edilen etkinlik başka bir etkinlikten çağrıldığında veya diyagramda bir işlem ya da işlev açıklandığı zaman kullanılır.<br /><br /> -   **türü** -aktarılan nesnelerin türü.|
|(gösterilmez)|**Nesne akışı**|Eylemler ve nesne düğümleri arasında veri akışını gösteren bir bağlayıcı.<br /><br /> Bir nesne akışı oluşturmak için **bağlayıcı** aracını kullanarak bir giriş veya çıkış sabitlemesi ya da bir nesne düğümünü başka bir öğeye bağlayın.<br /><br /> -   **seçimi** -bir işlemi çağırır, bu, verileri filtreleyerek başka bir diyagramda tanımlanabilir.<br />-   **dönüştürme** -bir işlemi çağırır, bu, verileri dönüştüren başka bir diyagramda tanımlanabilir.<br />**IÇok noktaya yayın** -   -çeşitli alıcı nesne veya bileşen olabileceğini belirtir.<br />**ımultireceive** -   -girişlerin çeşitli nesnelerden veya bileşenlerden alınamayacağını gösterir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)
