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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666086"
---
# <a name="get-uml-model-elements-from-idataobject"></a>IDataObject nesnesinden UML model öğelerini alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıcı herhangi bir kaynaktaki öğeleri diyagram üzerine sürüklediğinde, sürüklenen öğeler bir olarak kodlanır `System.Windows.Forms.IDataObject` . Kodlama, kaynak nesne türüne bağlıdır. Aşağıdaki parça, kaynak UML diyagramı olduğunda öğelerin nasıl alınacağını gösterir.

> [!NOTE]
> UML modellerinde yapmanız gereken işlemlerin çoğu, **Microsoft. VisualStudio. Uml. Interfaces** ve **Microsoft. VisualStudio. mimari Turetools. Extensibility**derlemelerinde tanımlanan türler kullanılarak gerçekleştirilebilir. Ancak bu amaçla, UML modelleme araçları uygulamasının bir parçası olan bazı sınıfları kullanmanız gerekir. Örneğin, `ShapeElement` Bu parçada UML ile aynı değildir `IShape` . UML model ve diyagramlarını tutarsız bir duruma getirme riskini azaltmak için, alternatif olmadığı durumlar dışında bu uygulama sınıflarında yöntemleri kullanmaktan kaçınmak daha iyidir.

## <a name="code-sample"></a>Kod örneği
 Projenizin aşağıdaki derlemelere başvurması gerekir [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] :

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

 `ElementGroupPrototype`Ve UML modelleme araçlarının uygulandığı hakkında daha fazla bilgi için `Store` bkz. [Visual STUDIO için modelleme sdk-etki alanına özgü diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [UML API Ile programlama](../modeling/programming-with-the-uml-api.md) [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
