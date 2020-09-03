---
title: Program kodundaki UML modelini okuma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbc55204987f4b6ea0d45c4228f6c194f1ebaf64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671303"
---
# <a name="read-a-uml-model-in-program-code"></a>Program kodundaki UML modelini okuma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML API kullanarak bir UML modeli ve diyagramlarını yükleyebilirsiniz.

## <a name="reading-a-model-in-program-code"></a><a name="Reading"></a> Program kodundaki bir modeli okuma
 Bir pencerenin bir pencerede gösterilmeksizin bir modelin içeriğine erişmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanın `ModelingProject.LoadReadOnly()` .

 Örneğin:

```
using Microsoft.VisualStudio.Uml.Classes;
               // for IElement
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
               // for ModelingProject
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
               // for IModelStore
...
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";
using (IModelingProjectReader projectReader =
           ModelingProject.LoadReadOnly(projectPath))
{
   IModelStore store = projectReader.Store;
   foreach (IClass umlClass in store.AllInstances<IClass>())
   {
       ...
   }
}
```

 Diyagramdaki şekilleri okumak istiyorsanız, projeyi ve sonra diyagramı okumanız gerekir.

 Örneğin:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
foreach (string diagramFile in projectReader. DiagramFileNames)
{
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);
  foreach (IShape<IElement> shape
         in diagram.GetChildShapes<IElement>())
  { ... }
}
```

## <a name="alternative-methods"></a>Alternatif Yöntemler
 Birçok uygulama için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus, bu konuda açıklanan yöntemlerle daha fazla sağlamlık ve esneklik ile bunların içindeki modellere ve öğelere başvurmalarını sağlar. Aynı ya da farklı modellerde rastgele öğeler arasında bağlantı oluşturmak için standart bir yöntem sağlar. Daha fazla bilgi için bkz. [UML modellerini diğer modeller ve araçlarla tümleştirme](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 API kullanarak Kullanıcı arabirimindeki modelleri ve diyagramları da açabilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Daha fazla bilgi için bkz. [Visual STUDIO API kullanarak BIR UML modeli açma](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="stand-alone-applications"></a><a name="Standalone"></a> Tek başına uygulamalar
 Önceki bölümdeki örnek, Visual Studio uzantıları 'nda çalışacaktır. Tek başına bir uygulamadaki modeli okumak mümkündür, ancak projenize bazı başvurular eklemeniz gerekir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

> [!NOTE]
> Tek başına bir uygulamadaki bir modelin nasıl okunabileceğinden ayrıntıları ürünün gelecekteki sürümlerinde değişebilir. Geçerli sürümde erişilebilen bazı özellikler gelecekteki sürümlerde kullanılamayabilir.

#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Tek başına bir uygulamadaki modeli okumak üzere başvurular eklemek için.

1. Çözüm Gezgini, uygulamayı oluşturduğunuz projeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler düzenleyicisinde, **uygulama** sekmesinde, **hedef Framework 'ü** .NET Framework gerekli sürümüne ayarlayın.

2. [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]UML modellerine erişim için gereken başvuruları ekleyin, genellikle:

   - Microsoft.VisualStudio.Uml.Interfaces.dll

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

3. Önceki bölümlerde listelenen başvurulara ek olarak, **\Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies**adresinden şu proje başvurularını ekleyin:

   - Microsoft.VisualStudio.Uml.dll

   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll

     Uygulamanızdaki diyagramları okumak istiyorsanız, bu başvuruları da isteyebilirsiniz:

   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll

## <a name="see-also"></a>Ayrıca Bkz.
 [UML API Ile programlama](../modeling/programming-with-the-uml-api.md) [UML modellerini ve diyagramlarını Genişlet](../modeling/extend-uml-models-and-diagrams.md)
