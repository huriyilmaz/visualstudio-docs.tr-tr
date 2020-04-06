---
title: Çözüm Gezgini Araç Çubuğuna Komut Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740339"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Çözüm Gezgini araç çubuğuna komut ekleme
Bu izlik, **Çözüm Gezgini** araç çubuğuna nasıl bir düğme eklendirilir gösterir.

 Araç çubuğu veya menüdeki tüm komutlar Visual Studio'da düğme olarak adlandırılır. Düğme tıklatıldığında, komut işleyicisindeki kod yürütülür. Genellikle, ilgili komutlar bir grup oluşturmak için birlikte gruplanır. Menüler veya araç çubukları gruplar için kapsayıcı görevi görededir. Öncelik, bir gruptaki tek tek komutların menüde veya araç çubuğunda görünme sırasını belirler. Bir düğmenin görünürlüğünü kontrol ederek araç çubuğunda veya menüde görüntülenmesini engelleyebilirsiniz. *.vsct* dosyasının `<VisibilityConstraints>` bir bölümünde listelenen bir komut yalnızca ilişkili bağlamda görüntülenir. Görünürlük gruplara uygulanamaz.

 Menüler, araç çubuğu komutları ve *.vsct* dosyaları hakkında daha fazla bilgi için [Komutlar, menüler ve araç çubuklarına](../extensibility/internals/commands-menus-and-toolbars.md)bakın.

> [!NOTE]
> VSPackages'lerinizde menülerin ve komutların nasıl göründüğünü tanımlamak için komut tablosu yapılandırması (*.ctc*) dosyaları yerine XML Komut Tablosu (*.vsct*) dosyalarını kullanın. Daha fazla bilgi için [Visual Studio Komut Tablosu(. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

## <a name="create-an-extension-with-a-menu-command"></a>Menü komutuyla uzantı oluşturma
 Adlı `SolutionToolbar`bir VSIX projesi oluşturun. **ToolbarButton**adlı bir menü komut öğesi şablonu ekleyin. Bunun nasıl yapılacılayaç yapıla [Create an extension with a menu command](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Çözüm Gezgini araç çubuğuna bir düğme ekleme
 Gözden geçirme bölümünün bu bölümü, Çözüm **Gezgini** araç çubuğuna nasıl bir düğme ekleyeceğinigösterir. Düğme tıklatıldığında, geri arama yöntemindeki kod çalıştırılır.

1. *ToolbarButtonPackage.vsct* dosyasında `<Symbols>` bölüme gidin. Düğüm, `<GuidSymbol>` paket şablonu tarafından oluşturulan menü grubunu ve komutu içerir. Komutunuzu `<IDSymbol>` tutacak grubu bildirmek için bu düğüme bir öğe ekleyin.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. `<Groups>` Bölümde, varolan grup girişinden sonra, önceki adımda beyan ettiğiniz yeni grubu tanımlayın.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Üst GUID:ID çiftini `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` ayarlama ve bu grubu **Çözüm Gezgini** araç çubuğuna koyar ve yüksek öncelikli bir değer ayarlamak, onu diğer komut gruplarının önüne koyar.

3. `<Buttons>` Bölümde, önceki adımda tanımladığınız `<Button>` grubu yansıtacak şekilde oluşturulan girişin üst kimliğini değiştirin. Değiştirilen `<Button>` öğe aşağıdaki gibi görünmelidir:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

     **Çözüm Gezgini** araç çubuğu, yeni komut düğmesini varolan düğmelerin sağında görüntülemelidir. Düğme simgesi strikethrough olduğunu.

5. Yeni düğmeyi tıklatın.

     **ToolbarButtonPackage Inside Solution.ToolbarButton.MenuItemCallback()** iletisi olan bir iletişim kutusu görüntülenmelidir.

## <a name="control-the-visibility-of-a-button"></a>Bir düğmenin görünürlüğünü denetleme
 Gözden geçirme nin bu bölümü, araç çubuğundaki bir düğmenin görünürlüğünü nasıl denetlergösteriyi gösterir. `<VisibilityConstraints>` *SolutionToolbar.vsct* dosyasının bölümündebir veya daha fazla projeye bağlam ayarlayarak, bir düğmenin yalnızca bir proje veya proje açık olduğunda görünmesini kısıtlarsınız.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Bir veya daha fazla proje açıkken bir düğmeyi görüntülemek için

1. `<Buttons>` *ToolbarButtonPackage.vsct*bölümünde, `<Button>` varolan öğeye ve `<Strings>` `<Icons>` etiketlerarasında iki komut bayrağı ekleyin.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Ve `DefaultInvisible` `DynamicVisibility` `<VisibilityConstraints>` bayraklar, bölümdeki girişlerin etkili olabilmesi için ayarlanmalıdır.

2. İki `<VisibilityItem>` `<VisibilityConstraints>` girişi olan bir bölüm oluşturun. Kapanış `</Commands>` etiketinden hemen sonra yeni bölümü koyun.

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

    Her görünürlük öğesi, belirtilen düğmenin görüntülendiği bir koşulu temsil eder. Birden çok koşul uygulamak için, aynı düğme için birden çok giriş oluşturmanız gerekir.

3. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

    **Solution Explorer** araç çubuğu strikethrough düğmesini içermez.

4. Proje içeren herhangi bir çözümü açın.

    Strikethrough düğmesi, varolan düğmelerin sağındaki araç çubuğunda görünür.

5. **Dosya** menüsünde **Çözümü Kapat'ı**tıklatın. Düğme araç çubuğundan kaybolur.

   VSPackage yüklenene [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kadar düğmenin görünürlüğü tarafından kontrol edilir. VSPackage yüklendikten sonra, düğmenin görünürlüğü VSPackage tarafından kontrol edilir.  Daha fazla bilgi için [MenuCommands vs. OleMenuCommands'a](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
