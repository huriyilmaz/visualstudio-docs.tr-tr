---
title: Dinamik Menü Öğeleri Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4387c1930e09e49c0ec5c36ccedc1bb83dc273f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712063"
---
# <a name="dynamically-add-menu-items"></a>Dinamik menü öğeleri ekleme
Visual Studio komut tablosunda*yer*tutucu `DynamicItemStart` düğme tanımında komut bayrağını belirterek, ardından (kodda) komutu görüntülemek ve işlemek için menü öğelerinin sayısını tanımlayarak (kodda) menü öğelerini belirleyerek çalışma zamanında menü öğeleri ekleyebilirsiniz. VSPackage yüklendiğinde, yer tutucu dinamik menü öğeleriyle değiştirilir.

 Visual Studio, son zamanlarda açılmış olan belgelerin adlarını ve şu anda açık olan pencerelerin adlarını görüntüleyen **Windows** listesinde **en son kullanılanlar** (MRU) listesinde dinamik listeler kullanır.   Komut `DynamicItemStart` tanımındaki bayrak, VSPackage açılana kadar komutun bir yer tutucu olduğunu belirtir. VSPackage açıldığında, yer tutucu çalışma zamanında oluşturulan 0 veya daha fazla komutla değiştirilir ve dinamik listeye eklenir. VSPackage açılana kadar dinamik listenin göründüğü menüdeki konumu göremeyebilirsiniz.  Dinamik listeyi doldurmak için Visual Studio, VSPackage'dan ilk karakterleri yer tutucunun kimliğiyle aynı olan bir kimliği olan bir komut aramasını ister. Visual Studio eşleşen bir komut bulduğunda, komutun adını dinamik listeye ekler. Daha sonra kimliği artırıp, daha fazla dinamik komut lar olmayana kadar dinamik listeye eklemek için başka bir eşleşen komut arar.

 Bu izlik, Solution **Explorer** araç çubuğundaki bir komutla başlangıç projesinin Visual Studio çözümünde nasıl ayarlangerektiğini gösterir. Etkin çözümdeki projelerin dinamik bir açılır listesi olan bir menü denetleyicisi kullanır. Bu komutun hiçbir çözüm açık olmadığında veya açık çözümün yalnızca bir projesi olduğunda görünmesini engellemek için, VSPackage yalnızca bir çözümde birden çok proje olduğunda yüklenir.

 *.vsct* dosyaları hakkında daha fazla bilgi için [Visual Studio komut tablosu (.vsct) dosyalarına](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)bakın.

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

1. Adlı `DynamicMenuItems`bir VSIX projesi oluşturun.

2. Proje açıldığında, özel bir komut öğesi şablonu ekleyin ve **dynamicmenu**adını verin. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="setting-up-the-elements-in-the-vsct-file"></a>*.vsct* dosyasındaki öğeleri ayarlama
 Araç çubuğunda dinamik menü öğeleri içeren bir menü denetleyicisi oluşturmak için aşağıdaki öğeleri belirtirsiniz:

- Biri menü denetleyicisini, diğeri açılır menü öğelerini içeren iki komut grubu

- Türünün bir menü öğesi`MenuController`

- İki düğme, biri menü öğeleri için yer tutucu olarak hareket eden diğeri ise araç çubuğundaki simgeyi ve araç ucunu sağlayan.

1. *DynamicMenuPackage.vsct'de*komut tanımlarını tanımlayın. Semboller bölümüne gidin ve **guidDynamicMenuPackageCmdSet** GuidSymbol bloğundaki IDSymbol öğelerini değiştirin. İki grup, menü denetleyicisi, yer tutucu komutu ve bağlantı komutu için IDSymbol öğelerini tanımlamanız gerekir.

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

2. Gruplar bölümünde, varolan grupları silin ve az önce tanımladığınız iki grubu ekleyin:

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

     MenuController'ı ekleyin. Her zaman görünür olmadığından DynamicVisibility komut bayrağını ayarlayın. ButtonText görüntülenmez.

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

3. İki düğme ekleyin, biri dinamik menü öğeleri için yer tutucu, diğeri menucontroller için çapa olarak.

     Yer tutucu düğmesinin üst öğesi **MyMenuControllerGroup'tur.** Yer tutucu düğmesine DynamicItemStart, DynamicVisibility ve TextChanges komut bayraklarını ekleyin. ButtonText görüntülenmez.

     Bağlantı düğmesi simgeyi ve araç ucu metnini tutar. Çapa düğmesinin üst de **MyMenuControllerGroup**olduğunu. Düğmenin menü denetleyici açılır menüsünde gerçekten görünmediğinden emin olmak için NoShowOnMenuController komut bayrağını ve kalıcı bağlantı noktası yapmak için FixMenuController komut bayrağını eklersiniz.

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

4. Projeye *(Kaynaklar* klasöründe) bir simge ekleyin ve sonra başvuruyu *.vsct* dosyasına ekleyin. Bu izbarada, proje şablonunda yer alan Oklar simgesini kullanırız.

5. Semboller bölümünden hemen önce Komutlar bölümünün dışına Bir Görünürlük Kısıtlamalar bölümü ekleyin. (Semboller'den sonra eklerseniz bir uyarı alabilirsiniz.) Bu bölüm, menü denetleyicisinin yalnızca birden çok projeiçeren bir çözüm yüklendiğinde görünmesini sağlar.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Dinamik menü komutunu uygulayın
 'den <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>devralan dinamik bir menü komut sınıfı oluşturursunuz. Bu uygulamada, oluşturucu komutları eşleştirmek için kullanılacak bir yüklem belirtir. Çağrılacak komutu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> tanımlayan <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> özelliği ayarlamak için bu yüklemi kullanmak için yöntemi geçersiz kılmanız gerekir.

1. *DynamicItemMenuCommand.cs*adında yeni bir C# sınıfı dosya oluşturun ve **DynamicItemMenuCommand** adında bir sınıf <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>ekleyin:

    ```csharp
    class DynamicItemMenuCommand : OleMenuCommand
    {

    }

    ```

2. Yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    using System.ComponentModel.Design;
    ```

3. Eşleşme yüklemini depolamak için özel bir alan ekleyin:

    ```csharp
    private Predicate<int> matches;

    ```

4. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Oluşturucudan devralan ve bir komut işleyicisi ve işleyicisi belirten bir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> oluşturucu ekleyin. Komutu eşleştirmek için bir yüklem ekleyin:

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

5. Yöntem, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> eşleşen yüklemi çağıracak ve özelliği ayarlayabilmek <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> için metodun geçersiz kılın:

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

## <a name="add-the-command"></a>Komutu ekle
 DynamicMenu oluşturucu, dinamik menüler ve menü öğeleri de dahil olmak üzere menü komutlarını ayarladığınız yerdir.

1. *DynamicMenuPackage.cs,* komut kümesinin GUID'ini ve komut Kimliğini ekleyin:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. *DynamicMenu.cs* dosyasına, yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. `DynamicMenu` Sınıfta, özel bir alan **dte2**ekleyin.

    ```csharp
    private DTE2 dte2;
    ```

4. Özel rootItemId alanı ekleyin:

    ```csharp
    private int rootItemId = 0;
    ```

5. DynamicMenu oluşturucuya menü komutunu ekleyin. Sonraki bölümde komut işleyicisi, `BeforeQueryStatus` olay işleyicisi ve maç yüklemi tanımlarız.

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

## <a name="implement-the-handlers"></a>Işleyicileri uygulayın
 Bir menü denetleyicisine dinamik menü öğeleri uygulamak için, dinamik bir öğe tıklatıldığında komutu işlemeniz gerekir. Menü öğesinin durumunu ayarlayan mantığı da uygulamanız gerekir. Işleyicileri `DynamicMenu` sınıfa ekleyin.

1. **Başlangıç Projesi Ayarla** komutunu uygulamak için **OnInvokedDynamicItem** olay işleyicisini ekleyin. Çağrılan komutun metniyle aynı adı olan projeyi arar ve <xref:EnvDTE.SolutionBuild.StartupProjects%2A> özellikteki mutlak yolunu ayarlayarak başlangıç projesi olarak ayarlar.

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

2. Olay `OnBeforeQueryStatusDynamicItem` işleyicisini ekleyin. Bu, bir `QueryStatus` olaydan önce çağrılan işleyicidir. Menü öğesinin "gerçek" bir öğe olup olmadığını, yani yer tutucu öğenin değil, öğenin zaten denetlenip denetlenmediğini (projenin zaten başlangıç projesi olarak ayarlandığı anlamına gelir) belirler.

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

## <a name="implement-the-command-id-match-predicate"></a>Komut kimliği eşlemi yüklemini uygulayın

Şimdi maç yüklemini uygulayın. İki şeyi belirlememiz gerekir: birincisi, komut kimliğinin geçerli olup olmadığı (bildirilen komut kimliğinden daha büyük veya eşit olup olmadığı) ve ikincisi, olası bir projeyi belirtip belirtmediği (çözümdeki proje sayısından daha azdır).

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>VSPackage'ı yalnızca bir çözüm birden fazla proje olduğunda yüklenir
 Başlangıç **Projesi Komutunu Ayarla** komutu, etkin çözümün birden fazla projesi olmadığı sürece mantıklı olmadığından, VSPackage'ınızı yalnızca bu durumda otomatik yüklenebebileceğiniz şekilde ayarlayabilirsiniz. UI <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> bağlamıyla <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>birlikte kullanırsınız. *DynamicMenuPackage.cs* dosyasında DynamicMenuPackage sınıfına aşağıdaki öznitelikleri ekleyin:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Set başlangıç proje komutunu test edin
 Artık kodunuzu test edebilirsiniz.

1. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

2. Deneysel örnekte, birden fazla projesi olan bir çözüm açın.

     **Çözüm Gezgini** araç çubuğundaki ok simgesini görmelisiniz. Genişlettiğinizde, çözümdeki farklı projeleri temsil eden menü öğeleri görünmelidir.

3. Projelerden birini kontrol ettiğinizde, başlangıç projesi haline gelir.

4. Çözümü kapattığınızda veya yalnızca bir projesi olan bir çözüm açtığınızda, araç çubuğu simgesi nin kaybolması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
