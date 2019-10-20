---
title: 'UML Kullanım örneği diyagramları: başvuru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657301"
---
# <a name="uml-use-case-diagrams-reference"></a>UML Kullanım Durumu Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da *kullanım durumu diyagramı* , uygulamanızı veya sisteminizi kimin kullanacağını ve onunla neler yapabileceğini özetler. UML Kullanım örneği diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

 Kullanım durumu diyagramı, kullanıcı gereksinimlerinin açıklaması için bir odak görevi görür. Gereksinimler, kullanıcılar ve ana bileşenler arasındaki ilişkileri açıklar. Ayrıntıları ayrıntılı olarak tanımlamaz; Bunlar ayrı diyagramlarda veya her kullanım örneğine bağlanabilen belgelerde açıklanabilir. Kullanım örneği diyagramlarının, kullanıcılarınızın ihtiyaçlarını anlamanıza, tartışmanıza ve iletmelerine yardımcı olabilecek bilgiler için bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bu konu başlığı altında, kullanım örneği diyagramlarında bulunan öğeler açıklanmaktadır. Kullanım örneği diyagramlarının nasıl çizildiği hakkında daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md). Modelleme diyagramları oluşturma ve çizme hakkında daha fazla bilgi için bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-use-case-diagrams"></a>Kullanım örneği diyagramlarını okuma
 Aşağıdaki bölümlerde yer alan tablolar, kullanım örneği diyagramında bulunan öğeleri ana özellikleriyle birlikte anlatmaktadır. Özelliklerin tam listesi için bkz. [UML Kullanım örneği diyagramlarında öğelerin özellikleri](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).

### <a name="actors-use-cases-and-subsystems"></a>Aktör, kullanım örnekleri ve alt sistemler
 ![Kullanım örneği diyagramındaki öğeler](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**Şeklinin**|**Öğe**|**Açıklama ve ana Özellikler**|
|---------------|-----------------|-----------------------------------------|
|1\.|**Aktör**|Uygulamanızla veya sisteminizle etkileşen bir Kullanıcı, kuruluş veya dış sistemi temsil eder. Aktör bir tür türüdür.<br /><br /> -   **resim yolu** -varsayılan aktör simgesi yerine kullanılması gereken bir görüntünün dosya yolu. Simgenin Visual Studio projesi içindeki bir kaynak dosyası olması gerekir.|
|2|**Kullanım örneği**|Belirli bir hedefin takibinde bir veya daha fazla aktör tarafından gerçekleştirilen eylemleri temsil eder. Kullanım örneği bir tür türüdür.<br /><br /> -   **konuları** -kullanım örneğinin göründüğü alt sistem.|
|3|**Kaldırma**|Aktörün bir kullanım durumunda bir parçasını aldığını belirtir.|
|4|**Alt sistem veya bileşen**|Üzerinde çalıştığınız sistem veya uygulama veya bunun bir parçası. Büyük bir ağdan bir uygulamadaki tek bir sınıfa kadar herhangi bir şey olabilir.<br /><br /> Bir sistemin veya bileşenin desteklediği kullanım örnekleri, dikdörtgeni içinde görüntülenir. Sisteminizin kapsamını netleştirmek için dikdörtgen dışında bazı kullanım durumlarının gösterilmesi yararlı olabilir.<br /><br /> Kullanım örneği diyagramında bir alt sistem temelde bir bileşen diyagramında bileşen ile aynı türde.<br /><br /> -   **dolaylı olarak örneklenmiştir** -false ise, çalışan sisteminizde bu alt sisteme doğrudan karşılık gelen bir veya daha fazla nesne vardır. True ise, alt sistem tasarımınızda yürütme sisteminde görüntülenen ve yalnızca bileşen bölümlerinin örneklenmesi aracılığıyla görünen bir yapıdır.|

### <a name="structuring-use-cases"></a>Kullanım örneklerini yapılandırma
 ![Include, Extend ve Genelleştirme ile kullanım örnekleri](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|Şekil|**Öğe**|Açıklama|
|-----------|-----------------|-----------------|
|5|**İçeriyor**|Dahil edilen kullanım örneği, içerilen bir kullanım durumu çağırır veya çağırır. Ekleme, kullanım durumunun daha küçük adımlara nasıl bölüneceğini göstermek için kullanılır. Dahil edilen kullanım durumu, ok ucu sonundadır.<br /><br /> Diyagramda adımların sırasını göstermediğine dikkat edin. Bu ayrıntıları anlatmak için bir etkinlik diyagramı, sıralı diyagram veya başka bir belge kullanabilirsiniz.|
|6|**Genişletmeyi**|Genişletme kullanım örneği, Genişletilmiş kullanım örneğine hedefler ve adımlar ekler. Uzantılar yalnızca belirli koşullar altında çalışır. Genişletilmiş kullanım durumu, ok ucu sonundadır.<br /><br /> Diyagramın, uzantının geçerli olduğu tam koşulları göstermediğine dikkat edin: bunları bir yoruma veya başka bir belgeye kaydedebilirsiniz.|
|7|**Devralma**|Özelleştirilmiş ve genelleştirilmiş bir öğe ilişkilendirir. Genelleştirilmiş öğe, ok ucu sonundadır.<br /><br /> Özelleştirilmiş kullanım örneği, genelleştirilinin hedeflerini ve aktörlerini devralır ve bunları elde etmek için daha özel hedefler ve adımlar ekleyebilir.<br /><br /> Özelleştirilmiş aktör, Genelleştirme 'nin kullanım örneklerini, özniteliklerini ve ilişkilendirmelerini devralır ve daha fazla eklenebilir.|
|8|**Bağımlılık**|Kaynak tasarımının hedefin tasarımına bağlı olduğunu gösterir.|
|9|**Yorum**|Diyagrama genel notlar eklemek için kullanılır.|
|10|**Deposunun**|Yapıt, başka bir diyagrama veya belgeye bağlantı sağlar. Çözüm Gezgini bir dosyayı sürükleyerek oluşturabilirsiniz. Diyagramda başka bir öğeye bağımlılığı ile bağlanabilir. Bir yapıt genellikle kullanım örneğini ayrıntılı olarak açıklayan bir sıralı diyagram, OneNote sayfası, Word belgesi veya PowerPoint sunumuna bağlamak için kullanılır. Belge, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümünde bir öğe ya da SharePoint sitesi gibi paylaşılan konumdaki bir belge olabilir.<br /><br /> -   **köprü**. Diyagramın veya belgenin URL veya dosya yolu.<br /><br /> Bağlandığı dosyayı veya Web sayfasını açmak için bir yapıya çift tıklayın.|
|11 (gösterilmez)|**Paketlerle**|Kullanım örnekleri, aktörler ve alt sistemler paketler içinde bulunabilir. Paket şekilleri diyagramda görünmez, ancak diyagramın **LinkedPackage** özelliğini ayarlayabilirsiniz. Diyagramda daha sonra oluşturduğunuz öğeler pakete yerleştirilir. Daha fazla bilgi için bkz. [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md).|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md) [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML sıralı diyagramları: başvuru](../modeling/uml-sequence-diagrams-reference.md) [UML sınıf diyagramları](../modeling/uml-class-diagrams-reference.md) : başvuru [UML Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru UML [bileşen](../modeling/uml-component-diagrams-reference.md) diyagramları: başvuru
