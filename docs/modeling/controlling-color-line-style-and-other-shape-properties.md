---
title: Renk, Çizgi Stili ve diğer Şekil Özelliklerini denetleme
description: Renk ve çizgi stili gibi şekil özelliklerini denetleme hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8f62d78e573f0fa2379fb3c36e91f0db971b8270
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061382"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Renk, Çizgi Stili ve Diğer Şekil Özelliklerini Denetleme

Renk gibi bazı şekil özellikleri 'açık' olabilir. Başka bir ifadeyle, özellikler şeklin bir etki alanı özelliğine bağlanabilirsiniz. Diğerlerinin doğrudan denetlen olması gerekir.

## <a name="exposing-a-property"></a>Bir özelliği açığa çıkararak
 Renk gibi bazı şekil özellikleri bir etki alanı özelliğinin değerine bağlanabilirsiniz.

 DSL Tanımı'da bir şekil, bağlayıcı veya diyagram sınıfı seçin. Sağ tıklama menüsünde, Açığa Çıkar **ekle'yi** seçin ve ardından Dolgu Rengi gibi istediğiniz özelliği seçin.

 Şeklin artık program kodunda veya kullanıcı olarak ayarlayabilirsiniz bir etki alanı özelliği vardır.

## <a name="dynamically-updating-an-exposed-property"></a>Açığa çıkarılmıştır bir özelliği dinamik olarak güncelleştirme
 Genellikle, açığa çıkarılacak özelliği başka bir özelle bağımlı yapmak istersiniz. Örneğin, belirli bir etki alanı özelliği sıfırdan küçük olduğunda şeklin kırmızıya dönüşecek şekilde olması iyi olabilir. Bu bağımlılığı oluşturmak için bir kural [oluşturun.](../modeling/rules-propagate-changes-within-the-model.md) Örnek:

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