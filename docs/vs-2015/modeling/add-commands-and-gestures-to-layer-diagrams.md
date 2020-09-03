---
title: Katman diyagramlarına komut ve hareket ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, adding custom commands
- layer diagrams, adding custom gestures
ms.assetid: ac9c417b-0b40-4a90-86f5-ee3cbdce030b
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7b0c54975cdd5bc86f77dddbd5ca1a56c1896394
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655314"
---
# <a name="add-commands-and-gestures-to-layer-diagrams"></a>Katman diyagramlarına komut ve hareket ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da katman diyagramlarında bağlam menüsü komutları ve hareket işleyicileri tanımlayabilirsiniz. Bu uzantıları, diğer Visual Studio kullanıcılarına dağıtabileceğiniz bir Visual Studio Tümleştirme Uzantısı 'na (VSıX) paketleyebilirsiniz.

 İsterseniz aynı Visual Studio projesinde birkaç komut ve hareket işleyicisi tanımlayabilirsiniz. Ayrıca, bu gibi birçok projeyi tek bir VSıX içinde birleştirebilirsiniz. Örneğin, katman komutları, etki alanına özgü dil ve UML diyagramları için komutlar içeren tek bir VSıX tanımlayabilirsiniz.

> [!NOTE]
> Ayrıca, kullanıcıların kaynak kodunun katman diyagramlarıyla karşılaştırıldığı mimari doğrulamasını özelleştirebilirsiniz. Mimari doğrulamayı ayrı bir Visual Studio projesinde tanımlamanız gerekir. Diğer uzantılarla aynı VSıX 'e ekleyebilirsiniz. Daha fazla bilgi için bkz. [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Gereksinimler
 [Gereksinimlere](../modeling/extend-layer-diagrams.md#prereqs)bakın.

## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Yeni bir VSıX 'te komut veya hareket tanımlama
 Uzantı oluşturmanın en hızlı yöntemi, proje şablonunu kullanmaktır. Bu, kodu ve VSıX bildirimini aynı projeye koyar.

#### <a name="to-define-an-extension-by-using-a-project-template"></a>Bir proje şablonu kullanarak bir uzantı tanımlamak için

1. **Dosya** menüsündeki **Yeni proje** komutunu kullanarak yeni bir çözümde bir proje oluşturun.

2. **Yeni proje** iletişim kutusunda, **modelleme projeleri**altında **Katman Tasarımcısı komut uzantısı** ya da **Katman Tasarımcısı hareket uzantısı**' nı seçin.

    Şablon küçük bir çalışma örneği içeren bir proje oluşturur.

3. Uzantıyı test etmek için **CTRL + F5** veya **F5**tuşlarına basın.

    Deneysel bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] başlar. Bu örnekte, bir katman diyagramı oluşturun. Komut veya hareket uzantınızın bu diyagramda çalışması gerekir.

4. Deneysel örneği kapatın ve örnek kodu değiştirin. Daha fazla bilgi için bkz. [Program kodundaki katman modellerini gezinme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md).

5. Aynı projeye daha fazla komut veya hareket işleyicisi ekleyebilirsiniz. Daha fazla bilgi için, aşağıdaki bölümlerden birine bakın:

    [Menü komutu tanımlama](#command)

    [Hareket Işleyicisi tanımlama](#gesture)

6. Uzantıyı ana örneğine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya başka bir bilgisayara yüklemek için, *bin \\ *içinde **. vsix** dosyasını bulun. Onu yüklemek istediğiniz bilgisayara kopyalayın ve çift tıklayın. Kaldırmak için, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler** ' i kullanın.

## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Ayrı bir VSıX 'e komut veya hareket ekleme
 Komutları, katman Doğrulayıcıları ve diğer uzantıları içeren bir VSıX oluşturmak istiyorsanız, VSıX tanımlamak için bir proje oluşturmanızı ve işleyiciler için ayrı projeler oluşturmanızı öneririz. Diğer modelleme uzantısı türleri hakkında daha fazla bilgi için bkz. [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md).

#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Ayrı bir VSıX 'e katman uzantıları eklemek için

1. Yeni veya mevcut bir Visual Studio çözümünde bir sınıf kitaplığı projesi oluşturun. **Yeni proje** iletişim kutusunda, **Visual C#** ' ye ve ardından **sınıf kitaplığı**' na tıklayın. Bu proje komut veya hareket işleyicisi sınıfları içerecektir.

    > [!NOTE]
    > Tek bir sınıf kitaplığında birden fazla komut veya hareket işleyicisi sınıfı tanımlayabilirsiniz, ancak katman doğrulama sınıflarını ayrı bir sınıf kitaplığında tanımlamanız gerekir.

2. Çözümünüzde bir VSıX projesi oluşturun veya oluşturun. VSıX projesi, **kaynak. Extension. valtmanifest**adlı bir dosya içerir. VSıX projesi eklemek için:

    1. **Yeni proje** iletişim kutusunda, **Visual C#**' ı genişletin, ardından **genişletilebilirlik**' e ve **VSIX projesi**' ne tıklayın.

    2. Çözüm Gezgini, VSıX projesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla**' ya tıklayın.

    3. **Sürümleri Seç** ' e tıklayın ve **Visual Studio 'nun** işaretli olduğundan emin olun.

3. **Source. Extension. valtmanifest**Içinde, **varlıklar**altında, komut veya hareket işleyicisi projesini MEF bileşeni olarak ekleyin.

    1. **Varlıklar**. sekmesinde **Yeni**' yi seçin.

    2. **Türünde**, **Microsoft. VisualStudio. MefComponent**öğesini seçin.

    3. **Kaynakta**, **Geçerli çözümde proje** ' yi seçin ve komut veya hareket işleyicisi projenizin adını seçin.

    4. Dosyayı kaydedin.

4. Komut veya hareket işleyicisi projesine dönün ve aşağıdaki proje başvurularını ekleyin.

|**Başvuru**|**Bunu yapmanıza izin verir**|
|-------------------|------------------------------------|
|Program Files\Microsoft Visual Studio [sürüm] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Katmanları oluşturma ve düzenleme|
|Microsoft. VisualStudio. Uml. Interfaces|Katmanları oluşturma ve düzenleme|
|Microsoft. VisualStudio. mimari Turetools. Extensibility|Diyagramlarda şekilleri değiştirme|
|System. ComponentModel. Composition|Managed Extensibility Framework kullanarak bileşenleri tanımlama (MEF)|
|Microsoft. VisualStudio. model. SDK. sürümünüze|Modelleme uzantıları tanımlama|
|Microsoft. VisualStudio. model. SDK. diyagramlar. sürümünüze|Şekilleri ve diyagramları güncelleştirme|

1. Uzantınızın kodunu içerecek şekilde C# Sınıf Kitaplığı projesindeki sınıf dosyasını düzenleyin. Daha fazla bilgi için, aşağıdaki bölümlerden birine bakın:

     [Menü komutu tanımlama](#command)

     [Hareket Işleyicisi tanımlama](#gesture)

     Ayrıca bkz. [Program kodundaki katman modellerini de gezinme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md).

2. Özelliği test etmek için CTRL + F5 veya F5 tuşlarına basın. Deneysel bir örneği [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] açılır. Bu örnekte, bir katman diyagramı oluşturun veya açın.

3. VSıX [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ' i ana örneğine veya başka bir bilgisayara yüklemek IÇIN VSIX projesinin **bin** dizininde **. vsix** dosyasını bulun. VSıX 'i yüklemek istediğiniz bilgisayara kopyalayın. Windows Gezgini 'nde (Windows 8 ' de dosya Gezgini) VSıX dosyasına çift tıklayın.

     Kaldırmak için, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler** ' i kullanın.

## <a name="defining-a-menu-command"></a><a name="command"></a> Menü komutu tanımlama
 Varolan bir hareket veya komut projesine daha fazla menü komut tanımı ekleyebilirsiniz. Her komut, aşağıdaki özelliklere sahip bir sınıf tarafından tanımlanır:

- Sınıfı şu şekilde bildirilmiştir:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *Mylayerkomutu*  `: ICommandExtension { ... }`

- Ad alanı ve sınıfın adı önemli değildir.

- Uygulayan yöntemler şunlardır `ICommandExtension` :

  - `string Text {get;}` -Menüde görünen etiket.

  - `void QueryStatus(IMenuCommand command)` -Kullanıcı diyagrama sağ tıkladığında çağrılır ve komutun kullanıcının geçerli seçimi için görünür ve etkin olup olmayacağını belirler.

  - `void Execute(IMenuCommand command)` -Kullanıcı komutu seçtiğinde çağırılır.

- Geçerli seçimi belirleyebilmek için şunları içeri aktarabilirsiniz `IDiagramContext` :

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

  Daha fazla bilgi için bkz. [Program kodundaki katman modellerini gezinme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md).

  Yeni bir komut eklemek için aşağıdaki örneği içeren yeni bir kod dosyası oluşturun. Sonra test edin ve düzenleyin.

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for Layer diagrams:
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

## <a name="defining-a-gesture-handler"></a><a name="gesture"></a> Hareket Işleyicisi tanımlama
 Bir hareket işleyicisi, kullanıcı öğeleri katman diyagramına sürüklediğinde ve Kullanıcı diyagramda herhangi bir yere çift tıkladığında yanıt verir.

 Mevcut komutunuz veya hareket işleyicisi VSıX projeniz için, bir hareket işleyicisini tanımlayan bir kod dosyası ekleyebilirsiniz:

```
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

- Üyeleri aşağıdaki gibidir `IGestureExtension` :

   **OnDoubleClick** -kullanıcı diyagram üzerinde herhangi bir yere çift tıkladığında çağırılır.

   **CanDragDrop** -Kullanıcı bir öğeyi diyagrama sürüklerken fareyi taşıdıkça sürekli çağırılır. Hızlı çalışması gerekir.

   **OnDragDrop** -kullanıcı diyagram üzerine bir öğe bırakıdüğünde çağırılır.

- Her yöntemin ilk bağımsız değişkeni, `IShape` katman öğesini alabileceğiniz bir öğesidir. Örneğin:

  ```
  public void OnDragDrop(IShape target, IDataObject data)
  {
      ILayerElement element = target.GetLayerElement();
      if (element is ILayer)
      {
          // ...
      }
  }
  ```

- Bazı sürüklenen öğe türleri için işleyiciler zaten tanımlandı. Örneğin, Kullanıcı Çözüm Gezgini öğeleri bir katman diyagramına sürükleyebilirsiniz. Bu öğe türleri için bir sürükleme işleyicisi tanımlayamazsınız. Bu durumlarda, `DragDrop` yöntemleriniz çağırılmaz.

  Diyagram üzerine sürüklendiğinde diğer öğelerin kodunu çözme hakkında daha fazla bilgi için bkz. [Modelleme diyagramında hareket Işleyicisi tanımlama](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Program kodundaki katman modellerine gitme ve güncelleştirme](../modeling/navigate-and-update-layer-models-in-program-code.md) , [Katman diyagramlarına özel mimari doğrulaması ekleme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md) [bir modelleme uzantısı tanımlama ve yüklemeyi](../modeling/define-and-install-a-modeling-extension.md)
