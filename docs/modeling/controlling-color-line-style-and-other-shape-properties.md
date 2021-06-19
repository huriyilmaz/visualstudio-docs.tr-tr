---
title: Renk, Çizgi Stili ve diğer Şekil Özelliklerini denetleme
description: Renk ve çizgi stili gibi şekil özelliklerini denetleme hakkında bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 836c77f3651b7686e9366fe75ea7922a248fd28f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389637"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Renk, Çizgi Stili ve Diğer Şekil Özelliklerini Denetleme

Renk gibi bazı şekil özellikleri 'açık' olabilir. Başka bir ifadeyle, özellikler şeklin bir etki alanı özelliğine bağlanabilirsiniz. Diğerlerinin doğrudan denetlen olması gerekir.

## <a name="exposing-a-property"></a>Bir özelliği açığa çıkararak
 Renk gibi bazı şekil özellikleri bir etki alanı özelliğinin değerine bağlı olabilir.

 DSL Tanımı'da bir şekil, bağlayıcı veya diyagram sınıfı seçin. Sağ tıklama menüsünde, Açığa Çıkar **ekle'yi** ve ardından Dolgu Rengi gibi istediğiniz özelliği seçin.

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