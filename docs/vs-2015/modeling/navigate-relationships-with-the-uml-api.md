---
title: UML API ile ilişkilerde gezinme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c0067e213fdff2bde09c290d9fcaa9b4f52b9ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668527"
---
# <a name="navigate-relationships-with-the-uml-api"></a>UML API ile ilişkilerde gezinme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir model, farklı ilişki türlerine göre birbirine bağlanmış öğelerden oluşur. Bu konu başlığında Program kodundaki modelde gezinme açıklanmaktadır.

## <a name="traversing-relationships"></a>Çapraz geçiş geçişi

### <a name="any-relationship"></a>Herhangi bir ilişki
 Belirtilen öğeye bağlı tüm öğeleri bulmak için `GetRelatedElements<T>()` kullanın. Tüm türlerdeki ilişkilerle çapraz geçiş yapmak için `T` `IRelationship` ayarlayın veya yalnızca o tür çapraz geçiş yapmak için `IAssociation` gibi daha belirli bir tür kullanın.

```
IElement anElement;
// Select all elements related to anElement.
Context.CurrentDiagram.SelectShapes (
   anElement.GetRelatedElements<IRelationship>()
    .SelectMany(e=>e.Shapes()).ToArray());

```

 Bir öğeye bağlı tüm ilişkileri bulmak için `GetRelatedLinks<T>()` kullanın.

```
// Process all relationships connected to an element.
foreach (IRelationship relationship in
   anElement.GetRelatedLinks<IRelationship>())
{
  Debug.Assert(relationship.SourceElement == anElement
      || relationship.TargetElement == anElement);
}

```

### <a name="association"></a>Kaldırma
 Ilişki, her biri bir sınıflandırıcıya ait olan iki özellik arasındaki ilişkidir.

```
IClassifier classifier; // class, interface, component, actor, ...
// Get all the associations sourced from this classifier
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())
{
  // p represents the end further end of an association.
  IType oppositeElement = p.Type;
    // The type to which this association connects classifier

  IProperty oppositeProperty = p.Opposite;
    // The nearer end of the association.
  Debug.Assert(oppositeProperty.Type == classifier);
  IAssociation association = p.Association;
  Debug.Assert(association.MemberEnds.Contains(p)
     && association.MemberEnds.Contains(oppositeProperty));
}
```

### <a name="generalization-and-realization"></a>Genelleştirme ve gerçekleştirme
 Genelleştirme 'nin ters uçlarına erişin:

```
foreach (IClassifier supertype in classifier.Generals) {…}
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}
Access the relationship itself:
foreach (IGeneralization gen in classifier.Generalizations)
{ Debug.Assert(classifier == gen.Specific); }
```

```

/// InterfaceRealization:
IEnumerable<IInterface> GetRealizedInterfaces
    (this IBehavioredClassifier classifier);
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers
    (this IInterface interface);

```

### <a name="dependency"></a>Bağımlılık

```
/// Returns the elements depending on this element
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);
/// Returns the elements this element depends on
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);

```

### <a name="activity-edge"></a>Etkinlik kenarı

```
/// Returns the nodes targeted by edges outgoing from this one
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);
/// Returns the nodes sourcing edges incoming to this one
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);

```

### <a name="connector-assembly-and-delegation"></a>Bağlayıcı (derleme ve yetkilendirme)

```
/// Returns the elements connected via assembly
/// or delegation to this one
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);

```

### <a name="messages-and-lifelines"></a>Mesajlar ve yaşam çizgileri

```
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);
// both from lifeline and execution occurrences
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);
ILifeline GetSourceLifeline(this IMessage message);
    // may return null for found messages
ILifeline GetTargetLifeline(this IMessage message);
    // may return null for lost messages

```

### <a name="package-import"></a>Paket Içeri aktarma

```
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);

```

### <a name="use-case-extend-and-include"></a>Kullanım örneği Genişlet ve içer

```
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);
```

## <a name="enumerating-relationships"></a>Ilişkiler numaralandırılıyor
 UML modelinin birden çok değer döndüren tüm özellikleri IEnumerable < > arabirimine uygun. Bu, [LINQ sorgu ifadelerini](http://go.microsoft.com/fwlink/?LinkId=168834) ve **System. LINQ** ad alanında tanımlanan genişletme yöntemlerini kullanabileceğiniz anlamına gelir.

 Örneğin:

```
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()
where shape.Color == System.Drawing.Color.Red
select shape.Element

```

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramları GENIŞLETME](../modeling/extend-uml-models-and-diagrams.md) [UML modeline git](../modeling/navigate-the-uml-model.md)
