---
title: 'UML sınıf diyagramları: başvuru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06e83e254cad77d4ede9716a18a51f6476fb51ad
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850175"
---
# <a name="uml-class-diagrams-reference"></a>UML Sınıf Diyagramları: Başvuru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sınıf diyagramı, uygulamanız tarafından hem dahili olarak hem de kullanıcılarıyla iletişim halinde kullanılan nesne ve bilgi yapılarını açıklar. Belirli bir uygulamaya başvuru olmadan bilgileri açıklar. Sınıfları ve ilişkileri, veritabanı tabloları, XML düğümleri veya yazılım nesnelerinin kompozisyonları gibi birçok şekilde uygulanabilir.

> [!NOTE]
> Bu konu UML sınıf diyagramları hakkındadır. Program kodunu görselleştirmek için kullanılan, .NET sınıf diyagramı olan başka bir tür sınıf diyagramı vardır. Daha fazla bilgi için bkz. [sınıfları ve türleri tasarlama ve görüntüleme](https://msdn.microsoft.com/library/ab7aty24.aspx).

 Bir UML sınıf diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' nı seçin. UML sınıf diyagramlarının nasıl çizildiği hakkında daha fazla bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md). Modelleme diyagramları oluşturma ve çizme hakkında daha fazla bilgi için bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md).

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Sınıf diyagramlarını okuma
 Bu bölümdeki tabloda, UML sınıf diyagramında görebileceğiniz öğeler açıklanmaktadır. Bu öğelerin özellikleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![İlişkileri ve özellikleri gösteren üç sınıf](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Şeklinin** |       **Öğe**        |                                                                                                                                                             **Açıklama**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1\.     |        **Sınıfı**         |                                                           Verilen yapısal veya davranış özelliklerini paylaşan nesnelerin tanımı. Daha fazla bilgi için bkz. [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1\.     |        Sınıflandırıcı        |                                                                                                             Bir sınıf, arabirim veya sabit listesinin genel adı. Bileşenler, kullanım örnekleri ve aktörler de sınıflandırıcılardır.                                                                                                             |
|     2     | Daraltma/genişletme denetimi |                                                                                         Sınıflandırıcının ayrıntılarını göremiyorsanız sınıflandırıcının sol üst kısmındaki genişleticiye tıklayın. Ayrıca, her kesimde [+] düğmesine tıklamanız gerekebilir.                                                                                         |
|     3     |      **Öznitelik**       |   Bir sınıflandırıcının her örneğine eklenen bir türü belirtilmiş değer.<br /><br /> Bir öznitelik eklemek için, **öznitelikler** bölümüne tıklayın ve ardından **ENTER**tuşuna basın. Özniteliğin imzasını yazın. Daha fazla bilgi için bkz. [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **İşlem**       | Sınıflandırıcının örnekleri tarafından gerçekleştirilebilecek bir yöntem veya işlev. Bir işlem eklemek için, **işlemler** bölümüne tıklayın ve ardından **ENTER**tuşuna basın. İşlemin imzasını yazın. Daha fazla bilgi için bkz. [UML sınıf diyagramlarındaki Işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **İlişkilendirme**      |                                                                  İki sınıflandırıcıın üyeleri arasındaki ilişki. Daha fazla bilgi için bkz. [UML sınıf diyagramlarındaki Ilişkilerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5A     |     **Toplama**      |                                                                                                    Paylaşılan bir sahiplik ilişkisini temsil eden bir ilişki. Sahip rolünün **toplama** özelliği **paylaşılan**olarak ayarlanmıştır.                                                                                                     |
|    5B     |     **Birleşim**      |                                                                                                      Bir tam bölüm ilişkisini temsil eden bir Ilişki. Sahip rolünün **toplama** özelliği **bileşik**olarak ayarlanır.                                                                                                      |
|     6     |   **İlişkilendirme adı**   |                                                                                                                                         Bir ilişkilendirmenin adı. Ad boş bırakılabilir.                                                                                                                                          |
|     7     |      **Rol adı**       |                       Bir rolün adı, yani bir ilişkinin sonu. , İlişkili nesneye başvurmak için kullanılabilir. Önceki çizimde, herhangi bir sıra `O`için, `O.ChosenMenu` ilişkili menü olur.<br /><br /> Her rolün, ilişkilendirmenin özellikleri altında listelenen kendi özellikleri vardır.                       |
|     8     |     **Çokluk**     |                                         Bu uçtaki nesnelerden kaç tane nesnenin diğer bir nesneye bağlanıp bağlanamayacağını gösterir. Örnekte, her bir siparişin tam olarak bir menü ile bağlantılı olması gerekir.<br /><br /> **\\** \*, yapılabilecek bağlantı sayısı üst sınırı olmadığı anlamına gelir.                                         |
|     9     |    **İnin**    |  *Belirli* sınıflandırıcı, tanımının bir parçasını *genel* sınıflandırıcıdan devralır. Genel sınıflandırıcı, bağlayıcının ok ucunda. Öznitelikler, ilişkilendirmeler ve işlemler belirli sınıflandırıcının devralmıştır.<br /><br /> İki sınıflandırıcı arasında genelleştirme oluşturmak için **Devralma** aracını kullanın.   |

 ![Arabirim ve numaralandırma içeren paket](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Şekil|Öğe|Açıklama|
|-----------|-------------|-----------------|
|10|**Arabirimi**|Bir nesnenin dışarıdan görünür davranışının bir bölümü tanımı. Daha fazla bilgi için bkz. [UML sınıf diyagramlarındaki türlerin özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Sabit listesi**|Değişmez değerler kümesinden oluşan bir sınıflandırıcı.|
|12|**Paket**|Sınıflandırıcılar, ilişkilendirmeler, Eylemler, yaşam çizgileri, bileşenler ve paketler grubu. Mantıksal sınıf diyagramı, üye Sınıflandırıcıların ve paketlerin paket içinde içerildiğini gösterir.<br /><br /> Adların, **package1** içindeki **Class1** 'In bu paketin dışındaki **Class1** 'den farklı olması için paketler içinde kapsamı vardır. Paketin adı, içeriğinin **tam ad** özelliklerinin bir parçası olarak görüntülenir.<br /><br /> Herhangi bir UML diyagramının **bağlı paket** özelliğini bir pakete başvuracak şekilde ayarlayabilirsiniz. Bu diyagramda oluşturduğunuz tüm öğeler, daha sonra paketin bir parçası olur. **UML Model Gezgini**'nde paketin altında görüntülenir.|
|13|**İçeri Aktar**|Tek bir paketin diğerinin tüm tanımlarını içerdiğine işaret eden paketler arasındaki ilişki.|
|14|**Bağımlılık**|Ok ucu sonundaki sınıflandırıcının değişmesi durumunda bağımlı sınıflandırıcının tanımı veya uygulanması değişebilir.|

 ![Bağlayıcı ve lolipop ile gösterilen gerçekleştirme](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Şekil|**Öğe**|Açıklama|
|-----------|-----------------|-----------------|
|15|**Gerçekleştirme**|Sınıfı, arabirimi tarafından tanımlanan işlemleri ve öznitelikleri uygular.<br /><br /> Bir sınıf ve arabirim arasında bir gerçekleştirme oluşturmak için **Devralma** aracını kullanın.|
|16|**Gerçekleştirme**|Aynı ilişkinin alternatif bir sunumu. Lolipop sembolünün etiketi, arabirimini tanımlar.<br /><br /> Bu sunuyu oluşturmak için var olan bir gerçekleştirme ilişkisi seçin. İlişkinin yakınında bir eylem etiketi görünür. Eylem etiketine tıklayın ve ardından **Lolipop olarak göster**' e tıklayın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML sınıf diyagramları:](../modeling/uml-class-diagrams-guidelines.md) UML sınıf diyagramları üzerindeki [nesnelerin](../modeling/properties-of-operations-on-uml-class-diagrams.md) [UML sınıf](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diyagramları özelliklerindeki yönergeler [özellikleri UML](../modeling/properties-of-types-on-uml-class-diagrams.md) sınıf diyagramlarında [ilişkilerin](../modeling/properties-of-associations-on-uml-class-diagrams.md) UML sınıf diyagramları özellikleri
