---
title: Renk, çizgi stili ve diğer şekil özelliklerini denetleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667851"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Renk, Çizgi Stili ve Diğer Şekil Özelliklerini Denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Renk gibi bazı şekil özellikleri ' açığa çıkarılan ' olabilir. Bu, şeklin bir etki alanı özelliğine bağlıdır. Diğerlerinin doğrudan denetlenmesi gerekir.

## <a name="exposing-a-property"></a>Bir özelliği gösterme
 Color gibi bazı şekil özellikleri, bir etki alanı özelliğinin değeri ile bağlantılı olabilir.

 DSL tanımında bir şekil, bağlayıcı veya Diyagram sınıfı seçin. Bağlam menüsünde, **gösterilen Ekle**' yi seçin ve ardından istediğiniz özelliği (örneğin, Fill Color) seçin.

 Artık şekil, program kodunda veya Kullanıcı olarak ayarlayabileceğiniz bir etki alanı özelliğine sahiptir.

## <a name="dynamically-updating-an-exposed-property"></a>Sunulan bir özelliği dinamik olarak güncelleştirme
 Genellikle, ortaya çıkan özelliği başka bir özelliğe bağımlı hale getirmek istersiniz. Örneğin, belirli bir etki alanı özelliği sıfırdan küçük olduğunda bir şeklin kırmızı olmasını isteyebilirsiniz. Bu bağımlılığı yapmak için bir [kural](../modeling/rules-propagate-changes-within-the-model.md)oluşturun. Örnek:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```
