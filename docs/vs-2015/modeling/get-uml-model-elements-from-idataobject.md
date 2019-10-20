---
title: IDataObject 'den UML model öğelerini Al | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666086"
---
# <a name="get-uml-model-elements-from-idataobject"></a>IDataObject nesnesinden UML model öğelerini alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı herhangi bir kaynaktaki öğeleri diyagrama sürüklediğinde, sürüklenen öğeler bir `System.Windows.Forms.IDataObject` kodlanır. Kodlama, kaynak nesne türüne bağlıdır. Aşağıdaki parça, kaynak UML diyagramı olduğunda öğelerin nasıl alınacağını gösterir.

> [!NOTE]
> UML modellerinde yapmanız gereken işlemlerin çoğu, **Microsoft. VisualStudio. Uml. Interfaces** ve **Microsoft. VisualStudio. mimari Turetools. Extensibility**derlemelerinde tanımlanan türler kullanılarak gerçekleştirilebilir. Ancak bu amaçla, UML modelleme araçları uygulamasının bir parçası olan bazı sınıfları kullanmanız gerekir. Örneğin, bu parçadaki `ShapeElement` UML `IShape` aynı değildir. UML model ve diyagramlarını tutarsız bir duruma getirme riskini azaltmak için, alternatif olmadığı durumlar dışında bu uygulama sınıflarında yöntemleri kullanmaktan kaçınmak daha iyidir.

## <a name="code-sample"></a>Kod örneği
 Projeniz aşağıdaki [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] Derlemeleriyle başvurulmalıdır:

 **Microsoft. VisualStudio. model. SDK. sürümünüze**

 **Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze**

 **System. Windows. Forms**

```
using Microsoft.VisualStudio.Modeling;
  // for ElementGroupPrototype
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs
… 
  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
                  (DiagramDragEventArgs dragEvent)
  {
     //ElementGroupPrototype is the container for
     //dragged and copied elements and toolbox items.
     ElementGroupPrototype prototype =
        dragEvent.Data.
        GetData(typeof(ElementGroupPrototype))
                     as ElementGroupPrototype;
     // Locate the originals in the implementation store.
     IElementDirectory implementationDirectory =
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

     return  prototype.ProtoElements.Select(
       prototypeElement =>
       {
          ModelElement element = implementationDirectory
                .FindElement(prototypeElement.ElementId);
          ShapeElement shapeElement = element as ShapeElement;
          if (shapeElement != null)
          {
            // Dragged from a diagram.
            return shapeElement.ModelElement as IElement;
          }
          else
          {
            // Dragged from UML Model Explorer.
            return element as IElement;
          }
        });
    }
```

 @No__t_0 ve UML modelleme araçlarının uygulandığı `Store` hakkında daha fazla bilgi için bkz. [Visual Studio Için modelleme sdk-etki alanına özgü diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [UML API Ile programlama](../modeling/programming-with-the-uml-api.md) [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
