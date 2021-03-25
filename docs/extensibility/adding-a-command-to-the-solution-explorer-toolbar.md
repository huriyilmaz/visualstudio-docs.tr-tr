---
title: Çözüm Gezgini araç çubuğuna komut ekleme | Microsoft Docs
description: Visual Studio 'da Çözüm Gezgini araç çubuğuna bir komut yürüten bir düğme eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf6ffcded95d142578ed118ab26b57914eb36c37
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060100"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Çözüm Gezgini araç çubuğuna komut ekleme
Bu izlenecek yol, **Çözüm Gezgini** araç çubuğuna nasıl düğme ekleneceğini gösterir.

 Bir araç çubuğu veya menüdeki herhangi bir komuta, Visual Studio 'da düğme denir. Düğmeye tıklandığında, komut işleyicisindeki kod yürütülür. Genellikle, ilgili komutlar bir grup oluşturmak için birlikte gruplandırılır. Menüler veya araç çubukları, gruplar için kapsayıcı olarak davranır. Öncelik, bir gruptaki bireysel komutların menüde veya araç çubuğunda görünme sırasını belirler. Bir düğmenin, görünürlüğünü denetleyerek araç çubuğunda veya menüde görüntülenmesini engelleyebilirsiniz. `<VisibilityConstraints>` *. Vsct* dosyasının bir bölümünde listelenen bir komut yalnızca ilişkili bağlamda görünür. Görünürlük, gruplara uygulanamıyor.

 Menüler, araç çubuğu komutları ve *. vsct* dosyaları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Menü ve komutlarının Vspackakleriniz içinde nasıl göründüğünü tanımlamak için komut tablosu yapılandırma (*. CTC*) dosyaları yerine XML komut tablosu (*. vsct*) dosyaları kullanın. Daha fazla bilgi için bkz [. Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma
 Adlı bir VSıX projesi oluşturun `SolutionToolbar` . **ToolBarButton** adlı bir menü komut öğesi şablonu ekleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Çözüm Gezgini araç çubuğuna düğme ekleme
 İzlenecek yolun bu bölümü, **Çözüm Gezgini** araç çubuğuna nasıl düğme ekleneceğini gösterir. Düğmeye tıklandığında, geri çağırma yöntemindeki kod çalıştırılır.

1. *Toolbarbuttonpackage. vsct* dosyasında `<Symbols>` bölümüne gidin. `<GuidSymbol>`Düğüm, paket şablonu tarafından oluşturulan menü grubunu ve komutu içerir. `<IDSymbol>`Komutunuz grubunu barındıracak grubu bildirmek için bu düğüme bir öğe ekleyin.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. `<Groups>`Bölümünde, varolan Grup girişinden sonra, önceki adımda bildirdiğiniz yeni grubu tanımlayın.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Üst GUID: ID çiftini ayarlama `guidSHLMainMenu` ve `IDM_VS_TOOL_PROJWIN` bu grubu **Çözüm Gezgini** araç çubuğuna yerleştirir ve yüksek öncelikli bir değer ayarlamak, diğer komut gruplarından sonra bunu koyar.

3. `<Buttons>`Bölümünde, oluşturulan girdinin ana kimliğini, `<Button>` önceki adımda tanımladığınız grubu yansıtacak şekilde değiştirin. Değiştirilen `<Button>` öğe şöyle görünmelidir:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

     **Çözüm Gezgini** araç çubuğu, varolan düğmelerin sağ tarafındaki yeni komut düğmesini görüntülemelidir. Düğme simgesi üstü çizilir.

5. Yeni düğmesine tıklayın.

     **SolutionToolbar. ToolbarButton. Menuıitemcallback () içinde bulunan Toolbarbuttonpackage** iletisini içeren bir iletişim kutusu görüntülenmelidir.

## <a name="control-the-visibility-of-a-button"></a>Bir düğmenin görünürlüğünü denetleme
 İzlenecek yolun bu bölümü, bir araç çubuğundaki bir düğmenin görünürlüğünü nasıl denetleyeceğinizi gösterir. `<VisibilityConstraints>` *SolutionToolbar. vsct* dosyasının bölümündeki bir veya daha fazla projeye bir bağlam ayarlayarak, bir düğmeyi yalnızca proje veya projeler açıkken görüntülenecek şekilde kısıtlayabilirsiniz.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Bir veya daha fazla proje açık olduğunda bir düğme göstermek için

1. `<Buttons>` *Toolbarbuttonpackage. vsct* bölümünde, `<Button>` ve etiketlerinin arasına var olan öğeye iki komut bayrağı ekleyin `<Strings>` `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    `DefaultInvisible`Ve `DynamicVisibility` bayrakları, bölümündeki girişlerin etkin olabilmesi için ayarlanmalıdır `<VisibilityConstraints>` .

2. `<VisibilityConstraints>`İki girişi olan bir bölüm oluşturun `<VisibilityItem>` . Yeni bölümü, kapanış etiketinden hemen sonra koyun `</Commands>` .

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

    Her görünürlük öğesi, belirtilen düğmenin görüntülendiği bir koşulu temsil eder. Birden çok koşul uygulamak için aynı düğme için birden çok giriş oluşturmanız gerekir.

3. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

    **Çözüm Gezgini** araç çubuğu üstünü çizili düğme içermiyor.

4. Proje içeren herhangi bir çözümü açın.

    Üzerine çizili düğme, var olan düğmelerin sağındaki araç çubuğunda görüntülenir.

5. **Dosya** menüsünde **çözümü kapat**' a tıklayın. Düğme araç çubuğundan kaybolur.

   Düğmenin görünürlüğü, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage yükleninceye kadar denetlenir. VSPackage yüklendikten sonra, düğmenin görünürlüğü VSPackage tarafından denetlenir.  Daha fazla bilgi için bkz. [MenuCommands vs. OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)