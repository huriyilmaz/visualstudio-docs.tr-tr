---
title: 'Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama'
description: Etki alanına özgü diliniz için bir komut veya hareket işleyicisi yazdığınızda kullanıcının sağ tıkladığını nasıl belirleyebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, accessing the current selection
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 83903c8ff911fdd1d4900714137a7f6976513dad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890571"
---
# <a name="how-to-access-and-constrain-the-current-selection"></a>Nasıl yapılır: Geçerli Seçime Erişme ve Seçimi Kısıtlama

Etki alanına özgü diliniz için bir komut veya hareket işleyicisi yazdığınızda, kullanıcının sağ tıkladığını belirleyebilirsiniz. Ayrıca, bazı şekillerin veya alanların seçilmesini engelleyebilirsiniz. Örneğin, Kullanıcı bir simge dekoratörü tıkladığı zaman, bunun yerine onu içeren şeklin seçili olduğunu düzenleyebilirsiniz. Seçimi bu şekilde kısıtlama, yazmanız gereken işleyicilerin sayısını azaltır. Ayrıca, kullanıcının dekoratmayı önlemek zorunda kalmadan şeklin içinde herhangi bir yere tıklaması için de daha kolay hale gelir.

## <a name="access-the-current-selection-from-a-command-handler"></a>Geçerli seçime bir komut Işleyicisinden erişin

Bir alana özgü dilin komut kümesi sınıfı, özel komutlarınız için komut işleyicilerini içerir. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Etki alanına özgü dil için komut kümesi sınıfına türettiği sınıf, geçerli seçime erişmek için birkaç üye sağlar.

Komuta bağlı olarak, komut işleyicisinin model tasarımcısında, model Gezgininde veya etkin pencerede seçim yapması gerekebilir.

### <a name="to-access-selection-information"></a>Seçim bilgilerine erişmek için

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>Sınıfı, geçerli seçime erişmek için kullanılabilecek aşağıdaki üyeleri tanımlar.

    |Üye|Description|
    |-|-|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsAnyDocumentSelectionCompartment%2A> yöntemi|`true`Model tasarımcısında seçili öğelerden herhangi biri bir bölme şekli ise, aksi takdirde, döndürür `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsDiagramSelected%2A> yöntemi|`true`Şema, model tasarımcısında seçiliyse döndürür; Aksi takdirde, `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleDocumentSelection%2A> yöntemi|`true`Model tasarımcısında tam olarak bir öğe seçildiyse, aksi takdirde, döndürür `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.IsSingleSelection%2A> yöntemi|`true`Etkin pencerede tam olarak bir öğe seçildiyse, aksi takdirde, döndürür `false` .|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentDocumentSelection%2A> özelliði|Model tasarımcısında seçilen öğelerin salt okunurdur bir koleksiyonunu alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.CurrentSelection%2A> özelliði|Etkin pencerede seçili öğelerin salt okunurdur bir koleksiyonunu alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleDocumentSelection%2A> özelliði|Model tasarımcısında seçimin birincil öğesini alır.|
    |<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.SingleSelection%2A> özelliði|Etkin pencerede Seçilenin birincil öğesini alır.|

2. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet.CurrentDocView%2A>Sınıfının özelliği, <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView> Model Tasarımcısı penceresini temsil eden nesneye erişim sağlar ve model tasarımcısında seçili öğelere ek erişim sağlar.

3. Ayrıca, oluşturulan kod, bir gezgin araç penceresi özelliği ve etki alanına özgü dilin komut kümesi sınıfında bir gezgin seçimi özelliği tanımlar.

    - Gezgin araç penceresi özelliği, etki alanına özgü dil için Gezgin araç penceresi sınıfının bir örneğini döndürür. Gezgin araç penceresi sınıfı <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow> sınıfından türetilir ve etki alanına özgü dilin model Gezginini temsil eder.

    - `ExplorerSelection`Özelliği, etki alanına özgü dil için Model Gezgini penceresinde seçili öğeyi döndürür.

## <a name="determine-which-window-is-active"></a>Hangi pencerenin etkin olduğunu belirleme

<xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>Arabirim, kabukta geçerli seçim durumuna erişim sağlayan üyeleri tanımlar. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> `MonitorSelection` Her birinin temel sınıfında tanımlanan özelliği aracılığıyla, paket sınıfından veya etki alanına özgü dilin komut kümesi sınıfından bir nesne alabilirsiniz. Paket sınıfı sınıfından türetilir <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage> ve komut kümesi sınıfı <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> sınıfından türetilir.

### <a name="to-determine-from-a-command-handler-what-type-of-window-is-active"></a>Bir komut işleyicisinden ne tür bir pencere etkin olduğunu belirlemek için

1. <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSetLibrary.MonitorSelection%2A>Sınıfının özelliği, <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> kabukta geçerli seçim durumuna erişim sağlayan bir nesne döndürür.

2. <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService.CurrentSelectionContainer%2A>Arabirim özelliği etkin <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService> pencereden farklı olabilen etkin seçim kapsayıcısını alır.

3. Hangi tür pencerenin etkin olduğunu belirlemek için, etki alanına özgü dil için komut kümesi sınıfına aşağıdaki özellikleri ekleyin.

    ```csharp
    // using Microsoft.VisualStudio.Modeling.Shell;

    // Returns true if the model designer is the active selection container;
    // otherwise, false.
    protected bool IsDesignerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is DiagramDocView);
        }
    }

    // Returns true if the model explorer is the active selection container;
    // otherwise, false.
    protected bool IsExplorerActive
    {
        get
        {
            return (this.MonitorSelection.CurrentSelectionContainer
                is ModelExplorerToolWindow);
        }
    }
    ```

## <a name="constrain-the-selection"></a>Seçimi sınırlama

Seçim kuralları ekleyerek, Kullanıcı modelde bir öğe seçtiğinde hangi öğelerin seçili olduğunu denetleyebilirsiniz. Örneğin, kullanıcının bir dizi öğeyi tek bir birim olarak ele almasını sağlamak için bir seçim kuralı kullanabilirsiniz.

### <a name="to-create-a-selection-rule"></a>Seçim kuralı oluşturmak için

1. DSL projesinde özel bir kod dosyası oluşturma

2. Sınıfından türetilmiş bir seçim kuralı sınıfı tanımlayın <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules> .

3. Seçim <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules.GetCompliantSelection%2A> ölçütlerini uygulamak için seçim kuralı sınıfının yöntemini geçersiz kılın.

4. Özel kod dosyanıza ClassDiagram sınıfı için kısmi bir sınıf tanımı ekleyin.

     `ClassDiagram`Sınıfı sınıfından türetilir <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram> ve DSL projesindeki Diagram.cs oluşturulan kod dosyasında tanımlanmıştır.

5. <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> `ClassDiagram` Özel seçim kuralını döndürmek için sınıfının özelliğini geçersiz kılın.

     Özelliğin varsayılan uygulanması, <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram.SelectionRules%2A> seçimi değiştirmayan bir seçim kuralı nesnesi alır.

### <a name="example"></a>Örnek

Aşağıdaki kod dosyası, seçimi başlangıçta seçili olan her bir etki alanı şekillerinin tüm örneklerini içerecek şekilde genişleten bir seçim kuralı oluşturur.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

namespace CompanyName.ProductName.GroupingDsl
{
    public class CustomSelectionRules : DiagramSelectionRules
    {
        protected Diagram diagram;
        protected IElementDirectory elementDirectory;

        public CustomSelectionRules(Diagram diagram)
        {
            if (diagram == null) throw new ArgumentNullException();

            this.diagram = diagram;
            this.elementDirectory = diagram.Store.ElementDirectory;
        }

        /// <summary>Called by the design surface to allow selection filtering.
        /// </summary>
        /// <param name="currentSelection">[in] The current selection before any
        /// ShapeElements are added or removed.</param>
        /// <param name="proposedItemsToAdd">[in/out] The proposed DiagramItems to
        /// be added to the selection.</param>
        /// <param name="proposedItemsToRemove">[in/out] The proposed DiagramItems
        /// to be removed from the selection.</param>
        /// <param name="primaryItem">[in/out] The proposed DiagramItem to become
        /// the primary DiagramItem of the selection. A null value signifies that
        /// the last DiagramItem in the resultant selection should be assumed as
        /// the primary DiagramItem.</param>
        /// <returns>true if some or all of the selection was accepted; false if
        /// the entire selection proposal was rejected. If false, appropriate
        /// feedback will be given to the user to indicate that the selection was
        /// rejected.</returns>
        public override bool GetCompliantSelection(
            SelectedShapesCollection currentSelection,
            DiagramItemCollection proposedItemsToAdd,
            DiagramItemCollection proposedItemsToRemove,
            DiagramItem primaryItem)
        {
            if (currentSelection.Count == 0 && proposedItemsToAdd.Count == 0) return true;

            HashSet<DomainClassInfo> itemsToAdd = new HashSet<DomainClassInfo>();

            foreach (DiagramItem item in proposedItemsToAdd)
            {
                if (item.Shape != null)
                    itemsToAdd.Add(item.Shape.GetDomainClass());
            }
            proposedItemsToAdd.Clear();
            foreach (DomainClassInfo classInfo in itemsToAdd)
            {
                foreach (ModelElement element
                    in this.elementDirectory.FindElements(classInfo, false))
                {
                    if (element is ShapeElement)
                    {
                        proposedItemsToAdd.Add(
                            new DiagramItem((ShapeElement)element));
                    }
                }
            }

            return true;
        }
    }

    public partial class ClassDiagram
    {
        protected CustomSelectionRules customSelectionRules = null;

        protected bool multipleSelectionMode = true;

        public override DiagramSelectionRules SelectionRules
        {
            get
            {
                if (multipleSelectionMode)
                {
                    if (customSelectionRules == null)
                    {
                        customSelectionRules = new CustomSelectionRules(this);
                    }
                    return customSelectionRules;
                }
                else
                {
                    return base.SelectionRules;
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelingPackage>
- <xref:Microsoft.VisualStudio.Modeling.Shell.DiagramDocView>
- <xref:Microsoft.VisualStudio.Modeling.Shell.ModelExplorerToolWindow>
- <xref:Microsoft.VisualStudio.Modeling.Shell.IMonitorSelectionService>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.DiagramSelectionRules>
- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>