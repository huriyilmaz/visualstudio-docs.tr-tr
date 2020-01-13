---
title: Diyagram üzerinde UML modeli görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 12c6cecf79b0c20ea2c110efa432d5ccb9f38863
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916132"
---
# <a name="display-a-uml-model-on-diagrams"></a>Diyagramlar üzerinde model görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio uzantısı için program kodunda, model öğelerinin diyagramlarda nasıl görüntülendiğini kontrol edebilirsiniz. Hangi Visual Studio sürümlerini UML modellerini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Bu konuda:
- [Diyagramda bir öğeyi göstermek için](#Display)

- [Bir öğeyi temsil eden şekillere erişme](#GetShapes)

- [Şekilleri taşıma ve yeniden boyutlandırma](#Moving)

- [Diyagramdan bir şekli kaldırmak için](#Removing)

- [Diyagramları açma ve oluşturma](#Opening)

- [Örnek: şekilleri hizalamak için komut](#AlignCommand)

## <a name="Display"></a>Diyagramda bir öğeyi göstermek için
 Kullanım örneği veya eylem gibi bir öğe oluşturduğunuzda, Kullanıcı onu UML Model Gezgini 'nde görebilir, ancak her zaman otomatik olarak diyagramda görünmez. Bazı durumlarda, görüntülenecek kodu yazmanız gerekir. Aşağıdaki tabloda alternatifler özetlenmektedir.

|Öğe türü|Örneğin:|Bunu göstermek için, kodunuzun|
|---------------------|-----------------|-------------------------------------|
|Sınıflandırıcı|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Belirtilen diyagramlarda ilişkili şekiller oluştur. Her sınıflandırıcı için istediğiniz sayıda şekil oluşturabilirsiniz.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Diyagramın en üst düzeyindeki bir şekil için `parentShape` `null` olarak ayarlayın.<br /><br /> Bir şekli diğerinin içinde göstermek için:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Note:** bir **ılınkedundo** işlemi içinde Display yaparsanız, yöntem bazen hiçbir `IShape`döndürmez. Ancak şekil doğru şekilde oluşturulur ve `IElement.Shapes().` kullanılarak erişilebilir|
|Sınıflandırıcı alt öğesi|Öznitelik, Işlem,<br /><br /> Bölüm, bağlantı noktası|Otomatik-kod gerekmez.<br /><br /> Üst öğenin bir parçası olarak görüntülenir.|
|Davranış|Etkileşim (sıra),<br /><br /> Etkinlik|Davranışı uygun bir diyagrama bağlayın.<br /><br /> Her bir davranış, tek seferde en çok bir diyagram ile bağlanabilir.<br /><br /> Örneğin:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|
|Davranışın alt öğesi|Yaşam çizgileri, iletiler, Eylemler, nesne düğümleri|Otomatik-kod gerekmez.<br /><br /> Üst öğe bir diyagrama bağlıysa görüntülenir.|
|İlişki|İlişkilendirme, Genelleştirme, akış, bağımlılık|Otomatik-kod gerekmez.<br /><br /> Her iki ucunun de görüntülendiği her diyagramda görüntülenir.|

## <a name="GetShapes"></a>Bir öğeyi temsil eden şekillere erişme
 Bir öğeyi temsil eden şekil türlerine aittir:

 `IShape`

 `IShape<` *ElementType* `>`

 Burada *ElementType* , `IClass` veya `IUseCase`gibi model öğesinin bir türüdür.

|||
|-|-|
|`anElement.Shapes ()`|Açık diyagramlarda bu öğeyi temsil eden tüm `IShapes`.|
|`anElement.Shapes(aDiagram)`|Belirli bir diyagramda bu öğeyi temsil eden tüm `IShapes`.|
|`anIShape.GetElement()`|Şeklin temsil ettiği `IElement`. Normalde bunu IElement 'in bir alt sınıfına atamalısınız.|
|`anIShape.Diagram`|Şekli içeren `IDiagram`.|
|`anIShape.ParentShape`|`anIShape`içeren şekil. Örneğin, bir bağlantı noktası şekli bir bileşen şeklinin içinde yer alır.|
|`anIShape.ChildShapes`|Bir `IShape` veya `IDiagram`içinde bulunan şekiller.|
|`anIShape.GetChildShapes<IUseCase>()`|`IUseCase`gibi belirtilen türdeki öğeleri temsil eden bir `IShape` veya `IDiagram` içinde yer alan şekiller.|
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Genel `IShape` türü kesin belirlenmiş `IShape<IElement>`atayın.|
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Parametreli bir şekil türünden diğerine bir şekil atayın.|

## <a name="Moving"></a>Şekilleri taşıma ve yeniden boyutlandırma

|||
|-|-|
|`anIShape.Move(x, y, [width], [height])`|Bir şekli taşıyın veya yeniden boyutlandırın.|
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Pencereyi etkinleştirin ve tüm verilen şekillerin görünür olması için diyagramı kaydırın. Şekillerin hepsi diyagramda olmalıdır. `zoomToFit` true ise, tüm şekillerin görünmesi için gerekirse diyagram ölçeklendirilir.|

 Bir örnek için bkz. [Hizalama komutu tanımlama](#AlignCommand).

## <a name="Removing"></a>Diyagramdan bir şekli kaldırmak için
 Öğesi silinmeden bazı öğe türlerinin şekillerini silebilirsiniz.

|Model öğesi|Şekli kaldırmak için|
|-------------------|-------------------------|
|Sınıflandırıcı: bir sınıf, arabirim, numaralandırma, aktör, kullanım örneği veya bileşen|`shape.Delete();`|
|Davranış: etkileşim veya etkinlik|Diyagramı projeden silebilirsiniz. Yolu almak için `IDiagram.FileName` kullanın.<br /><br /> Bu, modelden davranışı silmez.|
|Diğer herhangi bir şekil|Bir diyagramdan diğer şekilleri açıkça silemezsiniz. Öğe modelden silinirse veya üst Şekil diyagramdan kaldırılırsa şekil otomatik olarak kaybolur.|

## <a name="Opening"></a>Diyagramları açma ve oluşturma

### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Kullanıcının geçerli diyagramına bir komut veya hareket uzantısı aracılığıyla erişmek için
 Bu içeri aktarılan özelliği sınıfınıza bildirin:

 `[Import]`

 `IDiagramContext Context { get; set; }`

 Bir yönteminde, diyagrama erişin:

 `IClassDiagram classDiagram =`

 `Context.CurrentDiagram as IClassDiagram;`

> [!NOTE]
> `IDiagram` bir örneği (ve `IClassDiagram`gibi alt türleri) yalnızca işlemekte olduğunuz komut içinde geçerlidir. Denetim kullanıcıya döndürülerken devam eden bir değişkende `IDiagram` bir nesne tutmanız önerilmez.

 Daha fazla bilgi için bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="to-obtain-a-list-of-open-diagrams"></a>Açık diyagramların bir listesini almak için
 Şu anda projede açık olan diyagramların listesi:

```
Context.CurrentDiagram.ModelStore.Diagrams()
```

## <a name="to-access-the-diagrams-in-a-project"></a>Bir projedeki diyagramlara erişmek için
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API 'SI, modelleme projeleri ve diyagramları açmak ve oluşturmak için kullanılabilir.

 `EnvDTE.ProjectItem` 'den `IDiagramContext`'ye dönüştürme olduğunu fark edin.

```

      using EnvDTE; // Visual Studio API
...
[Import]
public IServiceProvider ServiceProvider { get; set; }
...
// Get Visual Studio API
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;
// Get current Visual Studio project
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
// Open and process every diagram in the project.
foreach (ProjectItem item in project.ProjectItems)
{
  // Cast ProjectItem to IDiagramContext
  IDiagramContext context = item as IDiagramContext;
  if (context == null)
  {
     // This is not a diagram file.
     continue;
  }
  // Open the file and give the window the focus.
  if (!item.IsOpen)
  {
      item.Open().Activate();
  }
  // Get the diagram.
  IDiagram diagram = context.CurrentDiagram;
  // Deal with specific diagram types.
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;
  if (seqDiagram != null)
  { ... } } }
```

 Denetim [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]geri döndürbaşladıktan sonra `IDiagram` ve alt türleri örnekleri geçerli değildir.

 Ayrıca, model deposunu bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projesinden elde edebilirsiniz:

```

      Project project = ...;
IModelStore modelStore = (project as IModelingProject).Store;
```

## <a name="AlignCommand"></a>Örnek: şekilleri hizalamak için komut
 Aşağıdaki kod, şekilleri düzenli olarak hizalayan bir menü komutu uygular. Kullanıcı önce, dikey veya yatay olarak yaklaşık olarak iki veya daha fazla şekil yerleştirmelidir. Sonra, merkezlerini hizalamak için align komutu kullanılabilir.

 Komutu kullanılabilir hale getirmek için, bu kodu bir menü komut projesine ekleyin ve ardından sonuç uzantısını kullanıcılarınıza dağıtın. Daha fazla bilgi için bkz. [Modelleme Diyagramında Menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace AlignCommand
{
  // Implements a command to align shapes in a UML class diagram.
  // The user first selects shapes that are roughly aligned either vertically or horizontally.
  // This command will straighten them up.

  // Place this file in a menu command extension project.
  // See https://msdn.microsoft.com/library/ee329481.aspx

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension] // TODO: Add other diagram types if needed
  class CommandExtension : ICommandExtension
  {
    /// <summary>
    /// See https://msdn.microsoft.com/library/ee329481.aspx
    /// </summary>
    [Import]
    IDiagramContext context { get; set; }

    /// <summary>
    /// Transaction context.
    /// See https://msdn.microsoft.com/library/ee330926.aspx
    /// </summary>
    [Import]
    ILinkedUndoContext linkedUndo { get; set; }

    /// <summary>
    /// Called when the user selects the command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      Align(context.CurrentDiagram.SelectedShapes);
    }

    /// <summary>
    /// Called when the user right-clicks on the diagram.
    /// Determines whether the command is enabled.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;
      // Make it visible if there are shapes selected:
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);

      // Make it enabled if there are two or more shapes that are roughly in line:
      command.Enabled = currentSelection.Count() > 1
        && (HorizontalAlignCenter(currentSelection) > 0.0
        || VerticalAlignCenter(currentSelection) > 0.0);

    }

    /// <summary>
    /// Title of the menu command.
    /// </summary>
    public string Text
    {
      get { return "Align Shapes"; }
    }

    /// <summary>
    /// Find a horizontal line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)
    {
      double Y = -1.0;
      double top = 0.0, bottom = shapes.First().Bottom();
      foreach (IShape shape in shapes)
      {
        top = Math.Max(top, shape.Top());
        bottom = Math.Min(bottom, shape.Bottom());
      }
      if (bottom > top) Y = (bottom + top) / 2.0;
      return Y;
    }

    /// <summary>
    /// Find a vertical line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)
    {
      double X = -1.0;
      double left = 0.0, right = shapes.First().Right();
      foreach (IShape shape in shapes)
      {
        left = Math.Max(left, shape.Left());
        right = Math.Min(right, shape.Right());
      }
      if (right > left) X = (right + left) / 2.0;
      return X;
    }

    /// <summary>
    /// Line up those shapes that are roughly aligned.
    /// </summary>
    /// <param name="shapes"></param>
    private void Align(IEnumerable<IShape> shapes)
    {
      if (shapes.Count() > 1)
      {
        // The shapes must all overlap either horizontally or vertically.
        // Find a horizontal line that is covered by all the shapes:
        double Y = HorizontalAlignCenter(shapes);
        if (Y > 0.0) // Negative if they don't overlap.
        {
          // Adjust all the shape positions in one transaction:
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
          {
            foreach (IShape shape in shapes)
            {
              shape.AlignYCenter(Y);
            }
            t.Commit();
          }
        }
        else
        {
          // Find a vertical line that is covered by all the shapes:
          double X = VerticalAlignCenter(shapes);
          if (X > 0.0) // Negative if they don't overlap.
          {
            // Adjust all the shape positions in one transaction:
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
            {
              foreach (IShape shape in shapes)
              {
                shape.AlignXCenter(X);
              }
              t.Commit();
            }
          }
        }
      }
    }
  }

  /// <summary>
  /// Convenience extensions for IShape.
  /// </summary>
  public static class IShapeExtension
  {
    public static double Bottom(this IShape shape)
    {
      return shape.YPosition + shape.Height;
    }

    public static double Top(this IShape shape)
    {
      return shape.YPosition;
    }

    public static double Left(this IShape shape)
    {
      return shape.XPosition;
    }

    public static double Right(this IShape shape)
    {
      return shape.XPosition + shape.Width;
    }

    public static void AlignYCenter(this IShape shape, double Y)
    {
      shape.Move(shape.XPosition, Y - shape.YCenter());
    }

    public static void AlignXCenter(this IShape shape, double X)
    {
      shape.Move(X - shape.XCenter(), shape.YPosition);
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double YCenter(this IShape shape)
    {
        return shape.Height / 2.0;
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double XCenter(this IShape shape)
    {
        return shape.Width / 2.0;
    }
  }
}

```

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramları GENIŞLETME](../modeling/extend-uml-models-and-diagrams.md) [UML modeline git](../modeling/navigate-the-uml-model.md)
 