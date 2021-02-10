---
title: MEF kullanarak DSL'nizi genişletme
description: Managed Extensibility Framework (MEF) kullanarak etki alanına özgü dili (DSL) nasıl genişletebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 324037010e642ab4e96f6efea5da0f232c9bd530
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935072"
---
# <a name="extend-your-dsl-by-using-mef"></a>MEF kullanarak DSL'nizi genişletme

Managed Extensibility Framework (MEF) kullanarak, etki alanına özgü dili (DSL) genişletebilirsiniz. Siz veya diğer geliştiriciler DSL tanımını ve program kodunu değiştirmeden DSL için Uzantılar yazabilir. Bu tür uzantılara menü komutları, sürükle ve bırak işleyicileri ve doğrulama dahildir. Kullanıcılar DSL 'yi yükleyebilecektir ve isteğe bağlı olarak uzantıları yükleyemez.

Ayrıca, DSL 'niz üzerinde MEF 'i etkinleştirdiğinizde, DSL ile birlikte yerleştirilmiş olsalar bile DSL 'nizin bazı özelliklerini yazmanız daha kolay olabilir.

MEF hakkında daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>DSL 'nin MEF tarafından genişletilmesini sağlamak için

1. **DslPackage** projesi Içinde **MefExtension** adlı yeni bir klasör oluşturun. Aşağıdaki dosyaları bu dosyaya ekleyin:

     Dosya adı: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Bu dosyadaki GUID 'yi DslPackage\GeneratedCode\Constants.tt içinde tanımlanan GUID CommandSetId ile aynı olacak şekilde ayarlayın

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Dosya adı: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Dosya adı: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Dosya adı: `ValidationExtensionRegistrar.tt`

    Bu dosyayı eklerseniz, DSL Explorer 'da **Editorvalidation** içindeki anahtarlardan en az bırını kullanarak DSL 'de doğrulamayı etkinleştirmeniz gerekir.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Dosya adı: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. **DSL** projesi Içinde **MefExtension** adlı yeni bir klasör oluşturun. Aşağıdaki dosyaları bu dosyaya ekleyin:

     Dosya adı: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Dosya adı: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Dosya adı: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Aşağıdaki satırı **Dslpackage\commands.vsct** adlı mevcut dosyaya ekleyin:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Varolan yönergeden sonra satırı ekleyin `<Include>` .

4. *DslDefinition. dsl*'yi açın.

5. DSL Gezgini ' nde **Editor\validation**' ı seçin.

6. Özellikler penceresi, adlı özelliklerden en az birinin **kullandığından** emin olun `true` .

7. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür**' e tıklayın.

     Bağlı olan dosyalar, eklediğiniz her bir dosyanın altında görünür.

8. Hala çalıştığını doğrulamak için çözümü derleyin ve çalıştırın.

DSL 'niz artık MEF etkin. Menü komutlarını, hareket işleyicilerini ve doğrulama kısıtlamalarını MEF uzantıları olarak yazabilirsiniz. Bu uzantıları DSL çözümünüze diğer özel kodla birlikte yazabilirsiniz. Ayrıca, siz veya diğer geliştiriciler DSL 'yi genişleten ayrı Visual Studio uzantıları yazabilir.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>MEF etkin DSL için uzantı oluşturma

Kendiniz veya başka biri tarafından oluşturulan MEF özellikli bir DSL 'ye erişiminiz varsa, bunun için Uzantılar yazabilirsiniz. Uzantılar, menü komutları, hareket işleyicileri veya doğrulama kısıtlamaları eklemek için kullanılabilir. Bu uzantıları yazmak için bir Visual Studio uzantısı (VSıX) çözümü kullanırsınız. Çözüm iki bölümden oluşur: kod derlemesini oluşturan bir sınıf kitaplığı projesi ve derlemeyi paketleyen bir VSıX projesi.

### <a name="to-create-a-dsl-extension-vsix"></a>DSL uzantısı VSıX oluşturmak için

1. Yeni bir **sınıf kitaplığı** projesi oluşturun.

2. Yeni projede, DSL derlemesine bir başvuru ekleyin.

   - Bu derleme genellikle ".Dsl.dll" ile biten bir ada sahiptir.

   - DSL projesine erişiminiz varsa, derleme dosyasını Dizin **DSL \\ bin \\ \*** altında bulabilirsiniz.

   - DSL VSıX dosyasına erişiminiz varsa, VSıX dosyasının dosya adı uzantısını ". zip" olarak değiştirerek derlemeyi bulabilirsiniz. . Zip dosyasını sıkıştırmasını açın.

3. Aşağıdaki .NET derlemelerine başvuruları ekleyin:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Yeni bir **VSIX proje** projesi oluşturun.

5. **Çözüm Gezgini**, VSIX projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

6. Yeni projede, açık **kaynak. Extension. valtmanifest**' i açın.

7. **Içerik Ekle**' ye tıklayın. İletişim kutusunda, **Içerik türünü** **MEF bileşeni** ve **kaynak proje** ' yi sınıf kitaplığı projenize ayarlayın.

8. DSL 'ye bir VSıX başvurusu ekleyin.

   1. **Source. Extension. valtmanifest** Içinde **Başvuru Ekle** ' ye tıklayın.

   2. İletişim kutusunda **Yük Ekle** ' ye tıklayın ve ardından dsl dosyasının VSIX dosyasını bulun. VSıX dosyası, **DslPackage \\ bin \\ \***' de DSL çözümünde yerleşiktir.

       Bu, kullanıcıların DSL 'yi ve uzantınızı aynı anda yüklemesine olanak tanır. Kullanıcı DSL 'yi zaten yüklemiştir, yalnızca uzantınızın yüklenmesi gerekir.

9. **Kaynak. Extension. valtmanifest**'in diğer alanlarını gözden geçirin ve güncelleştirin. **Sürümleri Seç** ' e tıklayın ve doğru Visual Studio sürümlerinin ayarlandığını doğrulayın.

10. Sınıf kitaplığı projesine kod ekleyin. Bir sonraki bölümdeki örnekleri kılavuz olarak kullanın.

     İstediğiniz sayıda komut, hareket ve doğrulama sınıfı ekleyebilirsiniz.

11. Uzantıyı test etmek için **F5**'e basın. Visual Studio 'nun deneysel örneğinde, DSL 'nin örnek bir dosyasını oluşturun veya açın.

## <a name="writing-mef-extensions-for-dsls"></a>DSLs için MEF uzantıları yazılıyor

Ayrı bir DSL uzantısı çözümünün derleme kodu projesinde uzantı yazabilirsiniz. Ayrıca, DSL 'nin bir parçası olarak komutları, hareketleri ve doğrulama kodunu yazmak için uygun bir yol olarak DslPackage projenizde MEF kullanabilirsiniz.

### <a name="menu-commands"></a>Menü Komutları

Bir menü komutu yazmak için, bir sınıfı, uygulayan <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> ve DSL ADLı DSL adında tanımlanmış olan özniteliğe önek olarak tanımlayın  `CommandExtension` . Birden fazla menü komut sınıfı yazabilirsiniz.

`QueryStatus()` kullanıcının diyagrama sağ tıkladığı her zaman çağrılır. Geçerli seçimi incelemelidir ve `command.Enabled` komutun ne zaman geçerli olduğunu belirtecek şekilde ayarlanmalıdır.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Hareket Işleyicileri

Bir hareket işleyicisi, Visual Studio 'Nun içindeki veya dışındaki her yerden diyagram üzerine sürüklenen nesneler ile başa geçirilebilirler. Aşağıdaki örnek, kullanıcının Windows Gezgini 'ndeki dosyaları diyagram üzerine sürükleyebilmenizi sağlar. Dosya adlarını içeren öğeleri oluşturur.

Diğer DSL modellerinden ve UML modellerinden sürüklerle başa çıkmak için işleyiciler yazabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Doğrulama kısıtlamaları

Doğrulama yöntemleri `ValidationExtension` DSL tarafından oluşturulan öznitelik tarafından ve ayrıca tarafından işaretlenir <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Yöntemi bir öznitelik tarafından işaretlenmemiş herhangi bir sınıfta bulunabilir.

Daha fazla bilgi için bkz. [Domain-Specific dilinde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Uzantıları Gönderme](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Etki Alanına Özgü bir Dilde Doğrulama](../modeling/validation-in-a-domain-specific-language.md)
