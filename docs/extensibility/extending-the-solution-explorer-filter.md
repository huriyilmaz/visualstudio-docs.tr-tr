---
title: Çözüm Gezgini Filtresini Genişletme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711565"
---
# <a name="extend-the-solution-explorer-filter"></a>Çözüm Gezgini filtresini genişletme
Farklı dosyaları göstermek veya gizlemek için **Solution Explorer** filtresi işlevini genişletebilirsiniz. Örneğin, **çözüm**gezgininde yalnızca C# sınıfı fabrika dosyalarını gösteren bir filtre oluşturabilirsiniz , bu izbisin gösterdiği gibi.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-visual-studio-package-project"></a>Visual Studio paket projesi oluşturma

1. Adlı `FileFilter`bir VSIX projesi oluşturun. **FileFilter**adlı özel bir komut öğesi şablonu ekleyin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Bir referans `System.ComponentModel.Composition` ekleyin `Microsoft.VisualStudio.Utilities`ve .

3. Menü komutunu Çözüm **Gezgini** araç çubuğunda görünmesini sağlayabilir. *FileFilterPackage.vsct* dosyasını açın.

4. Bloğu `<Button>` aşağıdakiyle değiştirin:

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Bildirim dosyasını güncelleştirme

1. *source.extension.vsixmanifest* dosyasında, MEF bileşeni olan bir varlık ekleyin.

2. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

3. **Tür** alanında **Microsoft.VisualStudio.MefComponent'u**seçin.

4. **Kaynak** alanında, **geçerli çözümde Bir proje**seçin.

5. **Proje** alanında **FileFilter'i**seçin ve ardından **Tamam** düğmesini seçin.

### <a name="add-the-filter-code"></a>Filtre kodu ekleme

1. *FileFilterPackageGuids.cs* dosyasına bazı GUID'ler ekleyin:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. *FileNameFilter.cs*adlı FileFilter projesine bir sınıf dosyası ekleyin.

3. Boş ad alanını ve boş sınıfı aşağıdaki kodla değiştirin.

     Yöntem, `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` çözümün`rootItems`() kökünü içeren koleksiyonu alır ve filtreye eklenecek öğelerin koleksiyonunu döndürür.

     Yöntem, `ShouldIncludeInFilter` **çözüm** gezgini hiyerarşisindeki öğeleri belirttiğiniz koşula göre filtreler.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. *FileFilter.cs,* komut yerleşimi ve işleme kodunu FileFilter oluşturucusundan kaldırın. Sonuç şu şekilde görünmelidir:

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     `ShowMessageBox()` Yöntemi de kaldırın.

5. *FileFilterPackage.cs,* yöntemdeki `Initialize()` kodu aşağıdakilerle değiştirin:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Kodunuza test etme

1. Projeyi oluşturun ve çalıştırın. Visual Studio'nun ikinci bir örneği görüntülenir. Buna deneysel örnek denir.

2. Visual Studio'nun deneysel örneğinde bir C# projesi açın.

3. **Solution Explorer** araç çubuğuna eklediğiniz düğmeyi arayın. Soldan dördüncü düğme olmalı.

4. Düğmeyi tıklattığınızda, tüm dosyalar filtrelenmeli ve **tüm öğelerin görünümden filtrelendiğini** görmeniz gerekir. Çözüm **Explorer'da**.
