---
title: VSPackages Kullanıcı arabirimi öğeleri ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 553c502c100cbb6ed4ae249096af408af14423b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833466"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage,. vsct dosyası aracılığıyla, menüler, araç çubukları ve araç pencereleri gibi kullanıcı arabirimi (UI) öğelerini Visual Studio 'ya ekleyebilir.  
  
 [Visual Studio Kullanıcı deneyimi yönergelerinden](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)Kullanıcı arabirimi öğeleri için tasarım yönergeleri bulabilirsiniz.  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio komut tablosu mimarisi  
 Belirtildiği gibi, komut tablosu mimarisi, mimari ilkelerini destekler. Soyutlamalar, veri yapıları ve komut tablosu mimarisinin araçlarının ardındaki olanaklar şunlardır:  
  
- Üç temel öğe türü vardır: menüler, komutlar ve gruplar. Menüler, Kullanıcı arabiriminde menüler, alt menüler, araç çubukları veya araç pencereleri olarak gösterilebilir. Komutlar, kullanıcının IDE 'de yürütebilecekleri yordamlardır ve menü öğeleri, düğmeler, liste kutuları veya diğer denetimler olarak ortaya çıkabilir. Gruplar hem menüler hem de komutlar için kapsayıcılardır.  
  
- Her öğe, öğeyi tanımlayan bir tanım ile belirtilir ve diğer öğelere göre önceliğini ve davranışını değiştiren bayrakları belirtir.  
  
- Her öğenin, öğenin üst öğesini açıklayan bir yerleştirmesi vardır. Bir öğe birden çok üst öğeye sahip olabilir, böylece kullanıcı arabiriminde birden çok konumda görünebilirler.  
  
     Her komutun, o gruptaki tek alt öğe olsa bile, üst öğesi olarak bir grubu olması gerekir. Her standart menünün de bir üst grubu olmalıdır. Araç çubukları ve araç pencereleri kendi üst öğeleri gibi davranır. Bir grup, ana Visual Studio menü çubuğunun veya herhangi bir menü, araç çubuğu ya da araç penceresinin üst öğesi olabilir.  
  
### <a name="how-items-are-defined"></a>Öğeler nasıl tanımlanır  
 . Vsct dosyaları XML olarak biçimlendirilir. . Vsct dosyası bir paket için Kullanıcı arabirimi öğelerini tanımlar ve bu öğelerin IDE 'de nerede göründüğünü belirler. Paketteki her menü, Grup veya komuta ilk olarak bölümünde bir GUID ve KIMLIK atanır `Symbols` . . Vsct dosyasının geri kalanı boyunca, her menü, komut ve Grup, GUID ve ID birleşimiyle tanımlanır. Aşağıdaki örnekte, `Symbols` şablonda bir **menü komutu** seçildiğinde Visual Studio paket şablonu tarafından oluşturulan tipik bir bölüm gösterilmektedir.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 Bölümünün en üst düzey öğesi `Symbols` [GuidSymbol öğesidir](../../extensibility/guidsymbol-element.md). `GuidSymbol` öğeler, paketleri ve bileşen parçalarını tanımlamak için IDE tarafından kullanılan GUID 'Lerle eşlenir.  
  
> [!NOTE]
> GUID 'Ler, Visual Studio paket şablonu tarafından otomatik olarak oluşturulur. **Araçlar** menüsünde **GUID oluştur** ' a TıKLAYARAK da benzersiz bir GUID oluşturabilirsiniz.  
  
 İlk `GuidSymbol` öğe olan "Guid [PackageName] pkg", paketin GUID 'sidir. Bu, paketi yüklemek için Visual Studio tarafından kullanılan GUID 'dir. Genellikle alt öğeleri yoktur.  
  
 Kurala göre, menüler ve komutlar ikinci bir `GuidSymbol` öğe olan "Guid [PackageName] CmdSet" ve bit eşlemler üçüncü bir `GuidSymbol` öğe, "Guıges" altında gruplandırılır. Bu kuralı izlemeniz gerekmez, ancak her menü, Grup, komut ve bit eşlem bir `GuidSymbol` öğenin alt öğesi olmalıdır.  
  
 İkinci `GuidSymbol` öğesinde, paket komut kümesini temsil eden birkaç öğesidir `IDSymbol` . Her [IDSymbol öğesi](../../extensibility/idsymbol-element.md) bir adı sayısal değerle eşleştirir ve komut kümesinin parçası olan bir menü, Grup veya komutu temsil edebilir. `IDSymbol`Üçüncü öğedeki öğeler, `GuidSymbol` Komutlar için simge olarak kullanılabilecek bit eşlemleri temsil eder. GUID/ID çiftlerinin bir uygulamada benzersiz olması gerektiğinden, aynı öğenin iki alt öğesi `GuidSymbol` aynı değere sahip olamaz.  
  
### <a name="menus-groups-and-commands"></a>Menüler, gruplar ve komutlar  
 Bir menü, Grup veya komut bir GUID ve ID 'ye sahip olduğunda, IDE 'ye eklenebilir. Her UI öğesi aşağıdaki şeylere sahip olmalıdır:  
  
- `guid` `GuidSymbol` UI öğesinin altında tanımlandığı öğenin adıyla eşleşen bir özniteliği.  
  
- `id`İlişkili öğenin adıyla eşleşen bir öznitelik `IDSymbol` .  
  
     Birlikte, `guid` ve `id` öznitelikleri, Kullanıcı arabirimi öğesinin *imzasını* oluşturan.  
  
- `priority`Kullanıcı arabirimi öğesinin üst menü veya grubunda yerleşimini belirleyen bir özniteliği.  
  
- [Parent Element](../../extensibility/parent-element.md) `guid` `id` Üst menünün veya grubun imzasını belirten ve öznitelikleri olan bir üst öğe.  
  
#### <a name="menus"></a>Menüler  
 Her menü, bölümünde bir [menü öğesi](../../extensibility/menu-element.md) olarak tanımlanır `Menus` . Menüler `guid` , `id` , ve `priority` öznitelikleri ve bir `Parent` öğesi ve ayrıca aşağıdaki ek öznitelikleri ve alt öğeleri içermelidir:  
  
- `type`Menünün IDE 'de bir menü türü veya bir araç çubuğu olarak görünüp görünmeyeceğini belirten bir özniteliği.  
  
- IDE 'deki menünün başlığını belirten bir bir [ButtonText öğesi](../../extensibility/buttontext-element.md)ve menüye erişmek için **komut** penceresinde kullanılan adı belirten bir [CommandName öğesi](../../extensibility/commandname-element.md)içeren [dizeler öğesi](../../extensibility/strings-element.md) .  
  
- İsteğe bağlı bayraklar. Bir [komut bayrağı öğesi](../../extensibility/command-flag-element.md) , IDE 'deki görünümünü veya davranışını değiştirmek için bir menü tanımında görünebilir.  
  
  `Menu`Bir araç çubuğu gibi yerleştirilebilir bir öğe olmadığı sürece her öğe kendi üst öğesi olarak bir gruba sahip olmalıdır. Yerleştirilebilir bir menü kendi üst öğesidir. Özniteliği için menüler ve değerler hakkında daha fazla bilgi için `type` , bkz. [menü öğesi](../../extensibility/menu-element.md) belgeleri.  
  
  Aşağıdaki örnekte, **Araçlar** menüsünün yanındaki Visual Studio menü çubuğunda görüntülenen bir menü gösterilmektedir.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Gruplar  
 Grup, `Groups` . vsct dosyasının bölümünde tanımlanan bir öğedir. Gruplar yalnızca kapsayıcılardır. Bu kişiler, bir menüdeki bölme çizgisi haricinde IDE 'de görünmez. Bu nedenle, bir [Grup öğesi](../../extensibility/group-element.md) yalnızca imzası, önceliği ve üst tarafından tanımlanır.  
  
 Bir grup, üst öğe olarak bir menü, başka bir grup veya kendisi olabilir. Ancak, üst öğe genellikle bir menü veya araç çubuğudur. Önceki örnekteki menü, grubun bir alt öğesidir `IDG_VS_MM_TOOLSADDINS` ve bu grup, Visual Studio menü çubuğunun bir alt öğesidir. Aşağıdaki örnekteki Grup, önceki örnekteki menünün bir alt öğesidir.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Bir menünün parçası olduğundan, bu grup genellikle komutları içerir. Ancak, diğer menüleri de içerebilir. Bu, aşağıdaki örnekte gösterildiği gibi alt menülerin tanımlanandır.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Komutlar  
 IDE 'ye sunulan bir komut, bir [Button öğesi](../../extensibility/button-element.md) ya da bir [kombo öğesi](../../extensibility/combo-element.md)olarak tanımlanır. Bir menü veya araç çubuğunda görünmesi için, komutun üst öğesi olarak bir grubu olmalıdır.  
  
##### <a name="buttons"></a>Düğmeler  
 Düğmeler `Buttons` bölümünde tanımlanmıştır. Herhangi bir menü öğesi, düğme veya kullanıcının tek bir komutu yürütmek için tıkladığı diğer öğe bir düğme olarak kabul edilir. Bazı düğme türlerinde ayrıca liste işlevselliği de bulunabilir. Düğmelerin aynı gerekli ve isteğe bağlı öznitelikleri vardır ve IDE 'deki düğmeyi temsil eden bit eşlemin GUID ve KIMLIĞINI belirten bir [simge öğesi](../../extensibility/icon-element.md) de olabilir. Düğmeler ve öznitelikleri hakkında daha fazla bilgi için, [düğmeler öğesi](../../extensibility/buttons-element.md) belgelerine bakın.  
  
 Aşağıdaki örnekte yer alan düğme, önceki örnekteki grubun bir alt öğesidir ve IDE 'de bu grubun ana menüsünde bir menü öğesi olarak görünür.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Combos  
 Combos, `Combos` bölümünde tanımlanmıştır. Her `Combo` öğe, IDE 'deki bir açılan liste kutusunu temsil eder. Birleşik giriş özniteliğinin değerine bağlı olarak, liste kutusu kullanıcılar tarafından yazılabilir veya olmayabilir `type` . Combos, düğmelerin sahip olduğu öğelere ve davranışa sahiptir ve aşağıdaki ek özniteliklere de sahip olabilir:  
  
- `defaultWidth`Piksel genişliğini belirten bir özniteliği.  
  
- `idCommandList`Liste kutusunda görüntülenen öğeleri içeren bir listeyi belirten bir özniteliği. Komut listesi, `GuidSymbol` Birleşik giriş içeren aynı düğümde bildirilmelidir.  
  
  Aşağıdaki örnek bir Birleşik öğe öğesi tanımlar.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Bit Eşlemler  
 Bir simge ile birlikte görüntülenecek komutlar `Icon` , GUID ve ID kullanarak bir bit eşlem 'e başvuran bir öğe içermelidir. Her bit eşlem, bölümünde bir [bit eşlem öğesi](../../extensibility/bitmap-element.md) olarak tanımlanır `Bitmaps` . Bir tanım için yalnızca gerekli öznitelikler `Bitmap` `guid` ve `href` kaynak dosyayı işaret eder. Kaynak dosya bir kaynak şeridinde ise, şerit 'teki kullanılabilir görüntüleri listelemek için bir **usedList** özniteliği de gereklidir. Daha fazla bilgi için, bkz. [bit eşlem öğesi](../../extensibility/bitmap-element.md) belgeleri.  
  
### <a name="parenting"></a>Olma  
 Aşağıdaki kurallar bir öğenin üst öğesi olarak başka bir öğeyi nasıl çağırabilme şeklini yönetir.  
  
|Öğe|Komut tablosunun bu bölümünde tanımlanmıştır|Bulunabilir (üst öğe veya `CommandPlacements` bölüme yerleştirme veya her ikisi de)|Bulunabilir (üst öğe olarak adlandırılır)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Gruplama|[Groups öğesi](../../extensibility/groups-element.md), IDE, diğer VSPackages|Bir menü, Grup, öğenin kendisi|Menüler, gruplar ve komutlar|  
|Menü|[Menüler öğesi](../../extensibility/menus-element.md), IDE, diğer VSPackages|1- *n* Grup|0- *n* Grup|  
|Araç Çubuğu|[Menüler öğesi](../../extensibility/menus-element.md), IDE, diğer VSPackages|Öğenin kendisi|0- *n* Grup|  
|Menü Öğesi|[Düğmeler öğesi](../../extensibility/buttons-element.md), IDE, diğer VSPackages|1- *n* Grup, öğenin kendisi|-0- *n* Grup|  
|Düğme|[Düğmeler öğesi](../../extensibility/buttons-element.md), IDE, diğer VSPackages|1- *n* Grup, öğenin kendisi||  
|Birleşik|[Combos öğesi](../../extensibility/combos-element.md), IDE, diğer VSPackages|1- *n* Grup, öğenin kendisi||  
  
### <a name="menu-command-and-group-placement"></a>Menü, komut ve grup yerleştirme  
 Bir menü, Grup veya komut IDE 'de birden fazla konumda görünebilir. Bir öğenin birden çok konumda görünmesi için, `CommandPlacements` bir [Commandyerleştirme öğesi](../../extensibility/commandplacement-element.md)olarak bölümüne eklenmelidir. Herhangi bir menü, Grup veya komut, komut yerleşimi olarak eklenebilir. Ancak, birden çok bağlama duyarlı konumlarda görünemediği için araç çubukları bu şekilde konumlandırılamıyor.  
  
 Komut yerleştirmelerinin `guid` , `id` , ve `priority` öznitelikleri vardır. GUID ve ID, konumlandırılmış olan öğe ile aynı olmalıdır. `priority`Özniteliği, öğenin diğer öğelerle ilgili yerleşimini yönetir. IDE, aynı önceliğe sahip iki veya daha fazla öğeyi birleşdiğinde, IDE paket kaynaklarının paket her oluşturulduğunda aynı sırada okunduğundan emin olmadığından, bunların yerleşimi tanımsızdır.  
  
 Bir menü veya Grup birden çok konumda görünürse, bu menünün veya grubun tüm alt öğeleri her örnekte görünür.  
  
## <a name="command-visibility-and-context"></a>Komut görünürlüğü ve bağlamı  
 Birden çok VSPackages yüklendiğinde, menülerin, menü öğelerinin ve araç çubuklarının bir yeteretsi IDE 'nin dağınıklığını etkileyebilir. Bu sorundan kaçınmak için, tek tek kullanıcı arabirimi öğelerinin görünürlüğünü *görünürlük kısıtlamalarını* ve komut bayraklarını kullanarak kontrol edebilirsiniz.  
  
##### <a name="visibility-constraints"></a>Görünürlük kısıtlamaları  
 Görünürlük kısıtlaması, bölümünde bir [VisibilityItem öğesi](../../extensibility/visibilityitem-element.md) olarak ayarlanır `VisibilityConstraints` . Görünürlük kısıtlaması, hedef öğenin görünür olduğu belirli kullanıcı arabirimi bağlamlarını tanımlar. Bu bölümde yer alan bir menü veya komut yalnızca tanımlı bağlamlarından biri etkin olduğunda görülebilir. Bu bölümde bir menü veya komuta başvurulmuyorsa, her zaman varsayılan olarak görünür. Bu bölüm, gruplar için geçerlidir.  
  
 `VisibilityItem` öğeler, aşağıdaki gibi üç özniteliğe sahip olmalıdır: `guid` ve `id` hedef UI öğesi ve `context` . `context`Öznitelik, hedef öğenin görünür olacağını belirtir ve değeri olarak geçerli herhangi bir kullanıcı arabirimi bağlamını alır. Visual Studio için Kullanıcı arabirimi bağlamı sabitleri, <xref:Microsoft.VisualStudio.VSConstants> sınıfının üyeleridir. Her `VisibilityItem` öğe yalnızca bir bağlam değeri alabilir. İkinci bir bağlam uygulamak için, `VisibilityItem` Aşağıdaki örnekte gösterildiği gibi, aynı öğeye işaret eden ikinci bir öğe oluşturun.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>Komut bayrakları  
 Aşağıdaki komut bayrakları, uygulanan menülerin ve komutların görünürlüğünü etkileyebilir.  
  
 AlwaysCreate  
 Menü, Grup veya düğme içermediğinden bile oluşturulur.  
  
 Geçerli: `Menu`  
  
 Yalnızca commandwell  
 Bu bayrağı, komut üst düzey menüde görünmezse ve ek kabuk özelleştirmesi için kullanılabilir hale getirmek istiyorsanız, örneğin bir anahtara bağlama yaparsanız uygulayın. VSPackage yüklendikten sonra, Kullanıcı bu komutları özelleştirerek **Seçenekler** iletişim kutusunu açıp **klavye ortamı** kategorisi altındaki komut yerleşimini düzenleyerek özelleştirebilirsiniz. , Kısayol menülerinde, araç çubuklarında, menü denetleyicilerinde veya alt menülerde yerleşimi etkilemez.  
  
 Geçerli: `Button` , `Combo`  
  
 DefaultDisabled  
 Varsayılan olarak, komutu uygulayan VSPackage yüklü değilse veya QueryStatus yöntemi çağrılmışsa, komut devre dışıdır.  
  
 Geçerli: `Button` , `Combo`  
  
 Defaulınvisible  
 Varsayılan olarak, komutu uygulayan VSPackage yüklü değilse veya QueryStatus yöntemi çağrılmışsa, komut görünmez.  
  
 Bayrağıyla birleştirilmelidir `DynamicVisibility` .  
  
 Geçerli: `Button` , `Combo` , `Menu`  
  
 DynamicVisibility  
 Komutun görünürlüğü, QueryStatus yöntemi veya bölümüne dahil olan bir bağlam GUID 'SI kullanılarak değiştirilebilir `VisibilityConstraints` .  
  
 Araç çubuklarında değil menülerde görüntülenen komutlar için geçerlidir. QueryStatus yönteminden OLECMDF_INVISIBLE bayrağı döndürüldüğünde, üst düzey araç çubuğu öğeleri devre dışı bırakılabilir, ancak gizlenemez.  
  
 Bir menüde, bu bayrak, üyeleri gizli olduğunda otomatik olarak gizlenmesi gerektiğini de belirtir. Üst düzey menülerde bu davranış zaten olduğu için bu bayrak genellikle alt menülere atanır.  
  
 Bayrağıyla birleştirilmelidir `DefaultInvisible` .  
  
 Geçerli: `Button` , `Combo` , `Menu`  
  
 NoShowOnMenuController  
 Bu bayrağa sahip bir komut bir menü denetleyicisine yerleştirilmezse, komut açılan listede görünmez.  
  
 Geçerli: `Button`  
  
 Komut bayrakları hakkında daha fazla bilgi için bkz. [komut bayrağı öğe](../../extensibility/command-flag-element.md) belgeleri.  
  
##### <a name="general-requirements"></a>Genel gereksinimler  
 Komutunuz görüntülenmeden ve etkinleştirilmeden önce aşağıdaki test serisini iletmelidir:  
  
- Komut doğru şekilde konumlandırıldı.  
  
- `DefaultInvisible`Bayrak ayarlanmadı.  
  
- Üst menü ya da araç çubuğu görünür.  
  
- Bu komut, [Visibilitykısıtlamalar öğesi](../../extensibility/visibilityconstraints-element.md) bölümündeki bir bağlam girişi nedeniyle görünmez değildir.  
  
- Arabirimi uygulayan VSPackage kodu, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> komutunuz görüntüleyip sağlar. Hiçbir arabirim kodu yakalandığından ve üzerinde işlem yaptığı için bu yok.  
  
- Bir Kullanıcı komutunuzu tıkladığında, [yönlendirme algoritmasında](../../extensibility/internals/command-routing-algorithm.md)özetlenen yordama tabi olur.  
  
## <a name="calling-pre-defined-commands"></a>Önceden tanımlanmış komutlar çağrılıyor  
 [UsedCommands öğesi](../../extensibility/usedcommands-element.md) , VSPackages 'ın diğer VSPackages tarafından veya IDE tarafından sağlanmış komutlara erişmesini sağlar. Bunu yapmak için, kullanılacak komutun GUID ve KIMLIĞINE sahip bir [UsedCommand öğesi](../../extensibility/usedcommand-element.md) oluşturun. Bu, geçerli Visual Studio yapılandırmasının bir parçası olmasa bile, komutun Visual Studio tarafından yüklenmesini sağlar. Daha fazla bilgi için bkz. [UsedCommand öğesi](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Arabirim öğesi görünümü  
 Komut öğelerini seçme ve konumlandırma konuları aşağıdaki gibidir:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , yerleştirmeye göre farklı şekilde görüntülenen birçok UI öğesi sağlar.  
  
- Bayrak kullanılarak tanımlanan bir UI öğesi, `DefaultInvisible` yönteminin VSPackage uygulamasıyla görüntülenmediği <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> ya da bölümde belırlı bir UI bağlamı ile ilişkili OLMADıĞı müddetçe IDE 'de görüntülenmez `VisibilityConstraints` .  
  
- Başarılı bir şekilde konumlandırılmış komut görünmeyebilir. Bunun nedeni, IDE 'nin, VSPackage 'ın uygulamadığı arayüzlere bağlı olarak bazı komutları otomatik olarak gizlediğini veya görüntülediğini gösterir. Örneğin, bir VSPackage 'ın bazı derleme arabirimlerinin uygulanması, derleme ile ilgili menü öğelerinin otomatik olarak gösterilmesine neden olur.  
  
- Bayrak, `CommandWellOnly` UI öğesinin tanımına uygulandığında, komutun yalnızca özelleştirmeye göre eklenebileceği anlamına gelir.  
  
- Komutlar yalnızca belirli kullanıcı arabirimi bağlamlarında kullanılabilir (örneğin, IDE Tasarım görünümünde olduğunda bir iletişim kutusu görüntülendiğinde).  
  
- IDE 'de belirli kullanıcı arabirimi öğelerinin görüntülenmesine neden olmak için bir veya daha fazla arabirim uygulamanız veya kod yazmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve Komutlari Genişletme](../../extensibility/extending-menus-and-commands.md)
