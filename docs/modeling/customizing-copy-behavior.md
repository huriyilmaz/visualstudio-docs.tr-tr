---
title: Kopyalama Davranışını Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcbe7a132f7e2f6f7d72cfd2ba210e5edba21b57
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654091"
---
# <a name="customizing-copy-behavior"></a>Kopyalama Davranışını Özelleştirme
Visual Studio görselleştirme ve modelleme SDK 'Sı ile oluşturulan, etki alanına özgü bir dilde (DSL), kullanıcı öğeleri kopyaladığında ve yapıştırdığında ne olacağını değiştirebilirsiniz.

## <a name="standard-copy-and-paste-behavior"></a>Standart kopyalama ve yapıştırma davranışı
 Kopyalamayı etkinleştirmek için, DSL Gezgini 'ndeki **Düzenleyici** düğümünün **kopyalama Yapıştır özelliğini etkinleştir** ' i ayarlayın.

 Varsayılan olarak, kullanıcı öğeleri panoya kopyaladığında aşağıdaki öğeler de kopyalanır:

- Seçili öğelerin gömülü alt öğeleri. (Diğer bir deyişle, kopyalanmış öğelerde kaynak olan ilişkiler katıştırma hedefi olan öğeler.)

- Kopyalanmış öğeler arasındaki ilişki bağlantıları.

  Bu kural, kopyalanmış öğeler ve bağlantılara yinelemeli olarak uygulanır.

  ![Kopyalanmış ve yapıştırılan öğeler](../modeling/media/dslcopypastedefault.png)

  Kopyalanmış öğeler ve bağlantılar, panoya yerleştirilmiş bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP) olarak serileştirilir ve saklanır.

  Kopyalanmış öğelerin bir görüntüsü de Pano 'ya yerleştirilir. Bu, kullanıcının Word gibi başka uygulamalara yapıştırmasına olanak tanır.

  Kullanıcı, kopyalanmış öğeleri DSL tanımına göre öğeleri kabul edebilecek bir hedefe yapıştırabilir. Örneğin, bileşenler çözüm şablonundan oluşturulan bir DSL 'de, Kullanıcı, bağlantı noktalarını bileşenlere yapıştıramazsınız, ancak diyagram üzerine yapıştırabilir; ve bileşenleri diyagrama kopyalayabilir, ancak diğer bileşenlere yapıştıramazsınız.

## <a name="customizing-copy-and-paste-behavior"></a>Kopyalama ve yapıştırma davranışını özelleştirme
 Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

 **Kopyalama, kesme ve yapıştırmayı etkinleştirin veya devre dışı bırakın.**
DSL Gezgini ' nde **Düzenleyici** düğümünün **kopyalama Yapıştır özelliğini etkinleştir** ' i ayarlayın.

 **Bağlantıları aynı hedefe kopyalayın.** Örneğin, aynı konu öğesine bağlanmış bir kopyalanmış yorum kutusu eklemek için.
Rolü **yalnızca bağlantıya yaymak**Için rolün **yayan Copy** özelliğini ayarlayın. Daha fazla bilgi için bkz. [bağlantı kopyalama davranışını özelleştirme](#customizeLinks).

 Bağlantılı öğeleri kopyala. Örneğin, yeni bir öğesi kopyaladığınızda, bağlantılı açıklama kutularının kopyaları da yapılır.
**Kopyayı bağlantı ve karşıt rol oyuncusuna yaymak**Için rolün **yayan Copy** özelliğini ayarlayın. Daha fazla bilgi için bkz. [bağlantı kopyalama davranışını özelleştirme](#customizeLinks).

 **Öğeleri kopyalayıp yapıştırarak hızla çoğaltın.** Normal olarak, yeni kopyaladığınız öğe hala seçilidir ve aynı öğe türünü üzerine yapıştıramazsınız.
Etki alanı sınıfına bir öğe birleştirme yönergesi ekleyin ve birleştirme Işlemini üst sınıfa ilet olarak ayarlayın. Bu, sürükleme işlemlerinde aynı etkiye sahip olacaktır. Daha fazla bilgi için bkz. [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).

 \- veya-

 @No__t_0 geçersiz kılarak öğeleri yapıştırmadan önce diyagramı seçin. Bu kodu DslPackage projesindeki özel bir dosyaya ekleyin:

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

 **Kullanıcı seçili bir hedefi üzerine yapıştırdığı zaman ek bağlantılar oluştur.** Örneğin, bir açıklama kutusu bir öğeye yapıştırıldığında aralarında bir bağlantı yapılır.
Hedef etki alanı sınıfına bir öğe birleştirme yönergesi ekleyin ve bağlantı ekleyerek birleştirme işlemini işleyecek şekilde ayarlayın. Bu, sürükleme işlemlerinde aynı etkiye sahip olacaktır. Daha fazla bilgi için bkz. [öğe oluşturma ve hareketini özelleştirme](../modeling/customizing-element-creation-and-movement.md).

 \- veya-

 Temel yöntemi çağırdıktan sonra ek bağlantılar oluşturmak için `ClipboardCommandSet.ProcessOnPasteCommand()` geçersiz kılın.

 **Öğelerin dış uygulamalara kopyalanabilen biçimleri** (örneğin, bit eşlem biçimine bir kenarlık eklemek) özelleştirin.
DslPackage projesindeki *MyDSL* `ClipboardCommandSet.ProcessOnMenuCopyCommand()` geçersiz kılın.

 **Öğelerin Pano 'ya kopyalama komutu tarafından nasıl kopyalanacağını özelleştirin, ancak bir sürükleme işleminde değildir.**
DslPackage projesindeki *MyDSL* `ClipboardCommandSet.CopyModelElementsIntoElementGroupPrototype()` geçersiz kılın.

 **Kopyala ve Yapıştır ile şekil yerleşimini koruyun.**
Kullanıcı birden çok şekli kopyalarken, bu kişilerin yapıştırıldığı zaman ilgili konumlarını koruyabilirsiniz. Bu teknik, [VMSDK: devre şemaları örneğindeki](http://go.microsoft.com/fwlink/?LinkId=213879)örnekle gösterilmiştir.

 Bu etkiyi elde etmek için şekilleri ve bağlayıcıları kopyalanmış ElementGroupPrototype öğesine ekleyin. Geçersiz kılınacak en kullanışlı Yöntem ElementOperations. CreateElementGroupPrototype (). Bunu yapmak için DSL projesine aşağıdaki kodu ekleyin:

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

 **Şekilleri seçili bir konuma (örneğin, geçerli imleç konumu) yapıştırın.**
Kullanıcı birden çok şekli kopyalarken, bu kişilerin yapıştırıldığı zaman ilgili konumlarını koruyabilirsiniz. Bu teknik, [VMSDK: devre şemaları örneğindeki](http://go.microsoft.com/fwlink/?LinkId=213879)örnekle gösterilmiştir.

 Bu etkiyi elde etmek için `ClipboardCommandSet.ProcessOnMenuPasteCommand()` `ElementOperations.Merge()` konuma özgü sürümünü kullanacak şekilde geçersiz kılın. Bunu yapmak için DslPackage projesine aşağıdaki kodu ekleyin:

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

 **Kullanıcıların öğeleri sürükleyip bırakması için izin verin.**
Bkz. [nasıl yapılır: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="customizeLinks"></a>Bağlantı kopyalama davranışını özelleştirme
 Kullanıcı bir öğeyi kopyaladığında, standart davranış herhangi bir katıştırılmış öğenin de kopyalanmasında olur. Standart kopyalama davranışını değiştirebilirsiniz. DSL tanımında bir ilişkinin bir tarafındaki bir rolü seçin Özellikler penceresi **yayar kopya** değerini ayarlayın.

 ![Etki alanı rolünün Copy özelliğini yayar](../modeling/media/dslpropagatescopy.png)

 Üç değer vardır:

- Kopyayı yayma

- Kopyayı yalnızca bağlantıya yay-grup yapıştırılırken, bu bağlantının yeni kopyası bağlantının diğer ucundaki var olan öğeye başvuracaktır.

- Kopyayı bağlantıya ve ters rol oyununa yay-kopyalanmış Grup, bağlantının diğer ucundaki öğesinin bir kopyasını içerir.

  ![PropagateCopyToLinkOnly ile kopyalamanın etkisi](../modeling/media/dslpropagatecopy.png)

  Yaptığınız değişiklikler hem öğeleri hem de kopyalanmış görüntüyü etkiler.

## <a name="programming-copy-and-paste-behavior"></a>Kopyalama ve yapıştırma davranışını programlama
 Bir DSL 'nin nesnelerin kopyalama, yapıştırma, oluşturma ve silme ile ilgili davranışı birçok yönü, diyagrama bağlanmış bir <xref:Microsoft.VisualStudio.Modeling.ElementOperations> örneğine tabidir. @No__t_0 ' den kendi sınıfınızı türeterek ve diyagram sınıfınızın <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> özelliğini geçersiz kılarak DSL davranışını değiştirebilirsiniz.

> [!TIP]
> Program kodunu kullanarak modeli özelleştirme hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

 ![Kopyalama işlemi için sıralı diyagram](../modeling/media/dslcopyseqdiagram.png)

 ![Yapıştırma işleminin sıralı diyagramı](../modeling/media/dslpasteseqdiagram.png)

#### <a name="to-define-your-own-elementoperations"></a>Kendi ElementOperations 'ı tanımlamak için

1. DSL projenizdeki yeni bir dosyada <xref:Microsoft.VisualStudio.Modeling.Diagrams.DesignSurfaceElementOperations> türetilen bir sınıf oluşturun.

2. Diyagram sınıfınız için kısmi bir sınıf tanımı ekleyin. Bu sınıfın adı **Dsl\GeneratedCode\Diagrams.cs**içinde bulunabilir.

    Diyagram sınıfında, <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.ElementOperations%2A> öğesini geçersiz kılarak ElementOperations alt sınıfınızın bir örneğini döndürün. Her çağrıda aynı örneği döndürmelidir.

   Bu kodu DslPackage projesindeki özel bir kod dosyasına ekleyin:

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
 ElementOperations, kopyalama, taşıma, silme ve sürükleme ve bırakma davranışlarını tanımlamak için de kullanılabilir. ElementOperations kullanmanın bir sunumu olarak, burada verilen örnek, özel sürükle ve bırak davranışını tanımlar. Ancak, bu amaçla, [nasıl yapılır: daha Genişletilebilir olan bir sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)bölümünde açıklanan alternatif yaklaşımı göz önünde bulundurabilir.

 ElementOperations sınıfında iki yöntem tanımlayın:

- Kaynak öğenin hedef şeklin, bağlayıcının veya diyagramın üzerine sürüklenemeyeceğini belirleyen `CanMerge(ModelElement targetElement, System.Windows.Forms.IDataObject data)`.

- kaynak öğeyi hedefle birleştiren `MergeElementGroupPrototype(ModelElement targetElement, ElementGroupPrototype sourcePrototype)`.

### <a name="canmerge"></a>CanMerge ()
 `CanMerge()`, fare diyagramda gezindiğinde kullanıcıya verilmesi gereken geri bildirimleri belirlemede çağrılır. Yöntemine yönelik parametreler, fare üzerine gelindiğinde bulunan öğesidir ve sürükleme işleminin gerçekleştirildiği kaynak hakkındaki verileri içerir. Kullanıcı ekran üzerinde herhangi bir yerden sürükleyebilirsiniz. Bu nedenle, kaynak nesne birçok farklı türde olabilir ve farklı biçimlerde seri hale getirilebilir. Kaynak bir DSL veya UML modelli ise, veri parametresi bir <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> serileştirmesi olur. Sürükleme, kopyalama ve araç kutusu işlemleri, model parçalarını göstermek için Elementgroupprototipleri kullanır.

 Öğe grubu prototipi, herhangi bir sayıda öğe ve bağlantı içerebilir. Öğe türleri, GUID 'Leri ile tanımlanabilir. GUID, temeldeki model öğesi değil, sürüklenen şekildir. Aşağıdaki örnekte, UML diyagramından bir sınıf şekli bu diyagrama sürüklendiğinde `CanMerge()` true değerini döndürür.

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

## <a name="mergeelementgroupprototype"></a>MergeElementGroupPrototype ()
 Bu yöntem, Kullanıcı bir öğeyi diyagrama, şekle veya bağlayıcıya düştüğünde çağrılır. Sürüklenen içeriği hedef öğe içine birleştirmelidir. Bu örnekte kod, hedef ve prototip türlerinin birleşimini tanıyıp tanımadığını belirler; Bu durumda, yöntemi sürüklenen öğeleri modele eklenmesi gereken öğelerin prototipine dönüştürür. Taban yöntemi, dönüştürülmüş veya Dönüştürülmeyen öğelerden birini birleştirmek için çağırılır.

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

 Bu örnek UML sınıf öğeleriyle bir UML sınıf diyagramından sürüklenen ile ilgilidir. DSL, UML sınıflarını doğrudan depolamak için tasarlanmamıştır, ancak bunun yerine, her sürüklenen UML sınıfı için bir DSL öğesi oluşturacağız. Bu, örneğin DSL bir örnek diyagramı ise yararlı olabilir. Kullanıcı bu sınıfların örneklerini oluşturmak için sınıfları diyagram üzerine sürükleyebilir.

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

## <a name="standard-copy-behavior"></a>Standart kopyalama davranışı
 Bu bölümdeki kodda kopyalama davranışını değiştirmek için geçersiz kılabileceğiniz Yöntemler gösterilmektedir. Kendi özelleştirmelerinizi nasıl elde etmek için bu bölümde, kopyalama işlemine dahil olan yöntemleri geçersiz kılan, ancak standart davranışı değiştirmediğinden oluşan kod gösterilmektedir.

 Kullanıcı CTRL + C tuşlarına bastığında veya Kopyala menü komutunu kullandığında Yöntem <xref:Microsoft.VisualStudio.Modeling.Shell.ClipboardCommandSet.ProcessOnMenuCopyCommand%2A> çağrılır. Bu, **Dslpackage\generated Code\CommandSet.cs**' de nasıl ayarlandığını görebilirsiniz. Komutların nasıl ayarlandığı hakkında daha fazla bilgi için bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 DslPackage projesinde *mydsl* `ClipboardCommandSet` kısmi sınıf tanımını ekleyerek Processonmenucopykomutunu geçersiz kılabilirsiniz.

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

 Her diyagramda tek bir ElementOperations örneği bulunur. Kendi türelerinizi sağlayabilirsiniz. DSL projesine yerleştirilebilecek bu dosya, geçersiz kılacak kodla aynı şekilde davranır:

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
- [Örnek: VMSDK devre şemaları örneği](http://go.microsoft.com/fwlink/?LinkId=213879)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]