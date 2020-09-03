---
title: Öğe araçlarını özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655019"
---
# <a name="customizing-element-tools"></a>Öğe Araçlarını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bazı DSL tanımlarında, tek bir kavramı öğe grubu olarak temsil edersiniz. Örneğin, bir bileşenin sabit bir bağlantı noktası kümesine sahip olduğu bir model oluşturursanız, her zaman bağlantı noktalarının üst bileşenleri ile aynı zamanda oluşturulmasını istersiniz. Bu nedenle, öğe oluşturma aracını yalnızca bir tane yerine bir öğe grubu oluşturacak şekilde özelleştirmeniz gerekir. Bunu başarmak için, öğe oluşturma aracının nasıl başlatıldığını özelleştirebilirsiniz.

 Ayrıca araç diyagrama veya bir öğeye sürüklendiğinde ne olacağını geçersiz kılabilirsiniz.

## <a name="customizing-the-content-of-an-element-tool"></a>Öğe aracının Içeriğini özelleştirme
 Her öğe aracı bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> veya daha fazla model öğesi ve bağlantısının serileştirilmiş bir sürümünü içeren bir (EGP) örneğini depolar. Varsayılan olarak, bir öğe aracının EGP 'si, araç için belirttiğiniz sınıfın bir örneğini içerir. Bunu, dilini geçersiz kılarak değiştirebilirsiniz *YourLanguage* `ToolboxHelper.CreateElementToolPrototype` . Bu yöntem DSL paketi yüklendiğinde çağrılır.

 Yöntemin parametresi, DSL tanımında belirttiğiniz sınıfın KIMLIĞIDIR. Yöntemi ilgilendiğiniz sınıfla çağrıldığında, EGP içine ek öğeler ekleyebilirsiniz.

 EGP, bir ana öğeden yan öğe öğelerine ekleme bağlantıları içermelidir. Ayrıca, başvuru bağlantıları da içerebilir.

 Aşağıdaki örnek, bir ana öğe ve iki Embedded öğesi oluşturur. Ana sınıfa Direntor adı verilir ve Terminal adlı öğelere iki katıştırma ilişkisi vardır. Ekleme rolü özellikleri terminal1 ve terminal2 olarak adlandırılır ve her ikisi de 1.. 1 çokluğuna sahiptir.

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Öğe Oluşturma ve Hareketini Özelleştirme](../modeling/customizing-element-creation-and-movement.md)
