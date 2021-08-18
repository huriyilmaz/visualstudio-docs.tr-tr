---
title: 'Nasıl yapılır: Etki Alanına Özgü Dil Tasarımcısını Genişletme'
description: Etki alanına özgü dil (DSL) Tanımlarını düzenlemek için kullanabileceğiniz tasarımcıya uzantılar yapmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f48f0674ecfe11ac28c8db6ea635fdb4f86ca77d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143397"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Nasıl yapılır: Etki Alanına Özgü Dil Tasarımcısını Genişletme

DSL Tanımlarını düzenlemek için kullanabileceğiniz tasarımcıya uzantılar yapabilirsiniz. Menü komutları ekleme, sürükle ve çift tıklama hareketleri için işleyiciler ekleme ve belirli değer veya ilişki türleri değiştirlendiğinde tetiklenen kurallar gibi uzantı türlerini kullanabilirsiniz. Uzantılar, bir Visual Studio Tümleştirme Uzantısı (VSIX) olarak paket olabilir ve diğer kullanıcılara dağıtılmalarını sağlar.

Örnek kod ve bu özellik hakkında daha fazla bilgi için bkz. Visual Studio [Görselleştirme ve Modelleme SDK'sı.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="set-up-the-solution"></a>Çözümü Ayarlama

Uzantının kodunu içeren bir proje ve projeyi dışarı aktaran bir VSIX projesi ayarlayın. Çözümünüz aynı VSIX'e dahil olan diğer projeleri içerebilir.

### <a name="to-create-a-dsl-designer-extension-solution"></a>DSL Tasarımcısı Uzantısı Çözümü oluşturmak için

1. Sınıf Kitaplığı proje şablonunu kullanarak **yeni bir** proje oluşturun. Bu proje uzantılarının kodunu içerir.

2. Yeni bir **VSIX Project** oluşturun.

     Çözüme **Ekle'yi seçin.**

     *Source.extension.vsixmanifest,* VSIX bildirim düzenleyicisinde açılır.

3. İçerik alanı üzerinde İçerik **Ekle'ye tıklayın.**

4. İçerik Ekle **iletişim kutusunda** MeF Bileşeni olarak bir **İçerik Türü** Seçin'i **ve** **sınıf Project** projenize göre ayarlayın.

5. Sürümleri **Seç'e** tıklayın ve Visual Studio Enterprise **emin** olun.

6. VSIX projesinin çözümün Başlangıç projesi olduğundan emin olun.

7. Sınıf kitaplığı projesinde, aşağıdaki derlemelere başvurular ekleyin:

     Microsoft.VisualStudio.CoreUtility

     Microsoft.VisualStudio.Modeling.Sdk.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     Sistem. Windows. Forms

## <a name="test-and-deployment"></a>Test ve Dağıtım

Bu konu başlığında yer alan uzantıları test etmek için çözümü derleme ve çalıştırma. Deneysel bir Visual Studio açılır. Bu örnekte bir DSL çözümü açın. DslDefinition diyagramını düzenleyin. Uzantı davranışı görülebilir.

Uzantıları ana sunucuya ve Visual Studio bilgisayarlara dağıtmak için şu adımları izleyin:

1. VSIX yükleme dosyasını bin \\ * \\ .vsix dosyasında VSIX \* projesinde bulun

2. Bu dosyayı hedef bilgisayara kopyalayın ve ardından Windows Gezgini'nde (veya Dosya Gezgini) çift tıklayın.

     uzantının Visual Studio onaylamak için Uzantı Yöneticisi açılır.

Uzantıyı kaldırmak için şu adımları izleyin:

1. Visual Studio Araçlar menüsünde **Uzantı** Yöneticisi'ne **tıklayın.**

2. Uzantıyı seçin ve silin.

## <a name="add-a-shortcut-menu-command"></a>Kısayol Menü Komutu Ekleme

Kısayol menü komutunun DSL Tasarımcısı veya DSL Gezgini penceresinde görünmesini yapmak için aşağıdakine benzer bir sınıf yazın.

sınıfı uygulamalı `ICommandExtension` ve özniteliğine sahip `DslDefinitionModelCommandExtension` olmalı.

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Fare Hareketlerini Tutam

Kod, menü komutunun koduna benzer.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Değer Değişikliklerine Yanıt Verme

Bu işleyicinin doğru çalışması için bir etki alanı modeli gerekir. Basit bir etki alanı modeli sağlaruz.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

Aşağıdaki kod basit bir model uygulamaya almaktadır. Yer tutucusunu değiştirmek için yeni bir GUID oluşturun.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```