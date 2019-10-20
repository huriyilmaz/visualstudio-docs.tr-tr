---
title: UML sınıf diyagramlarındaki türlerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671325"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki türlerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sınıf diyagramında bir *tür* sınıf, arabirim veya sabit listesi.

> [!NOTE]
> Bu konu, UML sınıf diyagramlarındaki türlerin özellikleri hakkındadır. Daha fazla bilgi için aşağıdaki konulara bakın:

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)

- [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [UML sınıf diyagramlarındaki ilişkilendirmelerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>Özellikler
 Bunlar bir sınıf, arabirim veya sabit listesi özelliklerdir.

 Bir türün özelliklerini görmek için diyagramda veya **UML Model Gezgini**' nde türü sağ tıklatın ve ardından **Özellikler**' e tıklayın. Özellikler **, Özellikler penceresinde görünür** .

|**Özelliði**|**Default**|İçinde görünür|Açıklama|
|------------------|-----------------|----------------|-----------------|
|**Ad**|Varsayılan ad|Tüm öğeler|Öğesi tanımlar.|
|**Tam ad**|İçeren paket:: tür adı|Tüm öğeler|Öğeyi benzersiz bir şekilde tanımlar. Ön eki içeren paketin tam adı.|
|**Renk**|Tür türü için varsayılan|Tüm öğeler|Bu şeklin rengi. Diğer özelliklerden farklı olarak, bu, temeldeki model öğesinin bir özelliği değildir. Aynı türde farklı görünümlerde farklı renkler olabilir.|
|**Soyut**|False|örneği|True ise, sınıf örneklenemez ve temel sınıf olarak kullanılmak üzere tasarlanmıştır.|
|**Yaprak**|False|Sınıf, arabirim|True ise, türün türetilmiş türleri olması amaçlanmamıştır.|
|**Etkin**|False|örneği|True ise, bu türün her örneği denetim iş parçacığı ile ilişkilendirilir.|
|**Görünürlük**|Ortak|Class, Interface, Enumeration|-Genel-genel olarak görünür.<br />-Private-bu tür, sahibi olan paketin içinde görünür.<br />-Package-paket içinde görünür.|
|**İş öğeleri**|0 ilişkili|Tüm öğeler|Bu öğeyle ilişkili iş öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz. [bağlantı modeli öğeleri ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|
|**Açıklama**|adet|Tüm öğeler|Öğe hakkında genel notları buradan yapabilirsiniz.|
|**Şablon bağlama**|seçim|Class, Interface, Enumeration|Boş değilse, bu tür parametre değerlerini bu şablon sınıfına bağlayarak tanımlanır. Şablon parametrelerinin bağlamalarını görmek için özelliği genişletin.|
|**Şablon Parametreleri**|seçim|Class, Interface, Enumeration|Boş değilse, burada listelenen parametrelere sahip bir şablon sınıftır. Parametreleri eklemek veya bağımsız parametrelerin özelliklerini görüntülemek için **[...]** düğmesine tıklayın.|

## <a name="see-also"></a>Ayrıca Bkz.
 UML sınıf diyagramları UML sınıf diyagramları üzerindeki [ilişkilerin](../modeling/properties-of-associations-on-uml-class-diagrams.md) UML [sınıf diyagramları özelliklerindeki](../modeling/properties-of-operations-on-uml-class-diagrams.md) [özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md) UML sınıf [diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)
