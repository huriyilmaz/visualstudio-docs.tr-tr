---
title: 'Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme'
description: Kullanıcıların diğer diyagramlardan diyagramınıza öğe sürükleyebilmeleri için DSL 'ye sürükle ve bırak olayları için işleyiciler nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5707df4cf24a977d928ffda5b495bd1ffc8cc31b0e12331f44926487efbec7d2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356122"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme

Kullanıcıların diğer diyagramlardan veya Visual Studio diğer parçalarından öğe diyagramınıza sürükleyebilmeleri için, DSL 'ye sürükle ve bırak olayları için işleyiciler ekleyebilirsiniz. Çift tıklama gibi olaylar için de işleyiciler ekleyebilirsiniz. Birlikte, sürükle ve bırak ve çift tıklama işleyicileri *hareket işleyicileri* olarak bilinir.

Bu konu, diğer diyagramlardaki sürükle ve bırak hareketlerini ele alır. Tek bir diyagram içindeki taşıma ve kopyalama olayları için, bir alt sınıfı tanımlamanın alternatifini düşünün `ElementOperations` . Daha fazla bilgi için bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md). Ayrıca DSL tanımını özelleştirebilirsiniz.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>ShapeElement yöntemlerini geçersiz kılarak hareket Işleyicilerini tanımlama

`OnDragDrop`, `OnDoubleClick` , `OnDragOver` ve diğer Yöntemler geçersiz kılınabilir.

DSL projenize yeni bir kod dosyası ekleyin. Bir hareket işleyicisi için genellikle en azından aşağıdaki yönergelere sahip olmanız gerekir `using` :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

Yeni dosyada, şekil veya Diyagram sınıfı için sürükle işlemine yanıt vermesi gereken kısmi bir sınıf tanımlayın. Aşağıdaki yöntemleri geçersiz kılın:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>-Bir sürükleme işlemi sırasında fare işaretçisi şekle girdiğinde bu yöntem çağrılır. Yönteminizin, kullanıcının sürükleneceği öğeyi incelemesi gerekir ve bu şekle kullanıcının öğeyi bırakıp bırakması gerektiğini belirtmek için efekt özelliğini ayarlayın. Efekt özelliği, imlecin bu şeklin üzerindeyken görünüşünü belirler ve ayrıca `OnDragDrop()` Kullanıcı fare düğmesini bıraktığında çağranıp çağrılmayacağını belirler.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -Bu yöntem, `OnDragOver(DiagramDragEventArgs e)` daha önce `e.Effect` dışında bir değere ayarlandıysa fare işaretçisi bu şeklin veya diyagramın üzerine getirildiğinde Kullanıcı fare düğmesini bıraktığında çağrılır `None` .

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -Bu yöntem, Kullanıcı şekle veya diyagrama çift tıkladığında çağrılır.

     Daha fazla bilgi için bkz. [nasıl yapılır: bir şekle veya Dekorata tıklama](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

`IsAcceptableDropItem(e)`Sürüklenen öğenin kabul edilip edilmeyeceğini belirlemek için tanımlayın ve öğe bırakıldığında modelinizi güncelleştirmek Için ProcessDragDropItem (e) seçeneğini belirleyin. Bu yöntemlerin önce öğeyi olay bağımsız değişkenlerinden ayıklamalıdır. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [sürüklenen öğeye başvuru alma](#to-send-an-object-from-a-source-dsl).

## <a name="define-gesture-handlers-by-using-mef"></a>MEF kullanarak hareket Işleyicileri tanımlama

Üçüncü taraf geliştiricilerin DSL 'niz için kendi işleyicilerini tanımlayabilmesini istiyorsanız bu yöntemi kullanın. Kullanıcılar, DSL 'yi yükledikten sonra üçüncü taraf uzantıları yüklemeyi seçebilirler.

MEF (Managed Extensibility Framework), en az yapılandırmayla yüklenebilen bileşenleri tanımlamanıza olanak sağlar. daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>MEF hareketi işleyicisi tanımlamak için

1. **DSL** ve **DslPackage** projelerinize, [mef kullanarak DSL 'Nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md)bölümünde açıklanan **MefExtension** dosyalarını ekleyin.

2. Artık bir MEF bileşeni olarak bir hareket işleyicisi tanımlayabilirsiniz:

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     Birden çok hareket işleyicisi bileşeni oluşturabilirsiniz, örneğin, farklı tipte sürüklenen nesneler olduğunda.

3. Hedef şekil, bağlayıcı veya Diyagram sınıfları için kısmi sınıf tanımları ekleyin ve yöntemlerini `IsAcceptableDropItem()` ve ve tanımlayın `ProcessDragDropItem()` . Bu yöntemlerin, olay bağımsız değişkenlerinden sürüklenen öğe ayıklanarak başlaması gerekir. Daha fazla bilgi için bkz. [sürüklenen öğeye başvuru alma](#to-send-an-object-from-a-source-dsl).

## <a name="how-to-decode-the-dragged-item"></a>Sürüklenen öğenin kodunu çözme

Öğeler herhangi bir pencereden veya masaüstünden, ayrıca bir DSL 'den sürüklenip olabilir.

Kullanıcı diyagramınıza bir öğe veya diyagramınızın bir bölümünden diğerine sürüklendiğinde, sürüklediğiniz öğe hakkındaki bilgiler içinde kullanılabilir `DiagramDragEventArgs` . Sürükleme işlemi ekrandaki herhangi bir nesne üzerinde başlaabileceğinden, veriler çeşitli biçimlerde kullanılabilir. Kodunuzun, ilgilendiği biçimleri tanıması gerekir.

Sürükleme kaynak bilgilerinizin kullanılabildiği biçimleri öğrenmek için kodunuzu hata ayıklama modunda çalıştırın, girişte veya olarak bir kesme noktası ayarlar `OnDragOver()` `CanDragDrop()` . Parametresinin değerlerini inceleyin `DiagramDragEventArgs` . Bilgiler iki şekilde sunulmaktadır:

- <xref:System.Windows.Forms.IDataObject>  `Data` -Bu özellik, genellikle birden çok biçimde kaynak nesnelerinin serileştirilmiş sürümlerini taşır. En faydalı işlevleri şunlardır:

  - diagramEventArgs. Data. GetDataFormats ()-sürüklenen nesnenin kodunu çözebileceği biçimleri listeler. Örneğin, Kullanıcı masaüstünden bir dosya sürüklediğinde, kullanılabilir biçimler dosya adını (" `FileNameW` ") içerir.

  - `diagramEventArgs.Data.GetData(format)` -Belirtilen biçimdeki sürüklenen nesnenin kodunu çözer. Nesneyi uygun türe atayın. Örnek:

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    Ayrıca, kendi özel biçiminizdeki kaynak veri yolu başvuruları gibi nesneleri de aktarabilirsiniz. Daha fazla bilgi için bkz. [bir sürükle ve bırak Ile model veri yolu başvuruları gönderme](#to-send-an-object-from-a-source-dsl).

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>`Prototype`-Kullanıcıların BIR DSL veya UML modelinden öğe sürükleyebilmesi istiyorsanız bu özelliği kullanın. Bir öğe grubu prototipi bir veya daha fazla nesne, bağlantı ve özellik değeri içerir. Yapıştırma işlemlerinde ve araç kutusundan bir öğe eklerken de kullanılır. Bir prototipde nesneler ve türleri GUID tarafından tanımlanır. Örneğin, bu kod kullanıcının UML diyagramı veya UML Model Gezgini 'nden sınıf öğelerini sürükleyesağlar:

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     UML şekillerini kabul etmek için, deneme tarafından UML şekil sınıflarının GUID 'Lerini saptayın. Her diyagramda genellikle birden çok öğe türü olduğunu unutmayın. Ayrıca, bir DSL veya UML diyagramından sürüklenen bir nesnenin model öğesi değil, şekil olduğunu unutmayın.

`DiagramDragEventArgs` Ayrıca, geçerli fare işaretçisi konumunu ve kullanıcının CTRL, ALT veya SHIFT tuşlarına basılı tutup basmadığını belirten özelliklere sahiptir.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Sürüklenen bir öğenin orijinalini alma

Sürüklenen öğe bir DSL öğesi ise, kaynak modeli açıp öğeye erişebilirsiniz.

`Data` `Prototype` Olay bağımsız değişkenlerinin ve özellikleri yalnızca sürüklenen şekle yönelik bir başvuru içerir. Genellikle, hedef DSL 'de prototipten bir şekilde türetilmiş bir nesne oluşturmak istiyorsanız, orijinale erişim edinmeniz, örneğin dosya içeriğini okumak veya bir şekille temsil edilen model öğesine gitmek gerekir. bu konuda yardımcı olması için Visual Studio Model veri yolu kullanabilirsiniz.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Model veri yolu için DSL projesi hazırlama

kaynak DSL 'yi Visual Studio Model veri yolu tarafından erişilebilir hale getirme:

1. DSL Tasarımcısı ' de kaynak DSL 'nin DSL tanım dosyasını açın. Tasarım yüzeyine sağ tıklayın ve sonra **ModelBus 'ı etkinleştir**' e tıklayın. İletişim kutusunda seçeneklerden birini veya her ikisini birden seçin.  **Tamam**'a tıklayın. DSL çözümüne yeni bir proje "ModelBus" eklenir.

2. **Tüm Şablonları Dönüştür** ' e tıklayın ve çözümü yeniden oluşturun.

### <a name="to-send-an-object-from-a-source-dsl"></a>Kaynak DSL 'den bir nesne göndermek için

1. ElementOperations alt sınıfınızın içinde, `Copy()` bir model veri yolu başvurusunu (MBR) bir IDataObject 'e kodlayan şekilde geçersiz kılın. Bu yöntem, Kullanıcı kaynak diyagramından sürüklemeye başladığında çağrılır. Kodlanmış MBR daha sonra Kullanıcı hedef diyagramı bırakıyorda, IDataObject 'de kullanılabilir olacaktır.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Hedef DSL veya UML projesindeki bir DSL 'den model veri yolu başvurusu almak için

1. Hedef DSL projesinde, projeye başvuruları ekle:

    - Kaynak Dsl projesi.

    - Kaynak ModelBus projesi.

2. Hareket işleyici kod dosyasında aşağıdaki ad alanı başvurularını ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. Aşağıdaki örnek, kaynak model öğesine nasıl erişim alınacağını göstermektedir:

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>UML modelden kaynakılmış bir öğeyi kabul etmek için

- Aşağıdaki kod örneği, UML diyagramından bırakılan bir nesneyi kabul eder.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>Fare eylemlerini kullanma: bölme öğelerini sürükleme

Şekil alanları üzerinde fare eylemlerini izleyen bir işleyici yazabilirsiniz. Aşağıdaki örnek, fare ile sürükleyerek bir bölmedeki öğeleri yeniden sıralamanıza imkan sağlar.

Bu örneği oluşturmak için **sınıf diyagramları** çözüm şablonunu kullanarak bir çözüm oluşturun. Bir kod dosyası ekleyin ve aşağıdaki kodu ekleyin. Ad alanını kendinizinkini aynı olacak şekilde ayarlayın.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape. Yuk.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)
- [Etki Alanına Özgü Dil Çözümlerini Dağıtma](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
