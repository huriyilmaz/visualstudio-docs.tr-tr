---
title: Araç çubuğu ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de74961715a82dde4e184509094d05145ad0f79c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184863"
---
# <a name="adding-a-toolbar"></a>Araç Çubuğu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Visual Studio IDE 'ye bir araç çubuğunun nasıl ekleneceğini gösterir.  
  
 Bir araç çubuğu, komutlara bağlanan düğmeleri içeren yatay veya dikey bir şerit olur. Uygulamasına bağlı olarak, IDE 'deki bir araç çubuğu, ana IDE penceresinin herhangi bir tarafına yerleştirilmiş olan veya diğer pencerelerin önünde kalmak için yeniden konumlandırılabilir.  
  
 Ayrıca, kullanıcılar bir araç çubuğuna komut ekleyebilir veya **Özelleştir** iletişim kutusunu kullanarak bunları kaldırabilir. Genellikle, VSPackages 'teki araç çubukları Kullanıcı tarafından özelleştirilebilir. IDE tüm özelleştirmeyi işler ve VSPackage, komutlara yanıt verir. VSPackage 'ın bir komutun fiziksel olarak nerede bulunduğunu bilmeleri gerekmez.  
  
 Menüler hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Araç çubuğuyla uzantı oluşturma  
 Adlı bir VSıX projesi oluşturun `IDEToolbar` . **ToolbarTestCommand**adlı bir menü komut öğesi şablonu ekleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için, bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>IDE için bir araç çubuğu oluşturma  
  
1. ToolbarTestCommandPackage. vsct içinde semboller bölümüne bakın. Guıdtoolbartestcommandpackagecmdset adlı GuidSymbol öğesinde, bir araç çubuğu ve bir araç çubuğu grubu için aşağıdaki gibi bildirimler ekleyin.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2. Komutlar bölümünün en üstünde bir menü bölümü oluşturun. Araç çubuğinizi tanımlamak için menüler bölümüne bir menü öğesi ekleyin.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Araç çubukları alt menüler gibi iç içe geçirilemez. Bu nedenle, bir üst grup atamanız gerekmez. Ayrıca, Kullanıcı araç çubuklarını taşıyabildiğinden, öncelik ayarlamanız gerekmez. Genellikle, bir araç çubuğunun ilk yerleşimi programlı olarak tanımlanır, ancak kullanıcı tarafından sonraki değişiklikler kalıcı hale getirilir.  
  
3. [Gruplar](../extensibility/groups-element.md) bölümünde, varolan Grup girişinden sonra, araç çubuğu komutlarını Içeren bir [Grup](../extensibility/group-element.md) öğesi tanımlayın.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4. Düğmenin araç çubuğunda görünmesini sağlayın. Düğmeler bölümünde, düğmedeki üst bloğu araç çubuğuna değiştirin. Ortaya çıkan düğme bloğu şöyle görünmelidir:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Varsayılan olarak, bir araç çubuğunda komut yoksa, görüntülenmez.  
  
5. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.  
  
6. Araç çubuklarının listesini almak için Visual Studio menü çubuğuna sağ tıklayın. **Test araç çubuğunu**seçin.  
  
7. Artık araç çubuğudur dosyaları bul simgesinin sağında bir simge olarak görmeniz gerekir. Simgeye tıkladığınızda, ToolbarTestCommandPackage adlı bir ileti kutusu görmeniz gerekir **. Onıtoolbar. ToolbarTestCommand. Menuıitemcallback () içinde**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
