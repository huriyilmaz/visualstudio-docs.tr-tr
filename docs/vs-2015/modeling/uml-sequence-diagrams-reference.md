---
title: 'UML sıralı diyagramlar: başvuru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9b02bbad4fa897404f6c20e12b1705a3ae9ac8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661709"
---
# <a name="uml-sequence-diagrams-reference"></a>UML Sıralı Diyagramlar: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, bir *sıralı diyagram* , sınıfların, bileşenlerin, alt sistemlerin veya aktörlerin örnekleri arasındaki ileti dizisini temsil eden bir etkileşimi gösterir. Diyagramda zaman akıp, bir katılımcıdan diğerine denetim akışını gösterir. Sınıflar ve Yöntemler yerine örnekleri ve olayları görselleştirmek için sıralı diyagramlar kullanın. Diyagramda aynı türden birden fazla örnek görünebilir. Aynı iletinin birden fazla oluşumu da görünebilir.

 UML sıralı diyagramları bir UML modelinin parçasıdır ve yalnızca UML modelleme projeleri içinde mevcuttur. UML sıralı diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın. [UML sıralı diyagramları](../modeling/uml-sequence-diagrams-guidelines.md) veya [UML modelleme diyagramlarını](../modeling/edit-uml-models-and-diagrams.md) genel olarak oluşturma ve çizme hakkında daha fazla bilgi edinin.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-sequence-diagrams"></a>Sıralı diyagramlar okunuyor
 Aşağıdaki tabloda, sıralı diyagramda görebileceğiniz öğeler açıklanmaktadır. Bu [öğelerin özellikleri](../modeling/properties-of-elements-on-uml-sequence-diagrams.md)hakkında daha fazla bilgi edinin.

 ![Sıralı diyagramın parçaları](../modeling/media/uml-sequence.png "UML_Sequence")

|**Şeklinin**|**Öğe**|**Açıklama**|
|---------------|-----------------|---------------------|
|1\.|**Yaşam**|Bir etkileşim sırasında bir katılımcı sırasında gerçekleşen olayların sırasını temsil eden, zaman satırı aşağı ilerledikçe oluşan dikey bir çizgi. Bu katılımcı bir sınıf, bileşen veya aktör örneği olabilir.|
|2|**Aktör**|Geliştirmekte olduğunuz sistem dışında bir katılımcı.<br /><br /> **Aktör özelliğini ayarlayarak** bir yaşam çizgisinin en üstünde bir aktör sembolü görünmesini sağlayabilirsiniz.|
|3|**Zaman uyumlu ileti**|Gönderen, devam etmeden önce zaman uyumlu bir iletiye yanıt bekler. Diyagramda hem çağrı hem de dönüş gösterilmektedir. Zaman uyumlu iletiler, bir program içindeki sıradan işlev çağrılarını ve aynı şekilde davranan diğer ileti türlerini temsil etmek için kullanılır.|
|4|**Zaman uyumsuz ileti**|Gönderen devam etmeden önce yanıt gerektirmeyen bir ileti. Zaman uyumsuz bir ileti yalnızca gönderenden gelen çağrıyı gösterir. Ayrı iş parçacıkları veya yeni bir iş parçacığının oluşturulması arasındaki iletişimi göstermek için kullanın.|
|5|**Yürütme oluşumu**|Katılımcının yaşam çizgisinde görüntülenen ve katılımcı bir işlem yürütürken dönemi temsil eden dikey gölgeli dikdörtgen.<br /><br /> Yürütme, katılımcının bir ileti alacağı yerde başlar. Başlatma iletisi zaman uyumlu bir iletidir, yürütme, bir «return» geri dönüşle sona erer.|
|6|**Geri arama iletisi**|Önceki bir çağrıdan dönüş için bekleyen bir katılımcıya geri döndüren bir ileti. Ortaya çıkan yürütme oluşumu var olan en üstünde görünür.|
|7|**Kendi kendine ileti**|Bir katılımcıdan kendine bir ileti. Ortaya çıkan yürütme oluşumu, gönderme yürütmesinin en üstünde görünür.|
|8|**İleti oluştur**|Katılımcı oluşturan bir ileti. Bir katılımcı bir oluşturma iletisi alırsa, ilk alması gerekir.|
|9|**İleti bulundu**|Bilinmeyen veya belirtilmemiş bir katılımcıdan zaman uyumsuz bir ileti.|
|10|**Kayıp ileti**|Bilinmeyen veya belirtilmemiş bir katılımcıya zaman uyumsuz bir ileti.|
|11|**Yorum**|Bir açıklama, bir yaşam çizgisinin herhangi bir noktasına iliştirilebilir.|
|12|**Etkileşim kullanımı**|Başka bir diyagramda tanımlı bir ileti dizisini barındırır.<br /><br /> Bir **etkileşim kullanımı**oluşturmak için araca tıklayın ve sonra dahil etmek istediğiniz yaşam çizgileri arasında sürükleyin.|
|13|**Birleşik parça**|Parçalar koleksiyonu. Her parça bir veya daha fazla ileti içerebilir. Farklı türlerde birleştirilmiş parçalar vardır. Daha fazla bilgi için bkz. [UML sıralı diyagramlarındaki parçaların bulunduğu denetim akışını açıklama](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Bir parça oluşturmak için, bir iletiye sağ tıklayın, şununla **çevreye**gelin ve ardından bir parça türüne tıklayın.|
|14|**Parça koruyucusu**|Parçanın gerçekleşip gerçekleşmeyeceğini ilgili bir koşul sağlamak için kullanılabilir.<br /><br /> Koruyucuyu ayarlamak için bir parça seçin, ardından koruyucu ' ı seçin ve bir değer yazın.|
|**Sayı**|**Yok etme olayı**|Nesnenin silindiği veya artık erişilemeyen noktayı temsil eder. Her yaşam çizgisinin altında görünür.|
||**Uyor**|Sıralı diyagramda görüntülenen ileti ve yaşam çizgileri koleksiyonu. Bir etkileşimin özelliklerini görüntülemek için **UML Model Gezgini**' nde seçmeniz gerekir.|
||**Sıralı diyagram**|Bir etkileşimi görüntüleyen diyagram. Özelliklerini görüntülemek için diyagramın boş bir kısmına tıklayın. **Note:**  Sıralı diyagramın adları, gösterdiği etkileşim ve diyagramı içeren dosya hepsi farklı olabilir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md) [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md) [UML sınıf diyagramları](../modeling/uml-class-diagrams-reference.md) : başvuru [UML Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru UML [bileşen](../modeling/uml-component-diagrams-reference.md) diyagramları: başvuru
