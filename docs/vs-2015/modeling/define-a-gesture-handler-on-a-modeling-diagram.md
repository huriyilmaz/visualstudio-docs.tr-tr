---
title: Modelleme diyagramında hareket işleyicisi tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af4123b24ab9286e306a1034de4416a31ae76f2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533074"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Modelleme diyagramında hareket işleyicisi tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, kullanıcının öğeleri bir UML diyagramına çift tıkladığı veya sürüklediğinde gerçekleştirilecek komutları tanımlayabilirsiniz. Bu uzantıları bir Visual Studio Tümleştirme Uzantısı 'na ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)) paketleyebilir ve diğer Visual Studio kullanıcılarına dağıtabilirsiniz.

 Diyagram türü ve sürüklemek istediğiniz öğe türü için yerleşik bir davranış zaten varsa, bu davranışı ekleyemeyebilirsiniz veya geçersiz kılamazsınız.

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-uml-models-and-diagrams.md#Requirements)bakın.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Hareket Işleyicisi oluşturma
 Bir UML tasarımcısı için bir hareket işleyicisi tanımlamak üzere, hareket işleyicisinin davranışını tanımlayan bir sınıf oluşturmanız ve bu sınıfı bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) katıştırmanız gerekir. VSıX işleyiciyi yükleyen bir kapsayıcı görevi görür. Hareket işleyicisini tanımlamanın iki alternatif yöntemi vardır:

- **Proje şablonunu kullanarak kendi VSIX 'inde bir hareket işleyicisi oluşturun.** Bu daha hızlı bir yöntemdir. İşleyicinizi doğrulama uzantıları, özel araç kutusu öğeleri veya menü komutları gibi diğer tür uzantılarla birleştirmek istemiyorsanız kullanın.

- **Ayrı hareket işleyicisi ve VSıX projeleri oluşturun.** Aynı VSıX içinde birkaç uzantı türünü birleştirmek istiyorsanız bu yöntemi kullanın. Örneğin, hareket işleyiciniz modelin belirli kısıtlamaları gözlemmesini bekliyorsa, bir doğrulama yöntemiyle aynı VSıX 'e katabilirsiniz.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Kendi VSIX 'inde bir hareket işleyicisi oluşturmak için

1. **Yeni proje** iletişim kutusunda, **modelleme projeleri**' nin altında, **hareket uzantısı**' nı seçin.

2. Yeni projede **. cs** dosyasını açın ve `GestureExtension` hareket işleyicinizi uygulamak için sınıfını değiştirin.

    Daha fazla bilgi için, bkz. [hareket Işleyicisini uygulama](#Implementing).

3. F5 tuşuna basarak hareket işleyicisini test edin. Daha fazla bilgi için bkz. [hareket Işleyicisini yürütme](#Executing).

4. Hareket işleyicisini, projeniz tarafından oluşturulan **bin \\ \* \\ \* . vsix** dosyasını kopyalayarak başka bir bilgisayara yükler. Daha fazla bilgi için bkz. [Uzantı yükleme ve kaldırma](#Installing).

   Alternatif yordam aşağıda verilmiştir:

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Hareket işleyicisi için ayrı bir sınıf kitaplığı (DLL) projesi oluşturmak için

1. Yeni bir çözümde ya da var olan bir çözümde bir sınıf kitaplığı projesi oluşturun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

   1. **Dosya** menüsünde, **Yeni**, **Proje**' yi seçin.

   2. **Yüklü şablonlar**altında **Visual C#** veya **Visual Basic**' i genişletin, ardından Orta sütundaki **sınıf kitaplığı**' nı seçin.

2. Aşağıdaki başvuruları projenize ekleyin.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` – Buna yalnızca Katman diyagramlarını uzatıyorsunuz yapmanız gerekir. Daha fazla bilgi için bkz. [Katman diyagramlarını genişletme](../modeling/extend-layer-diagrams.md).

3. Projeye bir sınıf dosyası ekleyin ve içeriğini aşağıdaki koda ayarlayın.

   > [!NOTE]
   > Ad alanını ve sınıf adını tercihinize göre değiştirin.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

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

         return prototype.ProtoElements.Select(
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

     }
   }

   ```

    Yöntemlere yerleştirilecek hakkında daha fazla bilgi için, bkz. [hareket Işleyicisini uygulama](#Implementing).

   Menü komutunu bir VSıX projesine eklemeniz gerekir ve bu, komutu yüklemek için kapsayıcı olarak davranır. İsterseniz, diğer bileşenleri aynı VSıX 'e ekleyebilirsiniz.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Bir VSıX projesine ayrı bir hareket işleyicisi eklemek için

1. Kendi VSıX ile hareket işleyicisi oluşturduysanız, bu yordama ihtiyacınız yoktur.

2. Çözümünüz bir tane içermiyorsa, bir VSıX projesi oluşturun.

    1. **Çözüm Gezgini**, çözümün kısayol menüsünde, **Ekle**, **Yeni proje**' yi seçin.

    2. **Yüklü şablonlar**altında **Visual C#** veya **Visual Basic**' i genişletin, ardından **genişletilebilirlik**' i seçin. Orta sütunda **VSIX projesi**' ni seçin.

3. VSıX projesini çözümün başlangıç projesi olarak ayarlayın.

    - Çözüm Gezgini, VSıX projesinin kısayol menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.

4. **Source. Extension. valtmanifest**içinde, hareket işleyicisi sınıf KITAPLıĞı projesini MEF bileşeni olarak ekleyin:

    1. **Meta veriler** sekmesinde VSIX için bir ad belirleyin.

    2. **Hedefleri yüklensin** sekmesinde, Visual Studio sürümlerini hedef olarak ayarlayın.

    3. **Varlıklar** sekmesinde **Yeni**' yi seçin ve iletişim kutusunda, şunu ayarlayın:

         **Tür**  =  **MEF bileşeni**

         **Kaynak**  =  **Geçerli çözümdeki bir proje**

         **Proje**  =  *Sınıf kitaplığı projeniz*

## <a name="executing-the-gesture-handler"></a><a name="Executing"></a> Hareket Işleyicisini yürütme
 Test amaçları için, hareket işleyicinizi hata ayıklama modunda yürütün.

#### <a name="to-test-the-gesture-handler"></a>Hareket işleyicisini test etmek için

1. **F5**tuşuna basın veya **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat**' a tıklayın.

    Deneysel bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar.

    **Sorun giderme**: yeni bir başlamazsa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

   - Birden çok projeniz varsa, VSıX projesinin çözümün başlangıç projesi olarak ayarlandığından emin olun.

   - Çözüm Gezgini, başlangıç veya yalnızca projenin kısayol menüsünde Özellikler ' i seçin. Proje özellikleri düzenleyicisinde **Hata Ayıkla** sekmesini seçin. **Dış program Başlat** alanındaki dizenin, genellikle tam yol adı olduğundan emin olun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Deneysel içinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir modelleme projesi açın veya oluşturun ve bir modelleme diyagramı açın veya oluşturun. Hareket işleyici sınıfınızın özniteliklerinde listelenen türlerden birine ait bir diyagram kullanın.

3. Diyagramda herhangi bir yere çift tıklayın. Çift tıklama işleyiciniz çağrılmalıdır.

4. UML Gezgininden bir öğeyi diyagram üzerine sürükleyin. Sürükleme işleyiciniz çağrılmalıdır.

   **Sorun giderme**: hareket işleyicisi çalışmazsa şunları yaptığınızdan emin olun:

- Hareket işleyicisi projesi, VSıX projesindeki **kaynak. Extensions. manifest** içindeki **VARLıKLAR** sekmesinde bir MEF bileşeni olarak listelenir.

- Tüm `Import` ve `Export` özniteliklerinin parametreleri geçerlidir.

- `CanDragDrop`Yöntem döndürülmedi `false` .

- Kullandığınız model diyagramın türü (UML sınıfı, sırası, vb.), hareket işleyicisi sınıf özniteliklerinden biri olarak [ClassDesignerExtension], [SequenceDesignerExtension] vb. olarak listelenir.

- Bu tür hedef ve bırakılan öğe için önceden tanımlanmış bir yerleşik işlev yok.

## <a name="implementing-the-gesture-handler"></a><a name="Implementing"></a> Hareket Işleyicisini uygulama

### <a name="the-gesture-handler-methods"></a>Hareket Işleyici yöntemleri
 Hareket işleyicisi sınıfı uygular ve dışarı aktarır <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension> . Tanımlamanız gereken yöntemler şunlardır:

|İmza|Description|
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|`true`İçinde başvurulan kaynak öğenin bu hedefte bırakılmasına izin vermek için geri dönün `dragEvent` .<br /><br /> Bu yöntem modelde değişiklik yapmamalıdır. Kullanıcı fareyi taşırken ok durumunu belirlemede kullanıldığından, bu değer hızlı bir şekilde çalışmalıdır.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|İçinde başvurulan kaynak nesnesine ve hedefe göre modeli güncelleştirin `dragEvent` .<br /><br /> Kullanıcı fareyi sürüklemeye sonra bıraktığında çağırılır.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` kullanıcının çift tıkladığını şekildir.|

 Dosyalar, .NET Sınıf görünümündeki düğümler gibi çok çeşitli diğer öğeleri de yalnızca UML değil de kabul edebilecek işleyiciler yazabilirsiniz. Kullanıcı bu öğelerden herhangi birini bir UML diyagramına sürükleyebilir, bu da `OnDragDrop` öğelerin seri hale getirilmiş biçimini çözebilen bir yöntem yazmanızı sağladı. Kod çözme yöntemleri bir öğe türünden diğerine farklılık gösterir.

 Bu yöntemlerin parametreleri şunlardır:

- `ShapeElement target`. Kullanıcının üzerine bir şeyi sürüklemiş olduğu şekil veya diyagram.

    `ShapeElement` , UML modelleme araçlarının temelini oluşturan uygulamadaki bir sınıftır. UML model ve diyagramlarını tutarsız bir duruma getirme riskini azaltmak için bu sınıfın yöntemlerini doğrudan kullanmanızı öneririz. Bunun yerine, öğesini bir içinde sarın `IShape` ve [DIYAGRAMDA bir UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md)bölümünde açıklanan yöntemleri kullanın.

  - Şunu almak için `IShape` :

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Sürükle veya çift tıklama işlemi tarafından hedeflenen model öğesini almak için:

      ```
      IElement target = targetIShape.Element;
      ```

      Bunu daha belirli bir öğe türüne çevirebilirsiniz.

  - UML modelini içeren UML Model deposunu almak için:

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - Konak ve hizmet sağlayıcısına erişim sağlamak için:

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`. Bu parametre, bir sürükleme işleminin kaynak nesnesinin seri hale getirilmiş formunu taşır:

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     Birçok farklı türdeki öğeleri, farklı veya Windows masaüstünden bir diyagram üzerine sürükleyebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Farklı öğe türleri içinde farklı yollarla kodlanır `IDataObject` . Öğeleri bundan ayıklamak için, uygun nesne türü için belgelere bakın.

     Kaynak nesneniz UML Model Gezgini 'nden veya başka bir UML diyagramından sürüklenen bir UML öğesi ise, bir UML [model öğelerini IDataObject 'Den al](../modeling/get-uml-model-elements-from-idataobject.md)' a bakın.

### <a name="writing-the-code-of-the-methods"></a>Yöntemlerin kodunu yazma
 Modeli okumak ve güncellemek üzere kod yazma hakkında daha fazla bilgi için bkz. [UML API Ile programlama](../modeling/programming-with-the-uml-api.md).

 Bir sürükleme işleminde model bilgilerine erişme hakkında daha fazla bilgi için, bkz. IDataObject ['den UML model öğelerini edinme](../modeling/get-uml-model-elements-from-idataobject.md).

 Bir sıralı diyagram ile uğraşıyorsanız [UML API 'sini kullanarak UML sıra diyagramlarını da düzenleme](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)bölümüne bakın.

 Yöntemlerin parametrelerine ek olarak, sınıfınızın geçerli diyagrama ve modele erişim sağlayan içeri aktarılan bir özelliği de bildirebilirsiniz.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 Bildirimi, `IDiagramContext` metotlarda diyagrama, geçerli seçime ve modele erişen kod yazmanıza izin verir:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 Daha fazla bilgi için bkz. [UML modeline gitme](../modeling/navigate-the-uml-model.md).

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a> Uzantı yükleme ve kaldırma
 Bir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] uzantıyı, hem kendi bilgisayarınıza hem de diğer bilgisayarlara yükleyebilirsiniz.

#### <a name="to-install-an-extension"></a>Uzantı yüklemek için

1. Bilgisayarınızda, VSıX projeniz tarafından oluşturulan **. vsix** dosyasını bulun.

    1. **Çözüm Gezgini**, VSIX projesinin kısayol menüsünde **klasörü Windows Gezgini 'nde aç**' ı seçin.

    2. Dosya ** \\ \* bin \\ **' i_Proje_**. vsix** ' i bulun

2. **. Vsix** dosyasını, uzantıyı yüklemek istediğiniz hedef bilgisayara kopyalayın. Bu, kendi bilgisayarınız veya başka bir tane olabilir.

     Hedef bilgisayar, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **kaynak. Extension. valtmanifest**içinde belirttiğiniz sürümlerden birine sahip olmalıdır.

3. Hedef bilgisayarda **. vsix** dosyasını açın.

     **Visual Studio Uzantı Yükleyicisi** açılır ve uzantıyı yüklüyor.

4. Başlatın veya yeniden başlatın [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

#### <a name="to-uninstall-an-extension"></a>Bir uzantıyı kaldırmak için

1. **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Yüklü uzantıları**genişletin.

3. Uzantıyı seçin ve ardından **Kaldır**' ı seçin.

   Nadiren, hatalı bir uzantı yükleme başarısız olur ve hata penceresinde bir rapor oluşturur, ancak Uzantı Yöneticisi 'nde görünmez. Bu durumda, dosyayı öğesinden silerek uzantıyı kaldırabilirsiniz:

   *% LocalAppData%* **\Local\microsoft\visualstudio \\ [sürüm] \Extensions**

## <a name="example"></a><a name="DragExample"></a> Örneğinde
 Aşağıdaki örnek, bir bileşen diyagramından sürüklenen bir bileşenin bölümlerine ve bağlantı noktalarına bağlı olarak bir sıralı diyagramda Yaşam çizgilerinin nasıl oluşturulacağını gösterir.

 Test etmek için F5 'e basın. Visual Studio 'nun deneysel bir örneği açılır. Bu örnekte, bir UML modeli açın ve bileşen diyagramında bir bileşen oluşturun. Bu bileşene bazı arabirimler ve iç bileşen bölümleri ekleyin. Arabirimleri ve parçaları seçin. Ardından arabirimleri ve parçaları sıralı diyagram üzerine sürükleyin. (Sıralı diyagram için bileşen diyagramından sekmeye kadar sürükleyin ve sonra sıralı diyagramda aşağı taşıyın.) Her arabirim ve bölüm için bir yaşam çizgisi görüntülenir.

 Sıralı diyagramlara bağlama etkileşimleri hakkında daha fazla bilgi için bkz. UML [API kullanarak UML sıra diyagramlarını düzenleme](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

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

    return prototype.ProtoElements.Select(
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

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 Kodu, `GetModelElementsFromDragEvent()` [IDataObject 'den UML model öğelerini Al](../modeling/get-uml-model-elements-from-idataobject.md)bölümünde açıklanmaktadır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Modelleme uzantısı tanımlama ve YÜKLEMEYI](../modeling/define-and-install-a-modeling-extension.md) [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) [Modelleme Diyagramında Menü komutu tanımlama modelleme diyagramı üzerinde BIR menü komutu tanımlama](../modeling/define-a-menu-command-on-a-modeling-diagram.md) UML [API ile programlama](../modeling/programming-with-the-uml-api.md) [için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md)
