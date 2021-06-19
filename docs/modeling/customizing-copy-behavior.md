---
title: Kopyalama Davranışını Özelleştirme
description: Visual Studio Görselleştirme ve Modelleme SDK'sı ile oluşturulan bir DSL'de, kullanıcı öğeleri kopyalayıp yapıştırıyorsa ne olacağını değiştirebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2e5ffbc7dde0bd1274756d1721088b18ea6ec34
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389416"
---
# <a name="customizing-copy-behavior"></a>Kopyalama Davranışını Özelleştirme
Visual Studio Görselleştirme ve Modelleme SDK'sı ile oluşturulan etki alanına özgü bir dilde (DSL), kullanıcı öğeleri kopyalayıp yapıştırıyorsa ne olacağını değiştirebilirsiniz.

## <a name="standard-copy-and-paste-behavior"></a>Standart Kopyalama ve Yapıştırma Davranışı
 Kopyalamayı etkinleştirmek için DSL **Gezgini'nde Düzenleyici düğümünün** **Kopyala** Yapıştır özelliğini etkinleştirin.

 Varsayılan olarak, kullanıcı öğeleri panoya kopyalayarak aşağıdaki öğeler de kopyalanır:

- Seçili öğelerin katıştırılmış alt öğeleri. (Yani, kopyalanan öğelerde kaynaklanan ekleme ilişkilerinin hedefleri olan öğeler.)

- Kopyalanan öğeler arasındaki ilişki bağlantıları.

  Bu kural kopyalanan öğelere ve bağlantılara tekrar tekrar uygulanır.

  ![Kopyalanan ve yapıştıran öğeler](../modeling/media/dslcopypastedefault.png)

  Kopyalanan öğeler ve bağlantılar seri hale getirilecek ve panoya yerleştirilen <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> bir (EGP) içinde depolanır.

  Kopyalanan öğelerin bir görüntüsü de panoya yerleştirilir. Bu, kullanıcının Word gibi diğer uygulamalara yapıştırmalarına olanak sağlar.

  Kullanıcı, kopyalanan öğeleri DSL Tanımına göre kabul eden bir hedefe yapıştırılabilir. Örneğin, bileşen çözümü şablonundan oluşturulan bir DSL'de kullanıcı bağlantı noktalarını bileşenlere yapıştırabilirsiniz ancak diyagrama yapıştırabilirsiniz; ve bileşenleri diyagrama yapıştırabilirsiniz, ancak diğer bileşenlere yapıştırabilirsiniz.

## <a name="customizing-copy-and-paste-behavior"></a>Kopyalama ve Yapıştırma Davranışını Özelleştirme
 Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. Program Kodunda [Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

 **Kopyalama, kesme ve yapıştırmayı etkinleştirme veya devre dışı bırakma.**
DSL Gezgini'nde Düzenleyici **düğümünün Kopyala Yapıştır** özelliğini **etkinleştirin.**

 **Bağlantıları aynı hedefe kopyalayın.** Örneğin, kopyalanan bir açıklama kutusunun aynı konu öğesine bağlı olması.
Rolün **Yayma Kopyalama özelliğini** Yalnızca bağlantısına kopyala olarak **ayarlayın.** Daha fazla bilgi için [bkz. Bağlantı Kopyalama Davranışını Özelleştirme.](#customizeLinks)

 Bağlantılı öğeleri kopyalayın. Örneğin, yeni bir öğeyi kopyalayıp bağlantılı açıklama kutularının kopyaları da yapılır.
Rolün **Yayma Kopyalama özelliğini,** kopyalamayı bağlantıya yay ve karşıt rol **oynatıcısı olarak ayarlayın.** Daha fazla bilgi için [bkz. Bağlantı Kopyalama Davranışını Özelleştirme.](#customizeLinks)

 **Öğeleri kopyalayıp yapıştırarak hızla yineler.** Normalde, az önce kopyalanan öğe seçili durumdadır ve öğeye aynı öğe türünü yapıştıramazsiniz.
Etki alanı sınıfına bir Öğe Birleştirme Yönergesi ekleyin ve birleştirmeleri üst sınıfa iletilecek şekilde ayarlayın. Bu, sürükleme işlemleri üzerinde de aynı etkiye sahip olur. Daha fazla bilgi için [bkz. Öğe Oluşturma ve Taşımayı Özelleştirme.](../modeling/customizing-element-creation-and-movement.md)

 \- veya -

 Öğeleri yapıştırarak, öğesini geçersiz kılmadan önce diyagramı `ClipboardCommandSet.ProcessOnPasteCommand()` seçin. DslPackage projesinde bu kodu özel bir dosyaya ekleyin:

```csharp
namespace Company.MyDsl {
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
partial class MyDslClipboardCommandSet
{
  protected override void ProcessOnMenuPasteCommand()
  {
 // Deselect the current selection after copying:
 Diagram diagram = (this.CurrentModelingDocView as SingleDiagramDocView).Diagram;
    this.CurrentModelingDocView
     .SelectObjects(1, new object[] { diagram }, 0);
  }
} }
```

 **Kullanıcı seçili bir hedefe yapıştırıyorken ek bağlantılar oluşturun.** Örneğin, bir öğeye bir açıklama kutusu yapıştırıldıkları zaman, aralarında bir bağlantı yapılır.
Hedef etki alanı sınıfına bir Öğe Birleştirme Yönergesi ekleyin ve bağlantıları ekleyerek birleştirme işlemini işley için ayarlayın. Bu, sürükleme işlemleri üzerinde de aynı etkiye sahip olur. Daha fazla bilgi için [bkz. Öğe Oluşturma ve Taşımayı Özelleştirme.](../modeling/customizing-element-creation-and-movement.md)

 \- veya -

 Temel `ClipboardCommandSet.ProcessOnPasteCommand()` yöntem çağrıldikten sonra ek bağlantıları oluşturmak için geçersiz kılın.

 **Öğelerin dış uygulamalara kopyalandırılma** biçimlerini özelleştirin; örneğin bit eşlem formuna kenarlık eklemek için.
DslPackage *projesinde* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` MyDsl'i geçersiz kılın.

 **Öğelerin kopyalama komutuyla panoya nasıl kopyalanır, ancak sürüklenme işlemi içinde nasıl kopyalanmaysa da özelleştirin.**
DslPackage *projesinde* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` MyDsl'i geçersiz kılın.

 **Kopyala ve yapıştır aracılığıyla şekil düzenini koruma.**
Kullanıcı birden çok şekil kopyalasa, yapıştırıldıklarında göreli konumlarını koruyabilirsiniz. Bu teknik, [VMSDK: Bağlantı Hattı Diyagramları örneği' örneğinde gösterildiği gibi.](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

 Bu etkiyi elde etmek için kopyalanan ElementGroupPrototype öğesine şekilleri ve bağlayıcıları ekleyin. Geçersiz kılmanın en kullanışlı yöntemi ElementOperations.CreateElementGroupPrototype() yöntemidir. Bunu yapmak için Dsl projesine aşağıdaki kodu ekleyin:

```csharp

public class MyElementOperations : DesignSurfaceElementOperations
{
  // Create an EGP to add to the clipboard.
  // Called when the elements to be copied have been
  // collected into an ElementGroup.
 protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
  {
 // Add the shapes and connectors:
 // Get the elements already in the group:
    ModelElement[] mels = elementGroup.ModelElements
        .Concat(elementGroup.ElementLinks) // Omit if the paste target is not the diagram.
        .ToArray();
 // Get their shapes:
    IEnumerable<PresentationElement> shapes =
       mels.SelectMany(mel =>
            PresentationViewsSubject.GetPresentation(mel));
    elementGroup.AddRange(shapes);

 return base.CreateElementGroupPrototype
           (elementGroup, elements, closureType);
  }

 public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
  { }
}

// Replace the standard ElementOperations
// singleton with your own:
partial class MyDslDiagram // EDIT NAME
{
 /// <summary>
 /// Singleton ElementOperations attached to this diagram.
 /// </summary>
 public override DesignSurfaceElementOperations ElementOperations
  {
 get
    {
 if (singleton == null)
      {
        singleton = new MyElementOperations(this.Store as IServiceProvider, this);
      }
 return singleton;
    }
  }
 private MyElementOperations singleton = null;
}
```

 **Şekilleri, geçerli imleç konumu gibi seçili bir konuma yapıştırın.**
Kullanıcı birden çok şekil kopyalasa, yapıştırıldıklarında göreli konumlarını koruyabilirsiniz. Bu teknik, [VMSDK: Bağlantı Hattı Diyagramları örneği' örneğinde gösterildiği gibi.](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

 Bu etkiyi elde etmek için, `ClipboardCommandSet.ProcessOnMenuPasteCommand()` konumunun konuma özgü sürümünü kullanmak üzere geçersiz `ElementOperations.Merge()` kılın. Bunu yapmak için DslPackage projesine aşağıdaki kodu ekleyin:

```csharp

partial class MyDslClipboardCommandSet // EDIT NAME
{
   /// <summary>
    /// This method assumes we only want to paste things onto the diagram
    /// - not onto anything contained in the diagram.
    /// The base method pastes in a free space on the diagram.
    /// But if the menu was used to invoke paste, we want to paste in the cursor position.
    /// </summary>
    protected override void ProcessOnMenuPasteCommand()
    {

  NestedShapesSampleDocView docView = this.CurrentModelingDocView as NestedShapesSampleDocView;

      // Retrieve data from clipboard:
      System.Windows.Forms.IDataObject data = System.Windows.Forms.Clipboard.GetDataObject();

      Diagram diagram = docView.CurrentDiagram;
      if (diagram == null) return;

      if (!docView.IsContextMenuShowing)
      {
        // User hit CTRL+V - just use base method.

        // Deselect anything that's selected, otherwise
        // pasted item will be incompatible:
        if (!this.IsDiagramSelected())
        {
          docView.SelectObjects(1, new object[] { diagram }, 0);
        }

        // Paste into a convenient spare space on diagram:
    base.ProcessOnMenuPasteCommand();
      }
      else
      {
        // User right-clicked - paste at mouse position.

        // Utility class:
        DesignSurfaceElementOperations op = diagram.ElementOperations;

        ShapeElement pasteTarget = diagram;

        // Check whether what's in the paste buffer is acceptable on the target.
        if (pasteTarget != null && op.CanMerge(pasteTarget, data))
        {

        // Although op.Merge would be a no-op if CanMerge failed, we check CanMerge first
          // so that we don't create an empty transaction (after which Undo would be no-op).
          using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("paste"))
          {
            PointD place = docView.ContextMenuMousePosition;
            op.Merge(pasteTarget, data, PointD.ToPointF(place));
            t.Commit();
          }
        }
      }
    }
  }
```

 **Kullanıcının öğeleri sürükleyip bırakmasına izin ver.**
Bkz. [Nasıl: Sürükle ve Bırak İşleyicisi Ekleme.](../modeling/how-to-add-a-drag-and-drop-handler.md)

## <a name="customizing-link-copy-behavior"></a><a name="customizeLinks"></a> Bağlantı Kopyalama Davranışını Özelleştirme
 Kullanıcı bir öğeyi kopyalasa, standart davranış tüm ekli öğelerin de kopyalanmış olmasıdır. Standart kopyalama davranışını değiştirebilirsiniz. DSL Tanımı'nda, ilişkinin bir tarafındaki rolü seçin ve Özellikler penceresi **Yay değerini** ayarlayın.

 ![Etki alanı rolünün Copy özelliğini yayın](../modeling/media/dslpropagatescopy.png)

 Üç değer vardır:

- Kopyalamayı yayma

- Kopyalamayı yalnızca bağlantıya yay - Grup yapıştırıldıksa, bu bağlantının yeni kopyası bağlantının diğer ucundaki mevcut öğeye başvurur.

- Bağlantıyı kopyalamayı ve karşıt rol oynatıcısını yay - kopyalanan grup, bağlantının diğer ucunda öğenin bir kopyasını içerir.

  ![PropagateCopyToLinkOnly ile kopyalamanın etkisi](../modeling/media/dslpropagatecopy.png)

  Yaptığınız değişiklikler hem öğeleri hem de kopyalanan görüntüyü etkiler.

## <a name="programming-copy-and-paste-behavior"></a>Programlama Kopyalama ve Yapıştırma Davranışı
 DSL'nin nesne kopyalama, yapıştırma, oluşturma ve silme ile ilgili davranışının birçok yönü diyagramla bir bağlantısı olan örneği <xref:Microsoft.VisualStudio.Modeling.ElementOperations> tarafından yönetilir. Kendi sınıfını türeterek ve diyagram sınıfınıza ait özelliğini geçersiz karak <xref:Microsoft.VisualStudio.Modeling.ElementOperations> <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> DSL'nizin davranışını değiştirebilirsiniz.

> [!TIP]
> Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. Program Kodunda [Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

 ![Kopyalama işlemi için sıra diyagramı](../modeling/media/dslcopyseqdiagram.png)

 ![Yapıştırma işlemi dizisi diyagramı](../modeling/media/dslpasteseqdiagram.png)

#### <a name="to-define-your-own-elementoperations"></a>Kendi ElementOperations'larınızı tanımlamak için

1. DSL projenizin yeni dosyasından türetilen bir sınıf <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations> oluşturun.

2. Diyagram sınıfınız için kısmi bir sınıf tanımı ekleyin. Bu sınıfın adı **Dsl\GeneratedCode\Diagrams.cs konumunda bulunabilir.**

    Diyagram  <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> sınıfında, ElementOperations alt sınıfı örneğinizi geri dönmek için geçersiz kılın. Her çağrıda aynı örneği geri dönmelisiniz.

   Bu kodu DslPackage projesinde özel bir kod dosyasına ekleyin:

```csharp

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;

  public partial class MyDslDiagram
  {
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, MyDslDiagram diagram)
      : base(serviceProvider, diagram)
    { }
    // Overridden methods follow
  }
```

## <a name="receiving-items-dragged-from-other-models"></a>Diğer modellerden sürüklenen öğeleri alma
 ElementOperations kopyalama, taşıma, silme ve sürükleyip bırakma davranışını tanımlamak için de kullanılabilir. ElementOperations kullanımının bir gösterimi olarak, burada verilen örnek özel sürükle ve bırak davranışını tanımlar. Ancak bu amaçla, Daha genişletilebilir olan Sürükle [ve](../modeling/how-to-add-a-drag-and-drop-handler.md)Bırak İşleyicisi Ekleme konusunda açıklanan alternatif yaklaşımı göz önünde bulunduramazsınız.

 ElementOperations sınıfınıza iki yöntem tanımlayın:

- `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)` kaynak öğenin hedef şekle, bağlayıcıya veya diyagrama sürüklenip sürüklenemediğini belirler.

- `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)` , kaynak öğeyi hedefte birleştirir.

### <a name="canmerge"></a>CanMerge()
 `CanMerge()` , kullanıcıya fare diyagramda hareket etti olarak verilmesi gereken geri bildirimi belirlemek için çağrılır. yöntemine yönelik parametreler, farenin üzerine gelinen öğe ve sürükleme işlemi gerçekleştirilen kaynakla ilgili verilerdir. Kullanıcı, ekranın herhangi bir yerinden sürükleyebilirsiniz. Bu nedenle, kaynak nesne birçok farklı türde olabilir ve farklı biçimlerde seri hale getirilebilir. Kaynak bir DSL veya UML modeli ise veri parametresi bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> serileştirmedir. Sürükleme, kopyalama ve araç kutusu işlemleri, model parçalarını temsil etmek için ElementGroupPrototypes kullanır.

 Bir Öğe Grubu Prototipi herhangi bir sayıda öğe ve bağlantı içerebilir. Öğe türleri GUID'leri tarafından belirlenebilirsiniz. GUID, temel alınan model öğesi değil sürüklenen şekildedir. Aşağıdaki örnekte, `CanMerge()` UML diyagramından bir sınıf şekli bu diyagrama sürüklenmişse true döndürür.

```csharp
public override bool CanMerge(ModelElement targetShape, System.Windows.Forms.IDataObject data)
 {
  // Extract the element prototype from the data.
  ElementGroupPrototype prototype = ElementOperations.GetElementGroupPrototype(this.ServiceProvider, data);
  if (targetShape is MyTargetShape && prototype != null &&
        prototype.RootProtoElements.Any(rootElement =>
          rootElement.DomainClassId.ToString()
          ==  "3866d10c-cc4e-438b-b46f-bb24380e1678")) // Guid of UML Class shapes
          // or SourceClass.DomainClassId
        return true;
   return base.CanMerge(targetShape, data);
 }
```

## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype()
 Kullanıcı bir öğeyi diyagrama, şekle veya bağlayıcıya düşürünca bu yöntem çağrılır. Sürüklenen içeriği hedef öğede birleştirmesi gerekir. Bu örnekte kod, hedef ve prototip türlerinin birleşimini tanıyıp tanımadığını belirler; öyleyse, yöntemi sürüklenen öğeleri modele eklenecek öğelerin bir prototipi içine dönüştürür. Temel yöntem, dönüştürülmüş veya dönüştürülemeyen öğelerden birini birleştirmeyi gerçekleştirmek için çağrılır.

```csharp
public override void MergeElementGroupPrototype(ModelElement targetShape, ElementGroupPrototype sourcePrototype)
{
  ElementGroupPrototype prototypeToMerge = sourcePrototype;
  MyTargetShape pel = targetShape as MyTargetShape;
  if (pel != null)
  {
    prototypeToMerge = ConvertDraggedTypeToLocal(pel, sourcePrototype);
  }
  if (prototypeToMerge != null)
    base.MergeElementGroupPrototype(targetShape, prototypeToMerge);
}
```

 Bu örnek, UML sınıf diyagramından sürüklenen UML sınıf öğeleriyle ilgilidir. DSL, UML sınıflarını doğrudan depolamak için tasarlanmamıştır, ancak bunun yerine sürüklenen her UML sınıfı için bir DSL öğesi oluşturabilirsiniz. Bu, örneğin DSL bir örnek diyagramı ise yararlı olacaktır. Kullanıcı, bu sınıfların örneklerini oluşturmak için sınıfları diyagrama sürükleyebilirsiniz.

```csharp

private ElementGroupPrototype ConvertDraggedTypeToLocal (MyTargetShape snapshot, ElementGroupPrototype prototype)
{
  // Find the UML project:
  EnvDTE.DTE dte = snapshot.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
  foreach (EnvDTE.Project project in dte.Solution.Projects)
  {
    IModelingProject modelingProject = project as IModelingProject;
    if (modelingProject == null) continue; // not a modeling project
    IModelStore store = modelingProject.Store;
    if (store == null) continue;
    // Look for the shape that was dragged:
    foreach (IDiagram umlDiagram in store.Diagrams())
    {
      // Get modeling diagram that implements UML diagram:
      Diagram diagram = umlDiagram.GetObject<Diagram>();
      Guid elementId = prototype.SourceRootElementIds.FirstOrDefault();
      ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
      if (shape == null) continue;
      IClass classElement = shape.ModelElement as IClass;
      if (classElement == null) continue;

      // Create a prototype of elements in my DSL, based on the UML element:
      Instance instance = new Instance(snapshot.Store);
      instance.Type = classElement.Name;
      // Pack them into a prototype:
      ElementGroup group = new ElementGroup(instance);
      return group.CreatePrototype();
    }
  }
  return null;
}
```

## <a name="standard-copy-behavior"></a>Standart Kopyalama Davranışı
 Bu bölümdeki kod, kopyalama davranışını değiştirmek için geçersiz kılabilirsiniz yöntemleri gösterir. Kendi özelleştirmelerinizi nasıl elde etmek istediğinize yardımcı olmak için bu bölümde kopyalamayla ilgili yöntemleri geçersiz k kullanılan ancak standart davranışı değiştirmeyen kodlar yer almaktadır.

 Kullanıcı CTRL+C tuşlarına bassa veya Kopyala menü komutunu kullandığında <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> yöntemi çağrılır. Bunun **DslPackage\Generated Code\CommandSet.cs** konumunda nasıl ayar olduğunu görüyorsunuz. Komutların nasıl ayar olduğu hakkında daha fazla bilgi için [bkz. Nasıl kullanılır: Kısayol Menüsüne Komut Ekleme.](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

 DslPackage projesine *MyDsl'nin* kısmi sınıf tanımını ekleyerek ProcessOnMenuCopyCommand'i `ClipboardCommandSet` geçersiz kılılabilir.

```csharp
using System.Collections.Generic;
using System.Drawing;
using System.Windows.Forms;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

partial class MyDslClipboardCommandSet
{
  /// <summary>
  /// Override ProcessOnMenuCopyCommand() to copy elements to the
  /// clipboard in different formats, or to perform additional tasks
  /// before or after copying - for example deselect the copied elements.
  /// </summary>
  protected override void ProcessOnMenuCopyCommand()
  {
    IList<ModelElement> selectedModelElements = this.SelectedElements;
    if (selectedModelElements.Count == 0) return;

    // System container for clipboard data.
    // The IDataObject can contain data in several formats.
    IDataObject dataObject = new DataObject();

    Bitmap bitmap = null; // For export to other programs.
    try
    {
      #region Create EGP for copying to a DSL.
      this.CopyModelElementsIntoElementGroupPrototype
                     (dataObject, selectedModelElements);
      #endregion

      #region Create bitmap for copying to another application.
      // Find all the shapes associated with this selection:
      List<ShapeElement> shapes = new List<ShapeElement>(
        this.ResolveExportedShapesForClipboardImages
              (dataObject, selectedModelElements));

      bitmap = this.CreateBitmapForClipboard(shapes);
      if (bitmap != null)
      {
        dataObject.SetData(DataFormats.Bitmap, bitmap);
      }
      #endregion

      // Add the data to the clipboard:
      Clipboard.SetDataObject(dataObject, true, 5, 100);
    }
    finally
    {
      // Dispose bitmap after SetDataObject:
      if (bitmap != null) bitmap.Dispose();
    }
  }
/// <summary>
/// Override this to customize the element group that is copied to the clipboard.
/// </summary>
protected override void CopyModelElementsIntoElementGroupPrototype(IDataObject dataObject, IList<ModelElement> selectedModelElements)
{
  return this.ElementOperations.Copy(dataObject, selectedModelElements);
}
}
```

 Her diyagramda ElementOperations'ın tek bir örneği vardır. Kendi türevini de s tedariki de SSS'ye 2019'da da 2 DSL projesine yer açılabilir bu dosya, geçersiz kılabilir kodla aynı şekilde davranır:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace Company.MyDsl
{
  partial class MyDslDiagram
  {
    /// <summary>
    /// Singleton ElementOperations attached to this diagram.
    /// </summary>
    public override DesignSurfaceElementOperations ElementOperations
    {
      get
      {
        if (this.elementOperations == null)
        {
          this.elementOperations = new MyElementOperations(this.Store as IServiceProvider, this);
        }
        return this.elementOperations;
      }
    }
    private MyElementOperations elementOperations = null;
  }

  // Our own version of ElementOperations so that we can override:
  public class MyElementOperations : DesignSurfaceElementOperations
  {
    public MyElementOperations(IServiceProvider serviceProvider, ElementOps1Diagram diagram)
      : base(serviceProvider, diagram)
    { }

    /// <summary>
    /// Copy elements to the clipboard data.
    /// Provides a hook for adding custom data.
    /// </summary>
    public override void Copy(System.Windows.Forms.IDataObject data,
      ICollection<ModelElement> elements,
      ClosureType closureType,
      System.Drawing.PointF sourcePosition)
    {
      if (CanAddElementGroupFormat(elements, closureType))
      {
        AddElementGroupFormat(data, elements, closureType);
      }

      // Override these to store additional data:
      if (CanAddCustomFormat(elements, closureType))
      {
        AddCustomFormat(data, elements, closureType, sourcePosition);
      }
    }

    protected override void AddElementGroupFormat(System.Windows.Forms.IDataObject data, ICollection<ModelElement> elements, ClosureType closureType)
    {
      // Add the selected elements and those implied by the propagate copy rules:
      ElementGroup elementGroup = this.CreateElementGroup(elements, closureType);

      // Mark all the elements that are not embedded under other elements:
      this.MarkRootElements(elementGroup, elements, closureType);

      // Store in the clipboard data:
      ElementGroupPrototype elementGroupPrototype = this.CreateElementGroupPrototype(elementGroup, elements, closureType);
      data.SetData(ElementGroupPrototype.DefaultDataFormatName, elementGroupPrototype);
    }

    /// <summary>
    /// Override this to store additional elements in the element group:
    /// </summary>
    protected override ElementGroupPrototype CreateElementGroupPrototype(ElementGroup elementGroup, ICollection<ModelElement> elements, ClosureType closureType)
    {
      ElementGroupPrototype prototype = new ElementGroupPrototype(this.Partition, elementGroup.RootElements, elementGroup);
      return prototype;
    }

    /// <summary>
    /// Create an element group from the given starting elements, using the
    /// copy propagation rules specified in the DSL Definition.
    /// By default, this includes all the embedded descendants of the starting elements,
    /// and also includes reference links where both ends are already included.
    /// </summary>
    /// <param name="startElements">model elements to copy</param>
    /// <param name="closureType"></param>
    /// <returns></returns>
    protected override ElementGroup CreateElementGroup(ICollection<ModelElement> startElements, ClosureType closureType)
    {
      // ElementClosureWalker finds all the connected elements,
      // according to the propagate copy rules specified in the DSL Definition:
      ElementClosureWalker walker = new ElementClosureWalker(this.Partition,
        closureType, // Normally ClosureType.CopyClosure
        startElements,
        true, // Do not load other models.
        null, // Optional list of domain roles not to traverse.
        true); // Include relationship links where both ends are already included.

      walker.Traverse(startElements);
      IList<ModelElement> closureList = walker.ClosureList;
      Dictionary<object, object> closureContext = walker.Context;

      // create a group for this closure
      ElementGroup group = new ElementGroup(this.Partition);
      group.AddRange(closureList, false);

      // create the element group prototype for the group
      foreach (object key in closureContext.Keys)
      {
        group.SourceContext.ContextInfo[key] = closureContext[key];
      }

      return group;
    }
  }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Öğe Oluşturma ve Hareketini Özelleştirme](../modeling/customizing-element-creation-and-movement.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Örnek: VMSDK Bağlantı Hattı Diyagramları örneği](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
