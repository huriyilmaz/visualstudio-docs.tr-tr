---
title: Visual Studio API 'sini kullanarak bir UML modeli açma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668502"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Visual Studio API kullanarak UML modeli açma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ayrıca, API 'YI kullanarak Visual Studio Kullanıcı arabirimindeki modelleri ve diyagramları da açabilirsiniz.

 Yalnızca Program kodundaki bir modeli kullanıcıya görünür yapmadan okumak istiyorsanız, aşağıdaki yöntemleri kullanabilirsiniz:

- Visual Studio Model veri yolu içlerindeki modellere ve öğelere erişmenize izin verir ve bir model ile diğeri arasında bağlantı yapmak için standart bir yöntem sağlar. Daha fazla bilgi için bkz. [UML modellerini diğer modeller ve araçlarla tümleştirme](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Bir modeli salt okuma modunda açabilirsiniz. Daha fazla bilgi için bkz. [program kodunda BIR UML modeli okuma](../modeling/read-a-uml-model-in-program-code.md).

## <a name="Showing"></a>Visual Studio 'da modelleri ve diyagramları açma
 Kullanıcı arabirimindeki bir modeli açmak için standart Visual Studio API `EnvDTE.DTE` kullanın. Modelleme Proje öğelerinde gerçekleştirebileceğiniz iki kullanışlı oluşturma vardır:

- `EnvDTE.Project`, proje bir modelleme projesi ise ve proje geçerli AppDomain 'e yüklenmişse, `IModelingProject`, ve ' a dönüşebilir.

- `EnvDTE.ProjectItem`, öğe bir UML diyagramı ise `IDiagramContext` türüne veya bu kaynaktan alınabilir.

  Aşağıdaki örnekte, projenizin bu başvuruları içeri aktarması gerekir:

- EnvDTE

- Microsoft. VisualStudio. mimari Turetools. Extensibility

- Microsoft. VisualStudio. model. SDK. sürümünüze

- Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze

- Microsoft. VisualStudio. Shell. sabit. sürümünüze

- Microsoft. VisualStudio. Uml. Interfaces

- System. ComponentModel. Composition

  Bu örnek, Visual Studio 'da bir UML modeli açar:

```
using EnvDTE; // Visual Studio API for loading diagrams
using
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension and other handler types
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // for model construction methods
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
```

 Visual Studio uzantısında, ana bilgisayar hizmet sağlayıcısına erişim elde etmek için bu bildirimi yapabilirsiniz:

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 Bir yöntemde, bir projeye (örneğin, geçerli proje) erişebilirsiniz:

```
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
IModelingProject modelingProject = project as IModelingProject;
if (modelingProject == null) return; // not a modeling project

// Access the model's store and contents.
IModelStore store = modelingProject.Store;
foreach (IElement element in store.Root.OwnedElements) {...}

// Open all the project's diagrams.
foreach (ProjectItem item in project.ProjectItems)
{
     IDiagramContext modelingItem = item as IDiagramContext;
     if (modelingItem == null)
         continue; // not a model diagram
     IDiagram diagram = modelingItem.CurrentDiagram;
     if (diagram == null)
     {
        // Diagram is closed. Open it.
        item.Open().Activate();
        diagram = modelingItem.CurrentDiagram;
     }
     // Access the shapes.
     foreach (IShape<IElement> shape
               in diagram.GetChildShapes<IElement>())
     {
       IElement displayedElement = shape.Element;
       ...
     }
   }
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [UML API Ile programlama](../modeling/programming-with-the-uml-api.md) [UML modellerini ve diyagramlarını Genişlet](../modeling/extend-uml-models-and-diagrams.md)
