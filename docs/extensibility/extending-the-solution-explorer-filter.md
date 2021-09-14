---
title: Çözüm Gezgini Filtresini Genişletme | Microsoft Docs
description: Visual Studio SDK'Çözüm Gezgini farklı dosyaları göstermek veya gizlemek için filtre işlevlerini genişletmeyi öğrenin.
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
ms.openlocfilehash: e2c41830892b6199a5cd844b365898efa83c83fb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634630"
---
# <a name="extend-the-solution-explorer-filter"></a>Uygulama filtresini Çözüm Gezgini genişletme
Farklı dosyaları **Çözüm Gezgini** veya gizleyebilirsiniz. Örneğin, bu kılavuzda da gösterdiği gibi, yalnızca Çözüm Gezgini C# sınıf fabrika dosyalarını gösteren bir filtre oluşturabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-visual-studio-package-project"></a>Bir Visual Studio paketi projesi oluşturma

1. adlı bir VSIX projesi `FileFilter` oluşturun. FileFilter adlı özel bir komut öğesi **şablonu ekleyin.** Daha fazla bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. ve için bir başvuru `System.ComponentModel.Composition` `Microsoft.VisualStudio.Utilities` ekleyin.

3. Menü komutunun araç çubuğunda görünmesini **Çözüm Gezgini.** *FileFilterPackage.vsct dosyasını* açın.

4. Bloğu `<Button>` aşağıdaki gibi değiştirme:

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

1. *source.extension.vsixmanifest* dosyasında MEF bileşeni olan bir varlık ekleyin.

2. Varlıklar **sekmesinde** Yeni **düğmesini** seçin.

3. Tür **alanında** **Microsoft.VisualStudio.MefComponent'ı seçin.**

4. Kaynak **alanında Geçerli** çözümde **bir proje'yi seçin.**

5. Yeni **Project** DosyaFiltre'yi ve ardından Tamam **düğmesini** seçin.

### <a name="add-the-filter-code"></a>Filtre kodunu ekleme

1. *FileFilterPackageGuids.cs dosyasına bazı GUID'ler* ekleyin:

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. FileFilter projesine *FileNameFilter.cs adlı bir sınıf dosyası ekleyin.*

3. Boş ad alanını ve boş sınıfı aşağıdaki kodla değiştirin.

     yöntemi, çözümün kökünü ( ) içeren koleksiyonu alır ve filtreye `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` dahil edilecek öğe koleksiyonunu `rootItems` döndürür.

     yöntemi, `ShouldIncludeInFilter` belirttiğiniz koşula **Çözüm Gezgini** hiyerarşideki öğeleri filtreler.

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

4. *FileFilter.cs dosyasında,* Komut yerleştirme ve işleme kodunu FileFilter oluşturucusndan kaldırın. Sonuç aşağıdaki gibi görünüyor olmalı:

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

     yöntemini `ShowMessageBox()` de kaldırın.

5. *FileFilterPackage.cs içinde,* yönteminde yer `Initialize()` alan kodu aşağıdakiyle değiştirin:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Kodunuza test etme

1. Projeyi derleme ve çalıştırma. İkinci bir örnek Visual Studio görüntülenir. Bu, deneysel örnek olarak adlandırılan bir örnek.

2. Deneysel Visual Studio bir C# projesi açın.

3. Araç çubuğunda ekley istediğiniz **düğmeyi Çözüm Gezgini** bakın. Sol tarafta dördüncü düğme olması gerekir.

4. Düğmeye tıklarken tüm dosyaların filtrelenmiş olması ve Tüm öğelerin görünümden **filtrelenmiş olduğunu görüyoruz.** içinde **Çözüm Gezgini.**
