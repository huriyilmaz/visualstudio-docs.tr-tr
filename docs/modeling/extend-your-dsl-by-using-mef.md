---
title: MEF kullanarak DSL'nizi genişletme
description: Etki alanına özgü dilinizi (DSL) etki alanına özgü dili (MEF) kullanarak Managed Extensibility Framework öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a4572a7210203d6c7525a278430210c954c3405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388886"
---
# <a name="extend-your-dsl-by-using-mef"></a>MEF kullanarak DSL'nizi genişletme

Etki alanına özgü dilinizi (DSL) Managed Extensibility Framework (MEF) kullanarak genişletebilirsiniz. Siz veya diğer geliştiriciler DSL tanımını ve program kodunu değiştirmeden DSL için uzantılar yazabileceksiniz. Bu uzantılar menü komutlarını, sürükleyip bırakma işleyicilerini ve doğrulamayı içerir. Kullanıcılar DSL'nizi yükleyebilir ve isteğe bağlı olarak bunun için uzantılar yükleyebilir.

Ayrıca, DSL'niz içinde MEF'yi etkinleştir yandan, DSL ile birlikte yapılmış olsalar bile DSL'nizin bazı özelliklerini yazmanız daha kolay olabilir.

MEF hakkında daha fazla bilgi için [bkz. Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>DSL'nizin MEF tarafından genişlet extended 'i etkinleştirmek için

1. **DslPackage** projesinin içinde **MefExtension** adlı yeni bir klasör oluşturun. Aşağıdaki dosyaları buna ekleyin:

     Dosya adı: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Bu dosyada GUID'i DslPackage\GeneratedCode\Constants.tt içinde tanımlanan GUID CommandSetId ile aynı olacak şekilde Constants.tt

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

    Bu dosyayı eklersiniz, DSL Gezgini'nde EditorValidation'daki anahtarlardan en az birini kullanarak **DSL'niz için doğrulamayı** etkinleştirmeniz gerekir.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Dosya adı: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Dsl projesinin içinde **MefExtension adlı** yeni bir **klasör** oluşturun. Aşağıdaki dosyaları buna ekleyin:

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

3. **DslPackage\Commands.vsct** adlı mevcut dosyaya aşağıdaki satırı ekleyin:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Satırı var olan yönergeden sonra `<Include>` ekler.

4. *DslDefinition.dsl'i açın.*

5. DSL Gezgini'nde **Düzenleyici\Doğrulama'ya seçin.**

6. Aşağıdaki Özellikler penceresi, Uses adlı özelliklerden en az birinin olduğundan **emin** `true` olun.

7. Uygulama araç **Çözüm Gezgini** Tüm Şablonları **Dönüştür'e tıklayın.**

     Yan kuruluş dosyaları, eklenen dosyaların her biri altında görünür.

8. Hala çalıştığını doğrulamak için çözümü derleme ve çalıştırma.

DSL'niz artık MEF etkindir. Menü komutlarını, hareket işleyicilerini ve doğrulama kısıtlamalarını MEF uzantıları olarak yazabilirsiniz. Bu uzantıları DSL çözümünüzde diğer özel kodlarla birlikte yazabilirsiniz. Ayrıca, siz veya diğer geliştiriciler DSL'nizi genişleten Visual Studio uzantılar yazabilir.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>MEF özellikli DSL için uzantı oluşturma

Kendiniz veya başka biri tarafından oluşturulan MEF özellikli bir DSL'ye erişiminiz varsa, bunun için uzantılar yazabilirsiniz. Uzantılar menü komutları, hareket işleyicileri veya doğrulama kısıtlamaları eklemek için kullanılabilir. Bu uzantıları yazmanız için bir Visual Studio (VSIX) çözümü kullanırsanız. Çözümün iki parçası vardır: kod derlemesini derlemek için bir sınıf kitaplığı projesi ve derlemeyi paketleye bir VSIX projesi.

### <a name="to-create-a-dsl-extension-vsix"></a>DSL uzantısı VSIX oluşturmak için

1. Yeni bir Sınıf **Kitaplığı projesi** oluşturun.

2. Yeni projede DSL derlemesi için bir başvuru ekleyin.

   - Bu derleme genellikle ".Dsl.dll" ile biter.

   - DSL projesine erişiminiz varsa derleme dosyasını Dsl bin dizininin **altında \\ bulabilirsiniz \\ \***

   - DSL VSIX dosyasına erişiminiz varsa, VSIX dosyasının dosya adı uzantısını ".zip" olarak değiştirerek derlemeyi bulabilirsiniz. Dosyanın .zip açın.

3. Aşağıdaki .NET derlemelerine başvurular ekleyin:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Yeni bir **VSIX proje projesi** oluşturun.

5. Bu **Çözüm Gezgini** VSIX projesine sağ tıklayın ve Başlangıç Projesi **Olarak Ayarla'yı seçin.**

6. Yeni projede **source.extension.vsixmanifest'i açın.**

7. İçerik **Ekle'ye tıklayın.** İletişim kutusunda İçerik **Türü'ne** **MEF Bileşeni,** Kaynak **Proje'yi ise** sınıf kitaplığı projenize ayarlayın.

8. DSL'ye vsIX başvurusu ekleyin.

   1. **source.extension.vsixmanifest içinde** Başvuru **Ekle'ye tıklayın.**

   2. İletişim kutusunda Yük **Ekle'ye tıklayın** ve DSL'nin VSIX dosyasını bulun. VSIX dosyası DSL çözümünde, **DslPackage bin içinde \\ yerleşiktir. \\ \***

       Bu, kullanıcıların DSL'i ve uzantınızı aynı anda yüklemelerini sağlar. Kullanıcı DSL'i zaten yüklemişse yalnızca uzantınız yüklenir.

9. **source.extension.vsixmanifest'in diğer alanlarını gözden geçirin ve güncelleştirin.** Sürümleri **Seç'e** tıklayın ve doğru sürümlerin Visual Studio doğru olduğunu doğrulayın.

10. Sınıf kitaplığı projesine kod ekleyin. Sonraki bölümde yer alan örnekleri kılavuz olarak kullanın.

     Herhangi bir sayıda komut, hareket ve doğrulama sınıfı eklemek için kullanabilirsiniz.

11. Uzantıyı test etmek için **F5 tuşuna basın.** Visual Studio'nin deneysel örneğinde DSL'nin örnek bir dosyasını oluşturun veya açın.

## <a name="writing-mef-extensions-for-dsls"></a>DSL'ler için MEF uzantıları yazma

Ayrı bir DSL uzantısı çözümünün derleme kodu projesine uzantılar yazabilirsiniz. DSL'nin bir parçası olarak komut, hareket ve doğrulama kodu yazmanın kullanışlı bir yolu olarak DslPackage projesinde MEF'i de kullanabilirsiniz.

### <a name="menu-commands"></a>Menü Komutları

Bir menü komutu yazmak için, UYGULAYAN bir sınıf tanımlayın ve DSL'niz içinde tanımlanan özniteliğiyle sınıf ön ekini <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> *YourDsl adlı bir sınıf* `CommandExtension` tanımlayın. Birden fazla menü komut sınıfı yazabilirsiniz.

`QueryStatus()` kullanıcı diyagrama sağ tıkladığında çağrılır. Geçerli seçimi incelemeli ve komutun `command.Enabled` ne zaman geçerli olduğunu belirtmek için ayarlan çalışmalı.

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

### <a name="gesture-handlers"></a>Hareket İşleyicileri

Hareket işleyicisi diyagrama sürüklenen nesneleri her yerden, her yerden, her yerden veya dış katmandan Visual Studio. Aşağıdaki örnek, kullanıcının Windows Gezgini'nde dosyaları diyagrama sürüklemesine olanak sağlar. Dosya adlarını içeren öğeler oluşturur.

Diğer DSL modellerinden ve UML modellerinden sürüklenmelerle başa olmak için işleyiciler yazabilirsiniz. Daha fazla bilgi için, [bkz. How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md).

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

Doğrulama yöntemleri DSL tarafından oluşturulan özniteliği ve ayrıca tarafından `ValidationExtension` <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> işaretlenir. yöntemi, bir öznitelikle işaretlenen herhangi bir sınıfta görünebilir.

Daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

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
