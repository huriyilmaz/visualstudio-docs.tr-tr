---
title: Araç Çubuğu ÇubuğuNa Menü Denetleyicisi | Microsoft Docs
description: Bir menü denetleyicisi oluşturma ve bunu araç penceresi araç çubuğuna ekleme hakkında Visual Studio, ardından menü denetleyicisi komutlarını uygulama ve test etmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 439b9475c92eb78e7deed63c3718d73dd9f81a4d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112002"
---
# <a name="add-a-menu-controller-to-a-toolbar"></a>Araç çubuğuna menü denetleyicisi ekleme
Bu izlenecek yol, Araç penceresine [araç çubuğu](../extensibility/adding-a-toolbar-to-a-tool-window.md) ekleme adım adım kılavuzda yer almaktadır ve araç penceresi araç çubuğuna menü denetleyicisi ekleme adımlarını gösterir. Burada gösterilen adımlar, Araç çubuğu ekleme adım adımlarında oluşturulan araç [çubuğuna da](../extensibility/adding-a-toolbar.md) uygulanabilir.

Menü denetleyicisi bir bölme denetimidir. Menü denetleyicisinin sol tarafında son kullanılan komut görüntülenir ve buna tıklayarak çalıştırabilirsiniz. Menü denetleyicisinin sağ tarafında, tıklandıktan sonra ek komutların listesini açan bir ok yer alıyor. Listede bir komuta tıklarken komut çalışır ve menü denetleyicisinin sol tarafındaki komutun yerini alar. Bu şekilde, menü denetleyicisi her zaman bir listeden son kullanılan komutu gösteren bir komut düğmesi gibi çalışır.

Menü denetleyicileri menülerde görünebilir ancak bunlar genellikle araç çubuklarında kullanılır.

## <a name="prerequisites"></a>Önkoşullar
2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-menu-controller"></a>Menü denetleyicisi oluşturma

1. Araç çubuğu olan bir [araç penceresi oluşturmak için Araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md) konusunda açıklanan yordamları izleyin.

2. *TWTestCommandPackage.vsct* içinde Semboller bölümüne gidin. **guidTWTestCommandPackageCmdSet** adlı GuidSymbol öğesinde menü denetleyicinizi, menü denetleyici grubu ve üç menü öğesini bildirin.

    ```xml
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />
    ```

3. Menüler bölümünde, son menü girdikten sonra menü denetleyicisini bir menü olarak tanımlayın.

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

    Menü `TextChanges` `TextIsAnchorCommand` denetleyicisinin son seçilen komutu yansıtmasını sağlamak için ve bayrakları ekilmelidir.

4. Gruplar bölümünde, son grup girişinin ardından menü denetleyicisi grubunu ekleyin.

    ```xml
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />
    </Group>
    ```

    Menü denetleyicisi üst öğe olarak ayarlandırarak, bu gruba yerleştirilen tüm komutlar menü denetleyicisinde görünür. Öznitelik atlanır ve bu, menü denetleyicisinde tek grup olduğundan varsayılan `priority` 0 değerine ayarlar.

5. Düğmeler bölümünde, son düğme girişinin ardından menü öğelerinizin her biri için bir Düğme öğesi ekleyin.

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

6. Bu noktada menü denetleyicisine bakabilirsiniz. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örneği görüyor gerekir.

   1. Görünüm **/ Diğer Windows** Test **AracıWindow'ı açın.**

   2. Menü denetleyicisi araç penceresindeki araç çubuğunda görünür.

   3. Üç olası komutu görmek için menü denetleyicisinin sağ tarafındaki oka tıklayın.

      Bir komuta tıklarken menü denetleyicisinin başlığında bu komutun görüntüleniyor olduğunu fark edersiniz. Sonraki bölümde, bu komutları etkinleştirmek için kodu ekleyebiliyoruz.

## <a name="implement-the-menu-controller-commands"></a>Menü denetleyicisi komutlarını uygulama

1. *TWTestCommandPackageGuids.cs* içinde, mevcut komut kimliklerinden sonra üç menü öğeniz için komut kimlikleri ekleyin.

    ```csharp
    public const int cmdidMCItem1 = 0x130;
    public const int cmdidMCItem2 = 0x131;
    public const int cmdidMCItem3 = 0x132;
    ```

2. *TWTestCommand.cs* içinde sınıfının en üstüne aşağıdaki kodu `TWTestCommand` ekleyin.

    ```csharp
    private int currentMCCommand; // The currently selected menu controller command
    ```

3. TWTestCommand oluşturucus unda, yöntemine yapılan son çağrıdan sonra, her komutun olaylarını aynı işleyiciler aracılığıyla yönlendiren `AddCommand` kod ekleyin.

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

4. Seçilen komutu işaretli olarak işaretlemek **için TWTestCommand** sınıfına bir olay işleyicisi ekleyin.

    ```csharp
    private void OnMCItemQueryStatus(object sender, EventArgs e)
    {
        OleMenuCommand mc = sender as OleMenuCommand;
        if (null != mc)
        {
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);
        }
    }
    ```

5. Kullanıcı menü denetleyicisinde bir komut seçerken MessageBox görüntüleyen bir olay işleyicisi ekleyin:

    ```csharp
    private void OnMCItemClicked(object sender, EventArgs e)
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

1. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örneği görüyor gerekir.

2. Görünüm / Diğer Menü menüsünde Test **AracıWindow'Windows** açın. 

    Menü denetleyicisi araç penceresinde araç çubuğunda görünür ve MC Öğesi **1'i görüntüler.**

3. Okun sol tarafından menü denetleyicisi düğmesine tıklayın.

    İlk öğe seçilmiş ve simgesinin etrafında bir vurgu kutusu bulunan üç öğe görüyorsanız. MC Öğe **3'e tıklayın.**

    Menü denetleyicisi Öğe **3'ü seçtiniz iletisiyle bir iletişim kutusu görüntülenir.** İletinin menü denetleyicisi düğmesinde yer alan metne karşılık gelen bir ileti olduğunu fark edersiniz. Menü denetleyicisi düğmesi artık MC Öğe **3'ü görüntüler.**

## <a name="see-also"></a>Ayrıca bkz.
- [Araç penceresine araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Araç çubuğu ekleme](../extensibility/adding-a-toolbar.md)
