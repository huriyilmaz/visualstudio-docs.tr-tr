---
title: Menü öğelerini dinamik olarak ekleme | Microsoft Docs
description: Çalışma zamanında menü öğeleri eklemek için DynamicItemStart komut bayrağını nasıl kullanacağınızı öğrenin. bu makalede, Visual Studio çözümünde başlangıç projesinin nasıl ayarlanacağı gösterilmektedir.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e7875b939748ff5140d65a1b17ffe30c6ecfac88
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726948"
---
# <a name="dynamically-add-menu-items"></a>Menü öğelerini dinamik olarak ekle
komut `DynamicItemStart` satırı Visual Studio komut tablosu (*. vsct*) dosyasındaki bir yer tutucu düğme tanımında komut bayrağını belirterek ve sonra (kodda) komutları göstermek ve işlemek için menü öğelerinin sayısını tanımlayarak çalışma zamanında menü öğeleri ekleyebilirsiniz. VSPackage yüklendiğinde, yer tutucu dinamik menü öğeleriyle değiştirilmiştir.

 Visual Studio, **en son** kullanılanlar (MRU) listesinde, son zamanlarda açılan belgelerin adlarını ve açık olan pencerelerin adlarını görüntüleyen **Windows** listesini görüntüleyen dinamik listeler kullanır.   `DynamicItemStart`Bir komut tanımındaki bayrak, VSPackage açılmadan komutun bir yer tutucu olduğunu belirtir. VSPackage açıldığında, yer tutucu, çalışma zamanında oluşturulan ve dinamik listeye eklenen 0 veya daha fazla komutlarla değiştirilmiştir. Dinamik listenin, VSPackage açılmadan önce göründüğü menüde konumu göremeyebilirsiniz.  dinamik listeyi doldurmak için Visual Studio, vspackage 'ın ilk karakterleri yer tutucunun kimliğiyle aynı olan bir kimliğe sahip bir komutu aramasını ister. Visual Studio eşleşen bir komut bulduğunda, komutun adını dinamik listeye ekler. Daha sonra KIMLIĞI artırır ve daha dinamik komut kalmayana kadar dinamik listeye eklemek için başka bir eşleşen komut arar.

 bu izlenecek yol, bir Visual Studio çözümünde başlangıç projesinin **Çözüm Gezgini** araç çubuğunda bir komutla nasıl ayarlanacağını gösterir. Etkin çözümdeki projelerin dinamik bir açılan listesine sahip olan bir menü denetleyicisi kullanır. Hiçbir çözüm açık olmadığında veya açık çözümün yalnızca bir projesi olduğunda, bu komutun görünmesini önlemek için, VSPackage yalnızca bir çözümde birden çok proje olduğunda yüklenir.

 *. vsct* dosyaları hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma

1. Adlı bir VSıX projesi oluşturun `DynamicMenuItems` .

2. Proje açıldığında, özel bir komut öğesi şablonu ekleyin ve onu **DynamicMenu** olarak adlandırın. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="setting-up-the-elements-in-the-vsct-file"></a>*. Vsct* dosyasındaki öğeleri ayarlama
 Bir araç çubuğunda dinamik menü öğeleriyle bir menü denetleyicisi oluşturmak için aşağıdaki öğeleri belirtirsiniz:

- Bir menü denetleyicisi ve açılan menüdeki menü öğelerini içeren başka iki komut grubu

- Türünde bir menü öğesi `MenuController`

- İki düğme, bir menü öğeleri için yer tutucu görevi gören diğeri ve araç çubuğunda simge ve araç ipucunu sağlayan diğeri.

1. *Dynamicmenupackage. vsct* içinde, komut kimliklerini tanımlayın. Semboller bölümüne gidin ve **Guiddynamicmenupackagecmdset** GuidSymbol bloğundaki IDSymbol öğelerini değiştirin. İki grup, menü denetleyicisi, yer tutucu komutu ve tutturucu komutu için IDSymbol öğelerini tanımlamanız gerekir.

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

2. Gruplar bölümünde, mevcut grupları silin ve yeni tanımladığınız iki grubu ekleyin:

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

     MenuController 'ı ekleyin. Her zaman görünür olmadığından DynamicVisibility komut bayrağını ayarlayın. ButtonText görüntülenmiyor.

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

3. Biri dinamik menü öğeleri için bir yer tutucu, diğeri ise Menuıcontroller için tutturucu olarak olmak üzere iki düğme ekleyin.

     Yer tutucu düğmesinin üst öğesi **Mymenucontrollergroup**' dır. DynamicItemStart, DynamicVisibility ve TextChanges komut bayraklarını yer tutucu düğmesine ekleyin. ButtonText görüntülenmiyor.

     Tutturucu düğmesi simgeyi ve araç ipucu metnini barındırır. Tutturucu düğmesinin üst öğesi de **Mymenucontrollergroup**' dır. Düğmenin menü denetleyicisi açılan menüsünde gerçekten görünmediğinden emin olmak için NoShowOnMenuController komut bayrağını ve kalıcı bağlantı kurmak için FixMenuController komut bayrağını ekleyin.

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

4. Projeye bir simge ekleyin ( *kaynaklar* klasöründe) ve ardından başvurusunu *. vsct* dosyasına ekleyin. Bu kılavuzda, proje şablonunda bulunan oklar simgesini kullanırız.

5. Semboller bölümünden hemen önce komutlar bölümünün dışında bir Visibilitykýsýtlamai bölümü ekleyin. (Simgelerden sonra eklerseniz bir uyarı alabilirsiniz.) Bu bölüm, menü denetleyicisinin yalnızca birden fazla proje içeren bir çözüm yüklendiğinde göründüğünden emin olmanızı sağlar.

    ```xml
    <VisibilityConstraints>
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>
    </VisibilityConstraints>
    ```

## <a name="implement-the-dynamic-menu-command"></a>Dinamik menü komutunu uygulama
 Öğesinden devralan dinamik bir menü komut sınıfı oluşturursunuz <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> . Bu uygulamada, Oluşturucu eşleştirme komutları için kullanılacak bir koşul belirtir. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>Çağrılacak komutu tanımlayan özelliğini ayarlamak için bu koşulu kullanmak için yöntemini geçersiz kılmanız gerekir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> .

1. *Dynamicıtemmenucommand. cs* adlı yeni bir C# sınıf dosyası oluşturun ve öğesinden devralan **dynamicıtemmenucommand** adlı bir sınıf ekleyin <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> :

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

3. Eşleştirme koşulunu depolamak için bir özel alan ekleyin:

    ```csharp
    private Predicate<int> matches;

    ```

4. Oluşturucuyu devralan bir Oluşturucu ekleyin <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ve bir komut işleyicisini ve <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> işleyiciyi belirtin. Komutu eşleştirmek için bir koşul ekleyin:

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

5. Yöntemi, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> eşleşmeler koşulunu çağıracak ve özelliğini ayarlayan şekilde geçersiz kılın <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> :

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

## <a name="add-the-command"></a>Komutu ekleyin
 DynamicMenu Oluşturucusu, dinamik menüler ve menü öğeleri dahil olmak üzere menü komutlarını ayarladığınız yerdir.

1. *Dynamicmenupackage. cs* dosyasında, komut kümesinin GUID 'ini ve komut kimliğini ekleyin:

    ```csharp
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    public const uint cmdidMyCommand = 0x104;
    ```

2. *DynamicMenu. cs* dosyasında aşağıdaki yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using System.ComponentModel.Design;
    ```

3. `DynamicMenu`Sınıfında, **DTE2** özel alanını ekleyin.

    ```csharp
    private DTE2 dte2;
    ```

4. Özel Rootıtemıd alanı ekle:

    ```csharp
    private int rootItemId = 0;
    ```

5. DynamicMenu oluşturucusunda menü komutunu ekleyin. Sonraki bölümde, komut işleyicisini, `BeforeQueryStatus` olay işleyicisini ve eşleşme koşulunu tanımlayacağız.

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
 Bir menü denetleyicisine dinamik menü öğeleri uygulamak için, bir dinamik öğeye tıklandığında komutu işlemeniz gerekir. Ayrıca, menü öğesinin durumunu ayarlayan mantığı da uygulamalısınız. İşleyicileri `DynamicMenu` sınıfına ekleyin.

1. **başlangıç Project ayarla** komutunu uygulamak için, **onınvokeddynamicıtem** olay işleyicisini ekleyin. Bu, adı çağrılan komutun metniyle aynı olan projeyi arar ve özellikte mutlak yolu ayarlayarak başlangıç projesi olarak ayarlar <xref:EnvDTE.SolutionBuild.StartupProjects%2A> ...

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

2. `OnBeforeQueryStatusDynamicItem`Olay işleyicisini ekleyin. Bu, bir olaydan önce çağrılan işleyicidir `QueryStatus` . Menü öğesinin bir "gerçek" öğe olup olmadığını, diğer bir deyişle, yer tutucu öğesi değil, öğenin zaten işaretli olup olmadığını (yani projenin zaten başlangıç projesi olarak ayarlanmış olduğunu) belirler.

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

## <a name="implement-the-command-id-match-predicate"></a>Komut KIMLIĞI eşleşme koşulunu Uygula

Şimdi eşleşme koşulunu uygulayın. İki şeyi belirlememiz gerekir: ilk olarak, komut KIMLIĞININ geçerli olup olmadığı (belirtilen komut KIMLIĞINDEN büyük veya buna eşit) ve ikincisi, olası bir proje (çözümdeki proje sayısından daha az) olup olmadığını belirtir.

```csharp
private bool IsValidDynamicItem(int commandId)
{
    // The match is valid if the command ID is >= the id of our root dynamic start item
    // and the command ID minus the ID of our root dynamic start item
    // is less than or equal to the number of projects in the solution.
    return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);
}
```

## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>VSPackage 'ı yalnızca bir çözümde birden çok proje olduğunda yüklenecek şekilde ayarlayın
 etkin çözümde birden fazla proje yoksa, **set Startup Project** komutu anlamlı olmadığından, vspackage 'ı yalnızca o durumda otomatik olarak yüklenecek şekilde ayarlayabilirsiniz. <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI bağlamı ile birlikte kullanırsınız <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects> . *Dynamicmenupackage. cs* dosyasında aşağıdaki öznitelikleri dynamicmenupackage sınıfına ekleyin:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
[ProvideMenuResource("Menus.ctmenu", 1)]
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]
[Guid(DynamicMenuPackage.PackageGuidString)]
public sealed class DynamicMenuItemsPackage : Package
{}
```

## <a name="test-the-set-startup-project-command"></a>Başlangıç projesini ayarla komutunu test etme
 Şimdi kodunuzu test edebilirsiniz.

1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

2. Deneysel örnekte, birden fazla proje içeren bir çözüm açın.

     **Çözüm Gezgini** araç çubuğunda ok simgesini görmeniz gerekir. Genişlettikten sonra, çözümdeki farklı projeleri temsil eden menü öğeleri görünmelidir.

3. Projelerden birini denetlediğinizde, bu, başlangıç projesi olur.

4. Çözümü kapattığınızda veya yalnızca bir projesi olan bir çözümü açtığınızda, araç çubuğu simgesinin kaybolması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
