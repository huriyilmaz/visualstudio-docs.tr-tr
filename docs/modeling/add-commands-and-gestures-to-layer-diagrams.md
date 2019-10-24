---
title: Bağımlılık diyagramlarına komut ve hareket ekleme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d54936c61606b67c298992cd003723327042eb0a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747663"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Bağımlılık diyagramlarına komut ve hareket ekleme

Visual Studio 'da bağımlılık diyagramlarında sağ tıklama menü komutlarını ve hareket işleyicilerini tanımlayabilirsiniz. Bu uzantıları, diğer Visual Studio kullanıcılarına dağıtabileceğiniz bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) paketleyebilirsiniz.

İsterseniz aynı Visual Studio projesinde birkaç komut ve hareket işleyicisi tanımlayabilirsiniz. Ayrıca, bu gibi birçok projeyi tek bir VSıX içinde birleştirebilirsiniz. Örneğin, katman komutları ve etki alanına özgü dil içeren tek bir VSıX tanımlayabilirsiniz.

> [!NOTE]
> Ayrıca, kullanıcıların kaynak kodunun bağımlılık diyagramlarıyla karşılaştırıldığı mimari doğrulamasını özelleştirebilirsiniz. Mimari doğrulamayı ayrı bir Visual Studio projesinde tanımlamanız gerekir. Diğer uzantılarla aynı VSıX 'e ekleyebilirsiniz. Daha fazla bilgi için bkz. [bağımlılık diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Gereksinimler

[Gereksinimlere](../modeling/extend-layer-diagrams.md#requirements)bakın.

## <a name="define-a-command-or-gesture-in-a-new-vsix"></a>Yeni bir VSıX 'te komut veya hareket tanımlama

Uzantı oluşturmanın en hızlı yöntemi, proje şablonunu kullanmaktır. Bu, kodu ve VSıX bildirimini aynı projeye koyar.

1. Yeni bir **Katman Tasarımcısı komut uzantısı** veya **Katman Tasarımcısı hareketi uzantı** projesi oluşturun.

   Şablon küçük bir çalışma örneği içeren bir proje oluşturur.

2. Uzantıyı test etmek için **Ctrl** +**F5** veya **F5**tuşlarına basın.

    Visual Studio 'nun deneysel bir örneği başlar. Bu örnekte, bir bağımlılık diyagramı oluşturun. Komut veya hareket uzantınızın bu diyagramda çalışması gerekir.

3. Deneysel örneği kapatın ve örnek kodu değiştirin.

4. Aynı projeye daha fazla komut veya hareket işleyicisi ekleyebilirsiniz. Daha fazla bilgi için, aşağıdaki bölümlerden birine bakın:

    [Menü komutu tanımlama](#command)

    [Hareket Işleyicisi tanımlama](#gesture)

::: moniker range="vs-2017"

5. Uzantıyı Visual Studio 'nun ana örneğine veya başka bir bilgisayara yüklemek için *bin* dizininde *. vsix* dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler** ' i seçin.

::: moniker-end

::: moniker range=">=vs-2019"

5. Uzantıyı Visual Studio 'nun ana örneğine veya başka bir bilgisayara yüklemek için *bin* dizininde *. vsix* dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için **Uzantılar** menüsünde **Uzantıları Yönet** ' i seçin.

::: moniker-end

## <a name="add-a-command-or-gesture-to-a-separate-vsix"></a>Ayrı bir VSıX 'e komut veya hareket ekleme

Komutları, katman Doğrulayıcıları ve diğer uzantıları içeren bir VSıX oluşturmak istiyorsanız, VSıX tanımlamak için bir proje oluşturmanızı ve işleyiciler için ayrı projeler oluşturmanızı öneririz.

1. Yeni bir **sınıf kitaplığı** projesi oluşturun. Bu proje komut veya hareket işleyicisi sınıfları içerecektir.

   > [!NOTE]
   > Tek bir sınıf kitaplığında birden fazla komut veya hareket işleyicisi sınıfı tanımlayabilirsiniz, ancak katman doğrulama sınıflarını ayrı bir sınıf kitaplığında tanımlamanız gerekir.

2. Çözümünüze VSıX projesi ekleyin veya oluşturun. VSıX projesi **kaynak. Extension. valtmanifest**adlı bir dosya içerir.

3. **Çözüm Gezgini**, VSIX projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

4. **Source. Extension. valtmanifest**Içinde, **varlıklar**altında, komut veya hareket işleyicisi projesini MEF bileşeni olarak ekleyin.

    1. **Varlıklar**. sekmesinde **Yeni**' yi seçin.

    2. **Türünde**, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

    3. **Kaynakta**, **Geçerli çözümde proje** ' yi seçin ve komut veya hareket işleyicisi projenizin adını seçin.

    4. Dosyayı kaydedin.

5. Komut veya hareket işleyicisi projesine dönün ve aşağıdaki proje başvurularını ekleyin:

   |**Başvuru**|**Bunu yapmanıza izin verir**|
   |-|-|
   |Program Files\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Katmanları oluşturma ve düzenleme|
   |Microsoft. VisualStudio. Uml. Interfaces|Katmanları oluşturma ve düzenleme|
   |Microsoft. VisualStudio. mimari Turetools. Extensibility|Diyagramlarda şekilleri değiştirme|
   |System. ComponentModel. Composition|Managed Extensibility Framework kullanarak bileşenleri tanımlama (MEF)|
   |Microsoft. VisualStudio. model. SDK. sürümünüze|Modelleme uzantıları tanımlama|
   |Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze|Şekilleri ve diyagramları güncelleştirme|

6. Uzantınızın kodunu içermesi için C# Sınıf Kitaplığı projesindeki sınıf dosyasını düzenleyin. Daha fazla bilgi için, aşağıdaki bölümlerden birine bakın:

     [Menü komutu tanımlama](#command)

     [Hareket Işleyicisi tanımlama](#gesture)

7. Özelliği test etmek için **Ctrl** +**F5** veya **F5**tuşlarına basın.

   Visual Studio 'nun deneysel bir örneği açılır. Bu örnekte, bir bağımlılık diyagramı oluşturun veya açın.

8. VSıX 'i Visual Studio 'nun ana örneğine veya başka bir bilgisayara yüklemek için VSıX projesinin **bin** dizininde **. vsix** dosyasını bulun. VSıX 'i yüklemek istediğiniz bilgisayara kopyalayın. Dosya Gezgini 'nde VSıX dosyasına çift tıklayın.

## <a name="command"></a>Menü komutu tanımlama

Varolan bir hareket veya komut projesine daha fazla menü komut tanımı ekleyebilirsiniz. Her komut, aşağıdaki özelliklere sahip bir sınıf tarafından tanımlanır:

- Sınıfı şu şekilde bildirilmiştir:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`*Mylayercommand* `: ICommandExtension { ... }`

- Ad alanı ve sınıfın adı önemli değildir.

- @No__t_0 uygulayan yöntemler şunlardır:

  - `string Text {get;}`-menüde görünen etiket.

  - `void QueryStatus(IMenuCommand command)`-kullanıcı diyagrama sağ tıkladığında çağrılır ve komutun kullanıcının geçerli seçimi için görünür ve etkin olup olmayacağını belirler.

  - `void Execute(IMenuCommand command)`-Kullanıcı komutu seçtiğinde çağırılır.

- Geçerli seçimi belirleyebilmek için `IDiagramContext` içeri aktarabilirsiniz:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Yeni bir komut eklemek için aşağıdaki örneği içeren yeni bir kod dosyası oluşturun. Sonra test edin ve düzenleyin.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

## <a name="gesture"></a>Hareket Işleyicisi tanımlama

Bir hareket işleyicisi, kullanıcı öğeleri bağımlılık diyagramına sürüklediğinde ve Kullanıcı diyagramda herhangi bir yere çift tıkladığında yanıt verir.

Mevcut komutunuz veya hareket işleyicisi VSıX projeniz için, bir hareket işleyicisini tanımlayan bir kod dosyası ekleyebilirsiniz:

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

Hareket işleyicileri hakkında aşağıdaki noktalara dikkat edin:

- @No__t_0 üyeleri aşağıdaki gibidir:

     **OnDoubleClick** -kullanıcı diyagram üzerinde herhangi bir yere çift tıkladığında çağırılır.

     **CanDragDrop** -Kullanıcı bir öğeyi diyagrama sürüklerken fareyi taşıdıkça sürekli çağırılır. Hızlı çalışması gerekir.

     **OnDragDrop** -kullanıcı diyagram üzerine bir öğe bırakıdüğünde çağırılır.

- Her yöntemin ilk bağımsız değişkeni, katman öğesini alabileceğiniz bir `IShape`. Örneğin:

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

- Bazı sürüklenen öğe türleri için işleyiciler zaten tanımlandı. Örneğin, Kullanıcı Çözüm Gezgini öğeleri bir bağımlılık diyagramına sürükleyebilirsiniz. Bu öğe türleri için bir sürükleme işleyicisi tanımlayamazsınız. Bu durumlarda, `DragDrop` yöntemleriniz çağırılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
