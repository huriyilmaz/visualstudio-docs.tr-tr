---
title: Çözüm Gezgini filtresini genişletme | Microsoft Docs
description: Visual Studio SDK 'sında farklı dosyaları göstermek veya gizlemek için Çözüm Gezgini filtre işlevini genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e0d9b7a3f3dcd1f3641d65a26e9919621cff15f7fcfff5f9968dc692769d2b53
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121275976"
---
# <a name="extend-the-solution-explorer-filter"></a>Çözüm Gezgini filtresini uzat
Farklı dosyaları göstermek veya gizlemek için **Çözüm Gezgini** filtre işlevini genişletebilirsiniz. Örneğin, bu kılavuzda gösterdiği gibi yalnızca **Çözüm Gezgini** C# sınıf fabrikası dosyalarını gösteren bir filtre oluşturabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Visual Studio paket projesi oluşturma

1. Adlı bir VSıX projesi oluşturun `FileFilter` . **FileFilter** adlı özel bir komut öğesi şablonu ekleyin. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Ve için bir başvuru `System.ComponentModel.Composition` ekleyin `Microsoft.VisualStudio.Utilities` .

3. Menü komutunun **Çözüm Gezgini** araç çubuğunda görünmesini sağlayın. *FileFilterPackage. vsct* dosyasını açın.

4. `<Button>`Bloğu aşağıdaki şekilde değiştirin:

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

1. *Source. Extension. valtmanifest* dosyasında, MEF bileşeni olan bir varlık ekleyin.

2. **Varlıklar** sekmesinde **Yeni** düğmesini seçin.

3. **Tür** alanında, **Microsoft. VisualStudio. MefComponent** öğesini seçin.

4. **Kaynak** alanında, **Geçerli çözümde bir proje** seçin.

5. **Project** alanında, **FileFilter**' ı seçin ve ardından **tamam** düğmesini seçin.

### <a name="add-the-filter-code"></a>Filtre kodunu ekleyin

1. *Filefilterpackageguid 'ler. cs* dosyasına bazı GUID 'ler ekleyin:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. *FileNameFilter. cs* adlı FileFilter projesine bir sınıf dosyası ekleyin.

3. Boş ad alanını ve boş sınıfı aşağıdaki kodla değiştirin.

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`Yöntemi çözümün kökünü içeren koleksiyonu alır ( `rootItems` ) ve filtreye dahil edilecek öğelerin koleksiyonunu döndürür.

     `ShouldIncludeInFilter`Yöntemi, **Çözüm Gezgini** hiyerarşisindeki öğeleri belirttiğiniz koşula göre filtreler.

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

4. *FileFilter. cs* dosyasında, komut yerleşimini ve Işleme kodunu FileFilter oluşturucusundan kaldırın. Sonuç şöyle görünmelidir:

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

     `ShowMessageBox()`Yöntemi de kaldırın.

5. *FileFilterPackage. cs* dosyasında, yöntemindeki kodu aşağıdaki gibi değiştirin `Initialize()` :

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Kodunuza test etme

1. Projeyi derleyin ve çalıştırın. ikinci bir Visual Studio örneği görüntülenir. Bu, deneysel örnek olarak adlandırılır.

2. Visual Studio deneysel örneğinde bir C# projesi açın.

3. **Çözüm Gezgini** araç çubuğuna eklediğiniz düğmeyi arayın. Sol taraftaki dördüncü düğme olmalıdır.

4. Düğmeye tıkladığınızda, tüm dosyalar filtrelenmelidir ve **tüm öğelerin görünümden filtrelendiğine bakabilirsiniz.** **Çözüm Gezgini**.
