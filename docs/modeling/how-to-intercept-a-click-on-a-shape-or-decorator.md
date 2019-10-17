---
title: 'Nasıl yapılır: Şekil veya Dekoratörde bir Click için Araya Girme'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e3295476b9a9d35768963baa05829a560fc9291
ms.sourcegitcommit: e82baa50bf5a65858c410882c2e86a552c2c1921
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381493"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Nasıl yapılır: Şekil veya Dekoratörde bir Click için Araya Girme
Aşağıdaki yordamlarda, bir şekle veya bir simge dekoratmasına tıklamanın nasıl ele alınacağını gösterilmektedir. Tıklama, Çift tıklama, sürükme ve diğer hareketleri yakalayabilir ve öğenin yanıt vermesini sağlayabilirsiniz.

## <a name="to-intercept-clicks-on-shapes"></a>Şekillerdeki tıklamaları kesme
 DSL projesinde, oluşturulan kod dosyalarından ayrı bir kod dosyasında, şekil sınıfı için kısmi bir sınıf tanımı yazın. @No__t-0 veya `On...` ile başlayan bir ada sahip diğer yöntemlerden birini geçersiz kılın. Örneğin:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
> Olayın, kapsayan şekle veya diyagrama geçirilmesini istemediğiniz müddetçe `e.Handled` ' ı `true` olarak ayarlayın.

## <a name="to-intercept-clicks-on-decorators"></a>Dekoratörler üzerinde tıklama tıklamalarını kesme
 Görüntü Dekoratörleri bir OnDoubleClick yöntemine sahip olan ImageField sınıfının bir örneğine taşınır. Bir ImageField alt sınıfı yazarsanız tıklama işlemlerini izleyebilirsiniz. Alanlar ınitialeshapefields yönteminde ayarlanır. Bu nedenle, normal ImageField yerine alt sınıflarınızın örneğini oluşturmak için bu yöntemi değiştirmeniz gerekir. Initialeshapefields yöntemi şekil sınıfının oluşturulan kodunda bulunur. Aşağıdaki yordamda açıklandığı gibi `Generates Double Derived` özelliğini ayarlarsanız şekil sınıfını geçersiz kılabilirsiniz.

 Initialeshapefields bir örnek yöntemi olsa da, her bir sınıf için yalnızca bir kez çağırılır. Bu nedenle, diyagramdaki her bir şekil için değil her bir sınıftaki her bir alan için yalnızca bir Click ' in bir örneği bulunur. Kullanıcı bir örneğe çift tıkladığında, örnekteki kodun gösterdiği gibi, hangi örneğin isabet olduğunu belirlemeniz gerekir.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Bir simge dekoratörü ' ne tıklamasına izin vermek için

1. Bir DSL çözümü açın veya oluşturun.

2. Simge dekoratörü olan bir şekil seçin veya oluşturun ve bunu bir etki alanı sınıfıyla eşleyin.

3. @No__t-0 klasöründeki dosyalardan ayrı bir kod dosyasında, ImageField öğesinin yeni alt sınıfını oluşturun:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Olayın, kapsayan şekle geçirilmesini istemiyorsanız, Işlenmiş olarak ayarlamanız gerekir.

4. Aşağıdaki kısmi sınıf tanımını ekleyerek şekil sınıfınızdaki ınitialeshapefields metodunu geçersiz kılın.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Çözümü derleyin ve çalıştırın.

2. Şeklin bir örneğindeki simgeye çift tıklayın. Sınama iletiniz görünmelidir.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>CompartmentShape listelerinde tıklama ve sürükme
 Aşağıdaki örnek, kullanıcıların bir bölme şeklinin içindeki öğeleri sürükleyerek yeniden sıralamasını sağlar. Bu kodu çalıştırmak için:

1. **Sınıf diyagramları** çözüm şablonunu kullanarak yenı bir DSL çözümü oluşturun.

    Ayrıca, bölme şekillerini içeren bir çözümle birlikte çalışabilirsiniz. Bu kod, şekil tarafından temsil edilen model öğeleri ve bölme listesi öğelerinde temsil edilen öğeler arasında bir katıştırma ilişkisi olduğunu varsayar.

2. Bölme şeklinin **Double Ile türetilmiş özelliğini oluşturur** .

3. Bu kodu **DSL** projesindeki bir dosyaya ekleyin.

4. Bu koddaki etki alanı sınıfı ve şekil adlarını kendi DSL 'ınızla eşleşecek şekilde ayarlayın.

   Özet olarak, kod aşağıdaki gibi çalışmaktadır. Bu örnekte, `ClassShape`, bölme şeklinin adıdır.

- Bir dizi fare olay işleyicisi oluşturulduğunda her bir bölme örneğine eklenir.

- @No__t-0 olayı geçerli öğeyi depolar.

- Fare geçerli öğeden dışarı taştığında, imleci ayarlayan ve serbest bırakılana kadar fare yakalayan bir MouseAction örneği oluşturulur.

     Bir öğenin metnini seçme gibi diğer fare eylemleriyle karışmasını önlemek için, fare orijinal öğeyi kapatıncaya kadar MouseAction oluşturulmaz.

     Yalnızca bir MouseAction oluşturmaya alternatif olarak, MouseUp için dinlemek yeterlidir. Ancak, Kullanıcı fare bölmesini bölme dışına sürükledikten sonra yeniden yayımlarsa bu düzgün çalışmaz. MouseAction, farenin nerede yayımlanmadığına bakılmaksızın uygun eylemi gerçekleştirebilir.

- Fare bırakıldığında, MouseAction. MouseUp model öğeleri arasındaki bağlantıların sırasını yeniden düzenler.

- Rol sırası değişikliği, görüntüyü güncelleştiren bir kural tetikler. Bu davranış zaten tanımlanmış ve ek kod gerekmez.

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
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
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
  /// click somewhere else in the source shape.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
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

## <a name="see-also"></a>Ayrıca Bkz.

- [Değişikliklere Yanıt Verme ve Değişiklikleri Yayma](../modeling/responding-to-and-propagating-changes.md)
- [Dekoratörlerin Özellikleri](../modeling/properties-of-decorators.md)
