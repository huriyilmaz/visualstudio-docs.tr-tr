---
title: Bir araç çubuğuna menü denetleyicisi ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c63f6c98153c9f7a9fab171b3caddd57df717cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184906"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>Araç Çubuğuna Menü Denetleyicisi Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, araç [çubuğundaki bir araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md) izlenecek yolu ve araç penceresi araç çubuğuna bir menü denetleyicisinin nasıl ekleneceğini gösterir. Burada gösterilen adımlar [araç çubuğu ekleme](../extensibility/adding-a-toolbar.md) gözden geçirmede oluşturulan araç çubuğuna da uygulanabilir.  
  
 Bir menü denetleyicisi bölünmüş bir denetimdir. Menü denetleyicisinin sol tarafında, son kullanılan komut gösterilir ve bu, tıklatılarak çalıştırılabilir. Menü denetleyicisinin sağ tarafı, tıklandığı zaman ek komutların bir listesini açan bir oktur. Listede bir komuta tıkladığınızda, komut çalışır ve menü denetleyicisinin sol tarafındaki komutu değiştirir. Bu şekilde, menü denetleyicisi her zaman bir listeden son kullanılan komutu gösteren bir komut düğmesi gibi çalışır.  
  
 Menü denetleyicileri menülerde görünebilir, ancak en sık araç çubuklarında kullanılır.  
  
## <a name="prerequisites"></a>Ön koşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-controller"></a>Menü denetleyicisi oluşturma  
  
#### <a name="to-create-a-menu-controller"></a>Bir menü denetleyicisi oluşturmak için  
  
1. Araç çubuğunun bulunduğu bir araç penceresi oluşturmak için araç [çubuğuna araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md) konusunda açıklanan yordamları izleyin.  
  
2. TWTestCommandPackage. vsct içinde semboller bölümüne gidin. **Guidtwtestcommandpackagecmdset**adlı GuidSymbol öğesinde menü denetleyicinizi, menü denetleyicisi grubunuzu ve üç menü öğesini bildirin.  
  
   ```xml  
   <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
   ```  
  
3. Menüler bölümünde, son menü girişinden sonra menü denetleyicisini bir menü olarak tanımlayın.  
  
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
  
    `TextChanges` `TextIsAnchorCommand` Menü denetleyicinin son seçili komutu yansıtmasını sağlamak için ve bayrakları dahil olmalıdır.  
  
4. Gruplar bölümünde, son grup girişinden sonra, menü denetleyicisi grubunu ekleyin.  
  
   ```xml  
   <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
       <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
   </Group>  
   ```  
  
    Menü denetleyicisini üst öğe olarak ayarlayarak, bu gruba yerleştirilmiş komutlar menü denetleyicisinde görünür. `priority`Özniteliği, menü denetleyicisindeki tek grup olacak şekilde varsayılan değer olan 0 değerine ayarlayan atlanır.  
  
5. Düğmeler bölümünde, son düğme girişinden sonra menü öğelerinizin her biri için bir Button öğesi ekleyin.  
  
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
  
6. Bu noktada, menü denetleyicisine bakabilirsiniz. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örneği görmeniz gerekir.  
  
   1. **Görünüm/diğer pencereler** menüsünde **Test ToolWindow**öğesini açın.  
  
   2. Menü denetleyicisi araç penceresindeki araç çubuğunda görüntülenir.  
  
   3. Üç olası komutu görmek için menü denetleyicisinin sağ tarafındaki oka tıklayın.  
  
      Bir komuta tıkladığınızda, menü denetleyicisinin başlığı bu komutu gösterecek şekilde değişir. Sonraki bölümde, bu komutları etkinleştirmek için kodu ekleyeceğiz.  
  
## <a name="implementing-the-menu-controller-commands"></a>Menü denetleyicisi komutlarını uygulama  
  
1. TWTestCommandPackageGuids.cs ' de, mevcut komut kimliklerinden sonra üç menü öğesi için komut kimliklerini ekleyin.  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2. TWTestCommand.cs ' de, TWTestCommand sınıfının en üstüne aşağıdaki kodu ekleyin.  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3. TWTestCommand oluşturucusunda, yönteme son çağrıdan sonra `AddCommand` , her komut için olayları aynı işleyiciler aracılığıyla yönlendirmek üzere kod ekleyin.  
  
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
  
4. Seçili komutu işaretlenmiş olarak işaretlemek için TWTestCommand sınıfına bir olay işleyicisi ekleyin.  
  
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
  
1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örneği görmeniz gerekir.  
  
2. **Görünüm/diğer pencereler** menüsünde **Test ToolWindow** açın.  
  
     Menü denetleyicisi araç penceresinde araç çubuğunda görünür ve **mc öğesi 1**' i görüntüler.  
  
3. Okun solundaki menü denetleyicisi düğmesine tıklayın.  
  
     İlki seçili olan ve simgesinin etrafında bir vurgulama kutusu olan üç öğe görmeniz gerekir. **Mc öğesi 3**' e tıklayın.  
  
     **Menü denetleyicisi öğesi 3 ' ü seçtiğiniz**iletiyle birlikte bir iletişim kutusu görüntülenir. İletinin menü denetleyicisi düğmesinde metne karşılık geldiğini unutmayın. Menü denetleyicisi düğmesi artık **mc öğesi 3 ' ü**görüntüler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç penceresine araç çubuğu ekleme](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Araç Çubuğu Ekleme](../extensibility/adding-a-toolbar.md)
