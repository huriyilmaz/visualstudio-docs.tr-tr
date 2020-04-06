---
title: Araç Çubuğuna Menü Denetleyicisi Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4dcb9e51f6633476a8f0eadea30da513e5ef760
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740324"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Araç çubuğuna menü denetleyicisi ekleme
Bu gözden geçirme, [araç penceresi](../extensibility/adding-a-toolbar-to-a-tool-window.md) nin içinaraç çubuğu ekle üzerinde oluşturur ve araç penceresi araç çubuğuna menü denetleyicisinin nasıl ekleyeceğini gösterir. Burada gösterilen adımlar, [araç çubuğu ekle](../extensibility/adding-a-toolbar.md) walkthrough'unda oluşturulan araç çubuğuna da uygulanabilir.

Menü denetleyicisi bölünmüş denetimdir. Menü denetleyicisinin sol tarafında son kullanılan komutu gösterir ve tıklatarak çalıştırabilirsiniz. Menü denetleyicisinin sağ tarafı, tıklatıldığında ek komutların listesini açan bir oktur. Listedeki bir komutu tıklattığınızda, komut çalışır ve menü denetleyicisinin sol tarafındaki komutun yerini alır. Bu şekilde, menü denetleyicisi her zaman bir listeden son kullanılan komutu gösteren bir komut düğmesi gibi çalışır.

Menü denetleyicileri menülerde görünebilir, ancak en sık araç çubuklarında kullanılır.

## <a name="prerequisites"></a>Ön koşullar
Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-controller"></a>Menü denetleyicisi oluşturma

1. Araç çubuğu olan bir araç penceresi oluşturmak için [araç penceresine araç çubuğu ekle'de](../extensibility/adding-a-toolbar-to-a-tool-window.md) açıklanan yordamları izleyin.

2. *TWTestCommandPackage.vsct,* Semboller bölümüne gidin. **guidTWTestCommandPackageCmdSet**adlı GuidSymbol öğesinde, menü denetleyicinizi, menü denetleyici grubunuzu ve üç menü öğenizi bildirin.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Menüler bölümünde, son menü girişinden sonra menü denetleyicisini menü olarak tanımlayın.

    ```xml
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <CommandFlag>IconAndText</CommandFlag>
        <CommandFlag>TextChanges</CommandFlag>
        <CommandFlag>TextIsAnchorCommand</CommandFlag>
        <Strings>
            <ButtonText>Test Menu Controller</ButtonText>
            <CommandName>Test Menu Controller</CommandName>
        </Strings>
    </Menu>
    ```

    Menü `TextChanges` `TextIsAnchorCommand` denetleyicisinin son seçilen komutu yansıtmasını sağlamak için ve bayraklar eklenmelidir.

4. Gruplar bölümünde, son grup girişinden sonra menü denetleyici grubunu ekleyin.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Menü denetleyicisini üst öğe olarak ayarlayarak, bu gruba yerleştirilen komutlar menü denetleyicisinde görünür. Menü `priority` denetleyicisi üzerindeki tek grup olduğu için öznitelik atlanır ve varsayılan değeri 0 olarak ayarlar.

5. Düğmeler bölümünde, son düğme girişinden sonra, menü öğelerinizin her biri için bir Düğme öğesi ekleyin.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 1</ButtonText>
            <CommandName>MC Item 1</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 2</ButtonText>
            <CommandName>MC Item 2</CommandName>
        </Strings>
    </Button>
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />
        <Icon guid="guidImages" id="bmpPicSearch" />
        <CommandFlag>IconAndText</CommandFlag>
        <Strings>
            <ButtonText>MC Item 3</ButtonText>
            <CommandName>MC Item 3</CommandName>
        </Strings>
    </Button>
    ```

6. Bu noktada, menü denetleyicisi bakabilirsiniz. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örneği görmelisin.

   1. Görünüm **/ Diğer Windows** menüsünde **Test Araç Penceresi'ni**açın.

   2. Menü denetleyicisi araç penceresindeki araç çubuğunda görünür.

   3. Üç olası komutu görmek için menü denetleyicisinin sağ tarafındaki oku tıklatın.

      Bir komutu tıklattığınızda, menü denetleyicisinin başlığının bu komutu görüntülemek için değiştiğine dikkat edin. Bir sonraki bölümde, bu komutları etkinleştirmek için kodu ekleyeceğiz.

## <a name="implement-the-menu-controller-commands"></a>Menü denetleyici komutlarını uygulayın

1. *TWTestCommandPackageGuids.cs,* varolan komut işlikilerinden sonra üç menü ürününiz için komut dünyaları ekleyin.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. *TWTestCommand.cs,* `TWTestCommand` sınıfın üst kısmında aşağıdaki kodu ekleyin.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. TWTestCommand oluşturucu, `AddCommand` yönteme son çağrıdan sonra, aynı işleyicileri aracılığıyla her komut için olayları yönlendirmek için kod ekleyin.

    ```csharp
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=
        TWTestCommandPackageGuids.cmdidMCItem3; i++)
    {
        CommandID cmdID = new
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);
        OleMenuCommand mc = new OleMenuCommand(new
          EventHandler(OnMCItemClicked), cmdID);
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);
        commandService.AddCommand(mc);
        // The first item is, by default, checked. 
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)
        {
            mc.Checked = true;
            this.currentMCCommand = i;
        }
    }
    ```

4. Seçili komutu işaretlenmiş olarak işaretlemek için **TWTestCommand** sınıfına bir olay işleyicisi ekleyin.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Kullanıcı menü denetleyicisinde bir komut seçtiğinde MessageBox görüntüleyen bir olay işleyicisi ekleyin:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            string selection;
            switch (mc.CommandID.ID)
            {
                case c.cmdidMCItem1:
                    selection = "Menu controller Item 1";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem2:
                    selection = "Menu controller Item 2";
                    break;

                case TWTestCommandPackageGuids.cmdidMCItem3:
                    selection = "Menu controller Item 3";
                    break;

                default:
                    selection = "Unknown command";
                    break;
            }
            this.currentMCCommand = mc.CommandID.ID;

            IVsUIShell uiShell =
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));
            Guid clsid = Guid.Empty;
            int result;
            uiShell.ShowMessageBox(
                    0,
                    ref clsid,
                    "Test Tool Window Toolbar Package",
                    string.Format(CultureInfo.CurrentCulture,
                                 "You selected {0}", selection),
                    string.Empty,
                    0,
                    OLEMSGBUTTON.OLEMSGBUTTON_OK,
                    OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
                    OLEMSGICON.OLEMSGICON_INFO,
                    0,
                    out result);
        }
    }
    ```

## <a name="testing-the-menu-controller"></a>Menü denetleyicisini test etme

1. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örneği görmelisin.

2. **Görünüm / Diğer Windows** menüsünde Test Araç **Penceresini** açın.

    Menü denetleyicisi araç penceresindearaç çubuğunda görünür ve **MC Öğesi 1'i**görüntüler.

3. Okun solundaki menü denetleyici düğmesini tıklatın.

    İlki seçilmiş ve simgesinin etrafında bir vurgu kutusu bulunan üç öğe görmeniz gerekir. **MC Öğe 3'e**tıklayın.

    **Seçtiğiniz Menü denetleyici öğesi 3**ile birlikte bir iletişim kutusu görüntülenir. İletinin menü denetleyicisi düğmesindeki metne karşılık geldiğini unutmayın. Menü denetleyici düğmesi artık **MC Madde 3'u**görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [Araç penceresine araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Araç çubuğu ekleme](../extensibility/adding-a-toolbar.md)
