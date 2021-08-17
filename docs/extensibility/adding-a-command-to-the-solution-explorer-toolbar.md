---
title: Çözüm Gezgini Toolbar | Microsoft Docs
description: Komut çubuğunda komut yürüten bir düğmeyi Çözüm Gezgini nasıl Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c110bf1f5dade488a0e657ce55d2240a65033085
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035377"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Araç çubuğuna komut Çözüm Gezgini ekleme
Bu kılavuzda, araç çubuğuna düğme **Çözüm Gezgini** gösterir.

 Araç çubuğundaki veya menüde yer alan komutlara, araç çubuğundaki Visual Studio. Düğmeye tıkıldığında, komut işleyicisi kodu yürütülür. Genellikle, ilgili komutlar bir grup oluşturmak için birlikte gruplar. Menüler veya araç çubukları, gruplar için kapsayıcı olarak kullanılır. Öncelik, bir gruptaki tek tek komutların menüde veya araç çubuğunda görünme sırası belirler. Bir düğmenin görünürlüğünü denetleyerek bir düğmenin araç çubuğunda veya menüde görüntülenebilir. `<VisibilityConstraints>` *.vsct* dosyasının bir bölümünde listelenen komut yalnızca ilişkili bağlamda görüntülenir. Görünürlük gruplara uygulanamaz.

 Menüler, araç çubuğu komutları ve *.vsct* dosyaları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları.](../extensibility/internals/commands-menus-and-toolbars.md)

> [!NOTE]
> MENÜlerin ve komutların VSPackage'lar içinde nasıl görüntül olduğunu tanımlamak için komut tablosu yapılandırması (*.ctc*) dosyaları yerine XML Komut Tablosu (*.vsct*) dosyalarını kullanın. Daha fazla bilgi için [bkz. Visual Studio Tablosu () . Vsct) dosyaları.](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma
 adlı bir VSIX projesi `SolutionToolbar` oluşturun. ToolbarButton adlı bir menü komut **öğesi şablonu ekleyin.** Bunun nasıl olduğu hakkında bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Araç çubuğuna düğme Çözüm Gezgini ekleme
 Adım adım kılavuzda bu bölümde, araç çubuğuna bir **düğmenin Çözüm Gezgini** yer almaktadır. Düğmeye tıkıldığında, geri çağırma yönteminde kod çalıştırıldığında.

1. *ToolbarButtonPackage.vsct* dosyasında bölümüne `<Symbols>` gidin. Düğüm, `<GuidSymbol>`  paket şablonu tarafından oluşturulan menü grubunu ve komutu içerir. Komutlarınızı `<IDSymbol>` tutacak grubu bildirecek bir öğeyi bu düğüme ekleyin.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. bölümünde, `<Groups>` mevcut grup girdiden sonra, önceki adımda bildirladığınız yeni grubu tanımlayın.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Üst GUID:ID çiftini olarak ayarp bu grubu Çözüm Gezgini araç çubuğuna koyar ve yüksek öncelikli bir değer ayarlarsa diğer komut gruplarının `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` ardından koyar. 

3. bölümünde, oluşturulan girişin üst kimliğini önceki adımda `<Buttons>` `<Button>` tanımlandığı grubu yansıtacak şekilde değiştirebilirsiniz. Değiştirilen `<Button>` öğe şuna benzmelidir:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

     Yeni **Çözüm Gezgini** araç çubuğunun, mevcut düğmelerin sağ tarafından yeni komut düğmesini görüntülemesi gerekir. Düğme simgesi, üzerinde çizili olarak gösterilir.

5. Yeni düğmesine tıklayın.

     **SolutionToolbar.ToolbarButton.MenuItemCallback() içinde ToolbarButtonPackage iletisine** sahip bir iletişim kutusu görüntüleniyor.

## <a name="control-the-visibility-of-a-button"></a>Bir düğmenin görünürlüğünü denetleme
 Kılavuzda bu bölümde, araç çubuğundaki bir düğmenin görünürlüğünü denetlemeyi gösterir. SolutionToolbar.vsct dosyasının bölümündeki bir veya birden çok projeye bağlam ayarlayan bir düğmenin yalnızca bir proje veya proje açık olduğunda görünmesini `<VisibilityConstraints>` kısıtlarsınız. 

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Bir veya daha fazla proje açık olduğunda düğme görüntülemek için

1. `<Buttons>` *ToolbarButtonPackage.vsct'nin* bölümünde, ve etiketleri arasına mevcut öğeye `<Button>` iki komut bayrağı `<Strings>` `<Icons>` ekleyin.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    bölümdeki `DefaultInvisible` `DynamicVisibility` girdilerin etkili olması için ve `<VisibilityConstraints>` bayraklarının ayarlanmış olması gerekir.

2. İki `<VisibilityConstraints>` girişi olan bir `<VisibilityItem>` bölüm oluşturun. Yeni bölümü kapanış etiketinin hemen altına `</Commands>` ekleyin.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Her görünürlük öğesi, belirtilen düğmenin altında görüntülendiğinde bir koşulu temsil eder. Birden çok koşulları uygulamak için aynı düğme için birden çok giriş oluşturmanız gerekir.

3. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

    Araç **Çözüm Gezgini,** üzerinde çizili düğmeyi içermez.

4. Proje içeren herhangi bir çözümü açın.

    Üzerinde çizili düğme, mevcut düğmelerin sağ üst çubuğunda görünür.

5. Dosya menüsünde **Çözümü** **Kapat'a tıklayın.** Düğme araç çubuğundan kaybolur.

   VSPackage yüklenene kadar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] düğmenin görünürlüğü tarafından denetlenır. VSPackage yüklendikten sonra düğmenin görünürlüğü VSPackage tarafından denetlenır.  Daha fazla bilgi için bkz. [MenuCommands ile OleMenuCommands karşılaştırması.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)