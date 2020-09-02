---
title: MenuCommands ve OleMenuCommands | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: jillfra
ms.openlocfilehash: 42c471ca924bfded62db32a956a26c07240459eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67624446"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands ve OleMenuCommands karşılaştırması
Nesnesinden ya da nesneden türeterek <xref:System.ComponentModel.Design.MenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ve uygun olay işleyicilerini uygulayarak menü komutları oluşturabilirsiniz. <xref:System.ComponentModel.Design.MenuCommand>VSPackage proje şablonu, ancak bazen kullanmanız gerekebilmeniz halinde kullanabileceğiniz çoğu durumda <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
 Bir VSPackage 'ın IDE için kullanılabilir hale getiren komutlar, bir kullanıcının kullanabilmesi için görünür ve etkin olmalıdır. Komutlar, Visual Studio Package proje şablonu kullanılarak bir. vsct dosyasında oluşturulduğunda, görünür ve varsayılan olarak etkindir. Gibi bazı komut bayraklarını ayarlama `DynamicItemStart` , varsayılan davranışı değiştirebilir. Bir komutun görünürlük, etkin durumu ve diğer özellikleri, komutla ilişkili nesneye erişerek çalışma zamanında kodda da değiştirilebilir <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
## <a name="prerequisites"></a>Ön koşullar  
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Visual Studio paket şablonu için şablon konumları  
 Visual Studio Package şablonunu **Visual Basic/genişletilebilirlik**, **C#/genişletilebilirlik**veya **diğer proje türleri/genişletilebilirlik**altındaki **Yeni proje** iletişim kutusunda bulabilirsiniz.  
  
## <a name="creating-a-command"></a>Komut oluşturma  
 Tüm komutlar, komut grupları, menüler, araç çubukları ve araç pencereleri. vsct dosyasında tanımlanmıştır. Daha fazla bilgi için bkz [. Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Paket şablonunu kullanarak bir VSPackage oluşturuyorsanız, bir. vsct dosyası oluşturmak ve varsayılan bir menü komutu tanımlamak için **menü komutunu** seçin. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>IDE 'ye bir komut eklemek için  
  
1. . Vsct dosyasını açın.  
  
2. `Symbols`Bölümünde grupları ve komutları Içeren [GuidSymbol](../extensibility/guidsymbol-element.md) öğesini bulun.  
  
3. Aşağıdaki örnekte gösterildiği gibi, eklemek istediğiniz her menü, Grup veya komut için bir [IDSymbol](../extensibility/idsymbol-element.md) öğesi oluşturun.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name`Ve öğelerinin öznitelikleri, `GuidSymbol` `IDSymbol` her yeni menü, Grup veya komut IÇIN GUID: ID çiftini sağlar. , `guid` VSPackage için tanımlanan bir komut kümesini temsil eder. Birden çok komut kümesi tanımlayabilirsiniz. Her GUID: ID çiftinin benzersiz olması gerekir.  
  
4. [Düğmeler](../extensibility/buttons-element.md) bölümünde, aşağıdaki örnekte gösterildiği gibi komutu tanımlamak Için bir [düğme](../extensibility/button-element.md) öğesi oluşturun.  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1. `guid`Ve alanlarını, `id` yenı komutun GUID: kimliğiyle eşleşecek şekilde ayarlayın.  
  
   2. Özniteliğini ayarlayın `priority` .  
  
        `priority`Özniteliği, üst grubundaki diğer nesneler arasındaki düğmenin konumunu öğrenmek için. vsct tarafından kullanılır.  
  
        Daha düşük öncelik değerleri olan komutlar yukarıda veya solunda, daha yüksek öncelik değerlerine sahip komutlarda görüntülenir. Yinelenen öncelik değerlerine izin verilir, ancak eşit önceliğe sahip komutların göreli konumu, VSPackages 'ın çalışma zamanında işlendiği sıraya göre belirlenir ve bu sıra önceden belirlenemez.  
  
        Özniteliği atlanırsa `priority` değeri 0 olarak ayarlanır.  
  
   3. Özniteliğini ayarlayın `type` . Çoğu durumda, değeri olacaktır `"Button"` . Diğer geçerli düğme türlerinin açıklamaları için bkz. [Button öğesi](../extensibility/button-element.md).  
  
5. Düğme tanımında, IDE 'de göründüğü gibi menünün adını içeren bir [ButtonText](../extensibility/buttontext-element.md) öğesi Içeren bir [dizeler](../extensibility/strings-element.md) öğesi ve **komut** penceresinde menüye erişmek Için kullanılan komutun adını içeren bir [CommandName](../extensibility/commandname-element.md) öğesi oluşturun.  
  
    Düğme metin dizesi ' & ' karakterini içeriyorsa, Kullanıcı ALT ve ' & ' karakterini hemen izleyen karaktere basarak menüyü açabilir.  
  
    Bir `Tooltip` öğe eklendiğinde, bir kullanıcı işaretçiyi düğmenin üzerine geldiğinde içerilen metnin görünmesine neden olur.  
  
6. Eğer varsa, komutuyla görüntülenecek olan simgeyi belirtmek için bir [simge](../extensibility/icon-element.md) öğesi ekleyin. Araç çubuklarındaki düğmeler için simgeler gereklidir ancak menü öğeleri için görüntülenmez. `guid`Öğesi ve, `id` `Icon` bölümünde tanımlanan bir [bit eşlem](../extensibility/bitmap-element.md) öğesiyle aynı olmalıdır `Bitmaps` .  
  
7. Düğmenin görünümünü ve davranışını değiştirmek için uygun şekilde komut bayrakları ekleyin. Bunu yapmak için, menü tanımına bir [CommandFlag](../extensibility/command-flag-element.md) öğesi ekleyin.  
  
8. Komutun üst grubunu ayarlayın. Üst grup, oluşturduğunuz bir grup, başka bir paketten bir grup veya IDE 'den bir grup olabilir. Örneğin, komutunu Visual Studio Düzen araç çubuğuna eklemek için **yorum** ve **kaldırma açıklaması** düğmelerini yanındaki üst öğeyi guidStdEditor: IDG_VS_EDITTOOLBAR_COMMENT olarak ayarlayın. Üst öğe Kullanıcı tanımlı bir gruptur, IDE 'de görünen bir menü, araç çubuğu veya araç penceresinin alt öğesi olmalıdır.  
  
    Bu bunu, tasarımınıza bağlı olarak iki şekilde yapabilirsiniz:  
  
   - `Button`Öğesinde, bir [üst](../extensibility/parent-element.md) öğe oluşturun ve `guid` ve `id` alanlarını, *birincil üst grup*olarak da bilinen komutu barındıracak olan grubun GUID 'si ve kimliği olarak ayarlayın.  
  
        Aşağıdaki örnek, Kullanıcı tanımlı bir menüde görünecek bir komutu tanımlar.  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   - Komut, komut `Parent` yerleşimi kullanılarak konumlandırılsa öğeyi atlayabilirsiniz. Bölümünden önce bir [CommandPlacements](../extensibility/commandplacements-element.md) öğesi oluşturun `Symbols` ve [CommandPlacement](../extensibility/commandplacement-element.md) `guid` `id` `priority` Aşağıdaki örnekte gösterildiği gibi komuta, a ve üst öğesine sahip bir commandyerleştirme öğesi ekleyin.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
      Aynı GUID: ID 'ye sahip ve farklı ebeveynler olan birden çok komut yerleşimi oluşturma, bir menünün birden çok konumda görünmesine neden olur. Daha fazla bilgi için bkz. [CommandPlacements](../extensibility/commandplacements-element.md) öğesi.  
  
    Komut grupları ve üst öğe hakkında daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../extensibility/creating-reusable-groups-of-buttons.md).  
  
   Bu noktada, komut IDE 'de görünür olur, ancak hiçbir işlevi olmayacaktır. Komut, paket şablonu tarafından oluşturulduysa, varsayılan olarak bir ileti görüntüleyen bir tıklama işleyicisine sahip olur.  
  
## <a name="handling-the-new-command"></a>Yeni komutu işleme  
 Yönetilen koddaki komutların çoğu, komutu bir <xref:System.ComponentModel.Design.MenuCommand> nesne veya <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> nesneyle ilişkilendirerek ve olay Işleyicilerini uygulayarak yönetilen paket çerçevesi (mpf) tarafından işlenebilir.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Arabirimi doğrudan komut işleme için kullanan kod için, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimini ve yöntemlerini uygulamanız gerekir. En önemli iki yöntem <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve ' dir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> .  
  
1. <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>Aşağıdaki örnekte gösterildiği gibi örneği alın.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2. <xref:System.ComponentModel.Design.CommandID>Aşağıdaki örnekte gösterildiği gibi, parametreleri parametresi olan bir nesne oluşturun ve işlenecek komutun kimliği.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Visual Studio paket şablonu iki koleksiyon sağlar `GuidList` ve `PkgCmdIDList` komut GUID 'Lerini ve kimliklerini tutmak için. Bunlar, şablon tarafından eklenen komutlar için otomatik olarak doldurulur, ancak el ile eklediğiniz komutlar için de ID girişini sınıfa eklemeniz gerekir `PkgCmdIdList` .  
  
     Alternatif olarak, <xref:System.ComponentModel.Design.CommandID> GUID 'nin ham dize değerini ve kimliğin tamsayı değerini kullanarak nesneyi doldurabilirsiniz.  
  
3. <xref:System.ComponentModel.Design.MenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Aşağıdaki örnekte gösterildiği gibi, komutunu ile birlikte işleyen yöntemini belirten bir veya nesnesi oluşturun <xref:System.ComponentModel.Design.CommandID> .  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     , <xref:System.ComponentModel.Design.MenuCommand> Statik komutlara uygundur. Dinamik menü öğesi, sorgu durumu olay işleyicilerini gerektirir. , <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Komutun ana bilgisayar menüsü açıldığında ve gibi bazı diğer özelliklerden oluşan olayı ekler <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Paket şablonu tarafından oluşturulan komutlar, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> paket sınıfının yöntemindeki bir nesneye varsayılan olarak geçirilir `Initialize()` .  
  
4. , <xref:System.ComponentModel.Design.MenuCommand> Statik komutlara uygundur. Dinamik menü öğesi, sorgu durumu olay işleyicilerini gerektirir. , <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Komutun ana bilgisayar menüsü açıldığında ve gibi bazı diğer özelliklerden oluşan olayı ekler <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Paket şablonu tarafından oluşturulan komutlar, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> paket sınıfının yöntemindeki bir nesneye varsayılan olarak geçirilir `Initialize()` . Visual Studio Sihirbazı `Initialize` kullanarak yöntemini uygular `MenuCommand` . Dinamik menü öğesi ekranları için, bir `OleMenuCommand` sonraki adımda gösterildiği gibi bunu olarak değiştirmeniz gerekir. Ayrıca, menü öğesi metnini değiştirmek için, aşağıdaki örnekte gösterildiği gibi,. vsct dosyasındaki menü komut düğmesine bir TextChanges komut bayrağı eklemeniz gerekir  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5. Yeni menü komutunu <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> arabirimindeki yönteme geçirin <xref:System.ComponentModel.Design.IMenuCommandService> . Bu, aşağıdaki örnekte gösterildiği gibi paket şablonu tarafından oluşturulan komutlar için varsayılan olarak gerçekleştirilir  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6. Komutu işleyen yöntemini uygulayın.  
  
#### <a name="to-implement-querystatus"></a>QueryStatus uygulamak için  
  
1. QueryStatus olayı, bir komut görüntülenmeden önce oluşur. Bu, kullanıcıya ulaşmadan önce olay işleyicisinde bu komutun özelliklerinin ayarlanmasını sağlar. Yalnızca nesne olarak eklenen komutlar <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Bu metoda erişebilir.  
  
    `EventHandler` <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Aşağıdaki örnekte gösterildiği gibi, komutu işlemek için oluşturulan nesnedeki olaya bir nesne ekleyin ( `menuItem` <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> örnek).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler`Nesnesine, menü komutunun durumu sorgulanırken çağrılan bir yöntemin adı verilir.  
  
2. Komut için sorgu durum işleyicisi yöntemini uygulayın. `object` `sender` Parametresi, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> metin dahil olmak üzere, menü komutunun çeşitli özniteliklerini ayarlamak için kullanılan bir nesnesine dönüşebilir. Aşağıdaki tabloda, <xref:System.ComponentModel.Design.MenuCommand> bayrağa karşılık gelen sınıftaki Özellikler (MPF sınıfının <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> türetildiği) gösterilmektedir <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> .  
  
   |MenuCommand özelliği|OLECMDF bayrağı|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    Bir menü komutunun metnini değiştirmek için, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> Aşağıdaki örnekte gösterildiği gibi nesnesi üzerinde özelliğini kullanın.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF, desteklenmeyen veya bilinmeyen grupların durumunu otomatik olarak işler. Yöntemi kullanılarak öğesine bir komut eklenmediyse <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> , komut desteklenmez.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>IOleCommandTarget arabirimini kullanarak komutları işleme  
 Arabirimi doğrudan kullanan kod için <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , VSPackage, arabirimin hem hem de yöntemlerinin uygulanması <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> gerekir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . VSPackage bir proje hiyerarşisi uygularsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> bunun yerine arabirimin ve yöntemlerinin uygulanması gerekir.  
  
 Ve yöntemlerinin her ikisi de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> giriş olarak tek bir komut kümesi `GUID` ve komut kimlikleri dizisi alacak şekilde tasarlanmıştır. VSPackages 'in, tek bir çağrıda birden çok kimlik kavramını tamamen desteklemesi önerilir. Ancak, VSPackage diğer VSPackages 'lerden çağrılmadığı sürece, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> yöntemleri iyi tanımlanmış bir sırada yürütüldüğü için, komut dizisinin yalnızca BIR komut kimliği içerdiğini varsayabilirsiniz. Yönlendirme hakkında daha fazla bilgi için bkz. [VSPackages 'de komut yönlendirme](../extensibility/internals/command-routing-in-vspackages.md).  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>Doğrudan komut işleme için arabirimi kullanan kod için, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> komutları işlemek üzere aşağıdaki gibi yöntemi VSPackage içinde uygulamanız gerekir.  
  
##### <a name="to-implement-the-querystatus-method"></a>QueryStatus yöntemini uygulamak için  
  
1. <xref:Microsoft.VisualStudio.VSConstants.S_OK>Geçerli komutlar için geri dönün.  
  
2. `cmdf`Parametresinin öğesini ayarlayın `prgCmds` .  
  
    Öğesinin değeri, `cmdf` <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> mantıksal OR () işleci kullanılarak birleştirilerek Numaralandırmadaki değerlerin mantıksal birleşimidir `|` .  
  
    Komutun durumuna göre uygun numaralandırmayı kullanın:  
  
   - Komut destekleniyorsa:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - Komut şu anda görünmez olmalıdır:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - Komut açık olursa ve tıklandığı gibi görünüyorsa:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      Türünde bir menüde barındırılan komutları işleme durumunda `MenuControllerLatched` , bayrak tarafından işaretlenen ilk komut, `OLECMDF_LATCHED` Başlangıç sırasında menü tarafından görüntülenen varsayılan komuttur. Menü türleri hakkında daha fazla bilgi için `MenuController` , bkz. [menü öğesi](../extensibility/menu-element.md).  
  
   - Komut şu anda etkinse:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - Komut bir kısayol menüsünün parçasıysa ve varsayılan olarak gizliyse:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - Komut `TEXTCHANGES` bayrağını kullanıyorsa, `rgwz` `pCmdText` parametresinin öğesini komutun yeni metin olarak ayarlayın ve `cwActual` `pCmdText` parametresinin öğesini komut dizesinin boyutuna ayarlayın.  
  
     Hata koşulları için, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi aşağıdaki hata durumlarını işlemelidir:  
  
   - GUID bilinmiyorsa veya desteklenmiyorsa, döndürün `OLECMDERR_E_UNKNOWNGROUP` .  
  
   - GUID biliniyorsa, ancak komut KIMLIĞI bilinmiyorsa veya desteklenmiyorsa, döndürün `OLECMDERR_E_NOTSUPPORTED` .  
  
   Metodun VSPackage uygulamasının, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> komutun desteklenip desteklenmediğini ve komutun başarıyla işlendiğine bağlı olarak belirli hata kodları döndürmesi gerekir.  
  
##### <a name="to-implement-the-exec-method"></a>Exec yöntemini uygulamak için  
  
- Komut `GUID` bilinmiyorsa, döndürün `OLECMDERR_E_UNKNOWNGROUP` .  
  
- Biliniyorsa, `GUID` ancak komut kimliği bilinmiyorsa, döndürün `OLECMDERR_E_NOTSUPPORTED` .  
  
- `GUID`Ve komut kimliği,. vsct dosyasında komutu tarafından kullanılan GUID: ID çiftiyle eşleşiyorsa, komutla ilişkili kodu yürütün ve döndürün <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)   
 [Menüleri ve Komutlari Genişletme](../extensibility/extending-menus-and-commands.md)
