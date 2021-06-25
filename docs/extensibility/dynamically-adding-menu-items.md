---
title: Menü Öğelerini Dinamik Olarak | Microsoft Docs
description: Çalışma zamanında menü öğeleri eklemek için DynamicItemStart komut bayrağını kullanmayı öğrenin. Bu makalede bir çözümde başlangıç projesinin nasıl ayar Visual Studio gösterir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6867baafa45ca794f65b4cb0cc365dbebfbd4219
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898363"
---
# <a name="dynamically-add-menu-items"></a>Menü öğelerini dinamik olarak ekleme
Visual Studio komut tablosu ( .vsct ) dosyasındaki bir yer tutucu düğme tanımında komut bayrağını belirterek, sonra da (kodda) komut görüntüleniyor ve işleniyor menü öğesi sayısını tanımlayarak çalışma zamanında menü öğeleri `DynamicItemStart` ekleyebilirsiniz. VSPackage yüklendiğinde yer tutucu, dinamik menü öğeleriyle değiştirilir.

 Visual Studio, en son açılan belgelerin adlarını ve şu anda açık olan **pencerelerin** adlarını görüntüleyen Windows listesini görüntüleyen En Son Kullanılan  (MRU) listesinde dinamik listeleri kullanır.   Komut `DynamicItemStart` tanımında bayrağı, VSPackage açılana kadar komutun bir yer tutucu olduğunu belirtir. VSPackage açıldığında yer tutucu, çalışma zamanında oluşturulan ve dinamik listeye eklenen 0 veya daha fazla komutla değiştirilir. VSPackage açılana kadar dinamik listenin göründüğü menü konumunu göreyemebilirsiniz.  Dinamik listeyi doldurmak için Visual Studio VSPackage'dan ilk karakterleri yer tutucu kimliğinin kimliğiyle aynı olan bir kimli komutu aramalıdır. Bu Visual Studio eşleşen bir komut bulduğunda, komutun adını dinamik listeye ekler. Ardından kimliği artırır ve daha fazla dinamik komut olana kadar dinamik listeye eklemek için eşleşen başka bir komut aratır.

 Bu kılavuzda, araç çubuğundaki bir komutla Visual Studio çözümünde başlangıç projesinin **Çözüm Gezgini** gösterir. Etkin çözümde projelerin dinamik açılan listesine sahip bir menü denetleyicisi kullanır. Hiçbir çözüm açıkken veya açık çözümde yalnızca bir proje olduğunda bu komutun görünmesinin ardından VSPackage yalnızca bir çözümde birden fazla proje olduğunda yüklenir.

 *.vsct* dosyaları hakkında daha fazla bilgi için [bkz. Visual Studio tablosu (.vsct) dosyaları.](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

1. adlı bir VSIX projesi `DynamicMenuItems` oluşturun.

2. Proje açıldığında, özel bir komut öğesi şablonu ekleyin ve **DynamicMenu olarak ad girin.** Daha fazla bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="setting-up-the-elements-in-the-vsct-file"></a>*.vsct dosyasındaki öğeleri* ayarlama
 Araç çubuğunda dinamik menü öğeleriyle bir menü denetleyicisi oluşturmak için aşağıdaki öğeleri belirtirsiniz:

- Biri menü denetleyicisini ve diğeri de açılan menü öğelerini içeren iki komut grubu

- Türünde bir menü öğesi `MenuController`

- Biri menü öğeleri için yer tutucu olarak görev alan iki düğme, diğeri ise araç çubuğunda simge ve araç ipucu sağlar.

1. *DynamicMenuPackage.vsct içinde* komut kimliklerini tanımlayın. Semboller bölümüne gidin ve **guidDynamicMenuPackageCmdSet** GuidSymbol bloğunda IDSymbol öğelerini değiştirin. İki grup için IDSymbol öğelerini tanımlamanız gerekir: menü denetleyicisi, yer tutucu komutu ve yer tutucu komutu.

    ```xml
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />
        <IDSymbol name="MyMenuController" value ="0x1030"/>
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />
        <!-- NOTE: The following command expands at run time to some number of ids.
         Try not to place command ids after it (e.g. 0x0105, 0x0106).
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />
    </GuidSymbol>
    ```

2. Gruplar bölümünde mevcut grupları silin ve az önce tanımlandığı iki grubu ekleyin:

    ```xml
    <Groups>
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.
             The 0x4000 priority adds this group after the group that contains the
             Preview Selected Items button, which is normally at the far right of the toolbar. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />
        </Group>
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />
        </Group>
    </Groups>
    ```

     MenuController'i ekleyin. DynamicVisibility komut bayrağını ayarlayın çünkü her zaman görünür değildir. ButtonText görüntülenmez.

    ```xml
    <Menus>
        <!-- The MenuController to display on the Solution Explorer toolbar.
             Place it in the ToolbarItemGroup.-->
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />
            <CommandFlag>DynamicVisibility</CommandFlag>
            <Strings>
               <ButtonText></ButtonText>
           </Strings>
        </Menu>
    </Menus>
    ```

3. Biri dinamik menü öğeleri için yer tutucu, biri de MenuController için yer tutucu olarak olmak için iki düğme ekleyin.

     Yer tutucu düğmesinin üst öğesi **MyMenuControllerGroup'dur.** Yer tutucu düğmesine DynamicItemStart, DynamicVisibility ve TextChanges komut bayraklarını ekleyin. ButtonText görüntülenmez.

     Yer noktası düğmesi simgeyi ve araç ipucu metnini tutar. Yer noktası düğmesinin üst öğesi de **MyMenuControllerGroup'tır.** Düğmenin menü denetleyicisi açılan listesinde görünmey olduğundan emin olmak için NoShowOnMenuController komut bayrağını ve kalıcı sabit noktası yapmak için FixMenuController komut bayrağını eklersiniz.

    ```xml
    <!-- The placeholder for the dynamic items that expand to N items at run time. -->
    <Buttons>
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <CommandFlag>DynamicItemStart</CommandFlag>
          <CommandFlag>DynamicVisibility</CommandFlag>
          <CommandFlag>TextChanges</CommandFlag>
          <!-- This text does not appear. -->
          <Strings>
            <ButtonText>Project</ButtonText>
          </Strings>
        </Button>

        <!-- The anchor item to supply the icon/tooltip for the MenuController -->
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->
          <Icon guid="guidImages" id="bmpPicArrows"/>
          <!-- Do not show on the menu controller's drop down list-->
          <CommandFlag>NoShowOnMenuController</CommandFlag>
          <!-- Become the permanent anchor item for the menu controller -->
          <CommandFlag>FixMenuController</CommandFlag>
          <!-- The text that appears in the tooltip.-->
          <Strings>
            <ButtonText>Set Startup Project</ButtonText>
          </Strings>
        </Button>
    </Buttons>
    ```

4. Projeye bir simge ekleyin *(Kaynaklar* klasörüne) ve *ardından .vsct* dosyasına başvuru ekleyin. Bu kılavuzda, proje şablonuna dahil edilen Oklar simgesini kullaneceğiz.

5. Semboller bölümünün hemen öncesinde Komutlar bölümünün dışına bir VisibilityConstraints bölümü ekleyin. (Semboller'den sonra eklersiniz bir uyarıyla karşınıza çıkar.) Bu bölüm, menü denetleyicisinin yalnızca birden çok proje içeren bir çözüm yüklendiğinde göründüğünden emin olur.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Dinamik menü komutunu uygulama
 'den devralan bir dinamik menü komut sınıfı <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> oluşturabilirsiniz. Bu uygulamada, oluşturucu komutları eşleştirmek için kullanılacak bir önkate belirtir. Çağrılan komutu tanımlayan özelliğini ayarlamak için bu ayarı <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> kullanmak üzere yöntemini geçersiz <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> kılmalısiniz.

1. *DynamicItemMenuCommand.cs* adlı yeni bir C# sınıf dosyası oluşturun ve 'den devralan **DynamicItemMenuCommand** adlı bir sınıf <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ekleyin:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Eşleşmeyi depolamak için özel bir alan ekleyin:

    ```csharp
    private Predicate<int> matches;

    ```

4. Oluşturucudan devralan ve bir komut <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> işleyicisi ve bir işleyici belirten bir oluşturucu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> ekleyin. komutuyla eşleştirmek için bir önkate ekleyin:

    ```csharp
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)
    {
        if (matches == null)
        {
            throw new ArgumentNullException("matches");
        }

        this.matches = matches;
    }
    ```

5. yöntemini <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> geçersiz kılarak eşleşme önkolojisi çağırarak özelliğini <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> ayarlar:

    ```csharp
    public override bool DynamicItemMatch(int cmdId)
    {
        // Call the supplied predicate to test whether the given cmdId is a match.
        // If it is, store the command id in MatchedCommandid
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.
        if (this.matches(cmdId))
        {
            this.MatchedCommandId = cmdId;
            return true;
        }

        this.MatchedCommandId = 0;
        return false;
    }
    ```

## <a name="add-the-command"></a>komutu ekleme
 DynamicMenu oluşturucusu, dinamik menüler ve menü öğeleri de dahil olmak üzere menü komutlarını ayar seçeneğinizdir.

1. *DynamicMenuPackage.cs içinde,* komut kümesi GUID'lerini ve komut kimliğini ekleyin:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. *DynamicMenu.cs dosyasına* aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. sınıfında, `DynamicMenu` **dte2** özel bir alan ekleyin.

    ```csharp
    private DTE2 dte2;
    ```

4. Özel bir rootItemId alanı ekleyin:

    ```csharp
    private int rootItemId = 0;
    ```

5. DynamicMenu oluşturucusu'nda menü komutunu ekleyin. Bir sonraki bölümde komut işleyicisini, olay `BeforeQueryStatus` işleyicisini ve eşleşme önkatesini tanımlay belirli bir bölüme yer ve ardından

    ```csharp
    private DynamicMenu(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,
                IsValidDynamicItem,
                OnInvokedDynamicItem,
                OnBeforeQueryStatusDynamicItem);
                commandService.AddCommand(dynamicMenuCommand);
                }

        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));
    }
    ```

## <a name="implement-the-handlers"></a>İşleyicileri uygulama
 Bir menü denetleyicisinde dinamik menü öğeleri uygulamak için, dinamik bir öğeye tık olduğunda komutu işlemelisiniz. Ayrıca menü öğesinin durumunu ayaran mantığı da uygulamalısınız. sınıfa işleyicileri `DynamicMenu` ekleyin.

1. Başlangıç Projesini **Ayarla komutunu uygulamak** için **OnInvokedDynamicItem olay işleyicisini** ekleyin. Adı çağrılan komutun metniyle aynı olan projeyi ve özelliğinde mutlak yolunu ayarerek bunu başlangıç projesi olarak <xref:EnvDTE.SolutionBuild.StartupProjects%2A> ayarlar.

    ```csharp
    private void OnInvokedDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;
        // If the command is already checked, we don't need to do anything
        if (invokedCommand.Checked)
            return;

        // Find the project that corresponds to the command text and set it as the startup project
        var projects = dte2.Solution.Projects;
        foreach (Project proj in projects)
        {
            if (invokedCommand.Text.Equals(proj.Name))
            {
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;
                return;
            }
        }
    }
    ```

2. Olay `OnBeforeQueryStatusDynamicItem` işleyicisini ekleyin. Bu, bir olaydan önce çağrılır `QueryStatus` işleyicidir. Menü öğesinin yer tutucu öğe değil "gerçek" öğe olup olmadığını ve öğenin zaten işaretli olup olmadığını belirler (projenin başlangıç projesi olarak zaten ayarlanmış olduğu anlamına gelir).

    ```csharp
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)
    {
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;
        matchedCommand.Enabled = true;
        matchedCommand.Visible = true;

        // Find out whether the command ID is 0, which is the ID of the root item.
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,
         // and IsValidDynamicItem won't be called.
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);

        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);

        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;

        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));

        // Check the command if it isn't checked already selected
        matchedCommand.Checked = (matchedCommand.Text == startupProject);

        // Clear the ID because we are done with this item.
        matchedCommand.MatchedCommandId = 0;
    }
    ```

## <a name="implement-the-command-id-match-predicate"></a>Komut kimliği eşleşmesi gerekliliği uygulama

Şimdi eşleşme gerekliliği uygulama. İki şeyi belirlememiz gerekir: öncelikle komut kimliğinin geçerli olup olmadığı (bildirilen komut kimliğinden büyük veya buna eşit) ve ikinci olarak da olası bir projeyi (çözümde yer alan proje sayısından daha azdır) belirlememiz gerekir.

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>VSPackage'i yalnızca bir çözümün birden çok projesi olduğunda yük olarak ayarlayın
 Etkin **çözümde birden** fazla proje yoksa Başlangıç Projesini Ayarla komutu anlamlı olmadığı için VSPackage'nızı yalnızca bu durumda otomatik yükleme yapacak şekilde ayarlayın. kullanıcı arabirimi <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> bağlamıyla birlikte kullanırız. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> *DynamicMenuPackage.cs* dosyasında, DynamicMenuPackage sınıfına aşağıdaki öznitelikleri ekleyin:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Başlangıç projesini ayarla komutunu test edin
 Artık kodunuzu testabilirsiniz.

1. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir.

2. Deneysel örnekte, birden fazla projesi olan bir çözüm açın.

     Araç çubuğunda ok simgesini **Çözüm Gezgini.** Genişletken, çözümdeki farklı projeleri temsil eden menü öğeleri görüntü gerekir.

3. Projelerden birini kontrol edin, başlangıç projesi olur.

4. Çözümü kapatarak veya yalnızca bir projesi olan bir çözümü a açmak için araç çubuğu simgesinin kaybolması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
