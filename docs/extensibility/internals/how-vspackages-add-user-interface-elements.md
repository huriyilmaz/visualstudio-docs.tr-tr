---
title: VSPackages Kullanıcı Arabirimi Öğelerini Nasıl Ekler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d9cc3184009dd98e743064db1b8eb2abe6059d1
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649593"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackages kullanıcı arabirimi öğelerini nasıl ekler?
VSPackage, *.vsct* dosyası sayesinde Visual Studio'ya menüler, araç çubukları ve araç pencereleri gibi kullanıcı arabirimi (UI) öğeleri ekleyebilir.

Kullanıcı arabirimi öğeleri için tasarım yönergelerini [Visual Studio kullanıcı deneyimi yönergelerinde](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)bulabilirsiniz.

## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio komut tablosu mimarisi
Belirtildiği gibi, komut tablosu mimarisi, belirtilen mimari ilkeleri destekler. Komut tablosu mimarisinin soyutlamalarının, veri yapılarının ve araçlarının arkasındaki ilkeler aşağıdaki gibidir:

- Üç temel öğe türü vardır: menüler, komutlar ve gruplar. Menüler UI'de menüler, alt menüler, araç çubukları veya araç pencereleri olarak açıklanabilir. Komutlar, kullanıcının IDE'de yürütebileceği yordamlardır ve menü öğeleri, düğmeler, liste kutuları veya diğer denetimler olarak açıklanabilir. Gruplar hem menüler hem de komutlar için kapsayıcılardır.

- Her öğe, öğeyi açıklayan bir tanım, diğer öğelere göre önceliği ve davranışını değiştiren bayraklar tarafından belirtilir.

- Her öğenin üst öğesini açıklayan bir yerleşimi vardır. Bir öğenin birden çok ebeveyni olabilir, böylece ui'de birden çok konumda görünebilir.

Her komutun, o gruptaki tek çocuk olsa bile, ebeveyni olarak bir grubu olmalıdır. Her standart menüde bir üst grup da olmalıdır. Araç çubukları ve araç pencereleri kendi ebeveynleri gibi davranır. Bir grubun ana öğesi ana Visual Studio menü çubuğu veya herhangi bir menü, araç çubuğu veya araç penceresi ebeveyni olarak olabilir.

### <a name="how-items-are-defined"></a>Maddeler nasıl tanımlanır?
Bir *.vsct* dosyası XML formatındadır. Bir paketin UI öğelerini tanımlar ve bu öğelerin IDE'de nerede görünacağını belirler. Paketteki her menüye, grubuna veya komutuna `Symbols` ilk olarak bölüme bir GUID ve kimlik atanır. *.vsct* dosyasının geri kalanı boyunca, her menü, komut ve grup GUID ve kimlik birleşimi ile tanımlanır. Aşağıdaki örnekte, `Symbols` şablonda bir **Menü Komutu** seçildiğinde Visual Studio paket şablonu tarafından oluşturulan tipik bir bölüm gösterilmektedir.

```xml
<Symbols>
  <!-- This is the package guid. -->
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />

  <!-- This is the guid used to group the menu commands together -->
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
  </GuidSymbol>

  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}">
    <IDSymbol name="bmpPic1" value="1" />
    <IDSymbol name="bmpPic2" value="2" />
    <IDSymbol name="bmpPicSearch" value="3" />
    <IDSymbol name="bmpPicX" value="4" />
    <IDSymbol name="bmpPicArrows" value="5" />
  </GuidSymbol>
</Symbols>
```

`Symbols` Bölümün üst düzey öğesi [GuidSymbol öğesidir.](../../extensibility/guidsymbol-element.md) `GuidSymbol`öğeler, paketleri ve bileşen parçalarını tanımlamak için IDE tarafından kullanılan GUID'lerle eşlenir.

> [!NOTE]
> GUI'ler Visual Studio paket şablonu tarafından otomatik olarak oluşturulur. **Ayrıca Araçlar** menüsünde **GUID Oluştur'u** tıklatarak benzersiz bir GUID oluşturabilirsiniz.

İlk `GuidSymbol` öğe, `guid<PackageName>Pkg`paketin kendisi GUID olduğunu. Bu, Visual Studio tarafından paketi yüklemek için kullanılan GUID'dir. Genellikle, alt öğeleri yok.

Kural `GuidSymbol` olarak menüler ve komutlar ikinci bir `guid<PackageName>CmdSet`öğe altında gruplandırılır `GuidSymbol` ve `guidImages`bit eşlemleri üçüncü bir öğe altındadır. Bu kuralı izlemeniz gerekmez, ancak her menü, grup, komut ve bit `GuidSymbol` eşlemi bir öğenin alt öğesi olmalıdır.

Paket komut `GuidSymbol` kümesini temsil eden ikinci öğede birkaç `IDSymbol` öğe vardır. Her [IDSymbol öğesi](../../extensibility/idsymbol-element.md) bir adı sayısal bir değerle eşler ve komut kümesinin bir parçası olan bir menü, grup veya komutu temsil edebilir. Üçüncü `IDSymbol` `GuidSymbol` öğedeki öğeler, komutlar için simge olarak kullanılabilecek bit eşlemlerini temsil eder. GUID/ID çiftleri bir uygulamada benzersiz olduğundan, aynı `GuidSymbol` öğedeki iki çocuk aynı değere sahip olmayabilir.

### <a name="menus-groups-and-commands"></a>Menüler, gruplar ve komutlar
Bir menü, grup veya komut bir GUID ve kimliği varsa, IDE eklenebilir. Her UI öğesi aşağıdaki şeylere sahip olmalıdır:

- `guid` UI öğesi altında tanımlanan `GuidSymbol` öğenin adı eşleşen bir öznitelik.

- `id` İlişkili `IDSymbol` öğenin adıyla eşleşen bir öznitelik.

Birlikte, `guid` ve `id` öznitelikleri UI öğesinin *imzasını* oluşturur.

- `priority` UI öğesinin üst menüsündeki veya grubunda yerleşimini belirleyen bir öznitelik.

- Üst menünün `guid` veya `id` grubun imzasını belirten ve öznitelik veren bir [Üst öğe.](../../extensibility/parent-element.md)

#### <a name="menus"></a>Menüler
Her `Menus` menü, bölümdeki menü [öğesi](../../extensibility/menu-element.md) olarak tanımlanır. Menülerde , `guid` `id`, `priority` ve özniteliklere ve bir `Parent` öğeye ve ayrıca aşağıdaki ek özniteliklere ve alt öğeye sahip olmalıdır:

- Menü, `type` IDE'de bir tür menü olarak mı yoksa araç çubuğu olarak mı görünmesi gerektiğini belirten bir özniteliktir.

- IDE'deki menünün başlığını belirten [ButtonText](../../extensibility/buttontext-element.md) [öğesi](../../extensibility/strings-element.md) ve menüye erişmek için **Komut** penceresinde kullanılan adı belirten [Bir CommandName öğesi.](../../extensibility/commandname-element.md)

- İsteğe bağlı bayraklar. IDE'deki görünümünü veya davranışını değiştirmek için bir Menü tanımında [CommandFlag öğesi](../../extensibility/command-flag-element.md) görünebilir.

Araç `Menu` çubuğu gibi takılabilir bir öğe olmadığı sürece, her öğenin üst öğesi olarak bir grubu olmalıdır. Takılabilir menü kendi üst öğesidir. Öznitelik için menüler ve `type` değerler hakkında daha fazla bilgi için [Menü öğesi](../../extensibility/menu-element.md) belgelerine bakın.

Aşağıdaki örnekte, **Araçlar** menüsünün yanındaki Visual Studio menü çubuğunda görünen bir menü gösterilmektedir.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
  <Parent guid="guidSHLMainMenu" id="IDG_VS_MM_TOOLSADDINS" />
  <Strings>
    <ButtonText>TestMenu</ButtonText>
    <CommandName>TestMenu</CommandName>
  </Strings>
</Menu>
```

#### <a name="groups"></a>Gruplar
Grup, *.vsct* dosyasının `Groups` bölümünde tanımlanan bir öğedir. Gruplar sadece konteynerdir. Menüde bölen satır dışında IDE'de görünmezler. Bu nedenle, bir [Grup öğesi](../../extensibility/group-element.md) yalnızca imzası, önceliği ve üst öğesi ile tanımlanır.

Bir grubun bir menüsü, başka bir grup veya üst öğe olarak kendisi olabilir. Ancak, üst genellikle bir menü veya araç çubuğudur. Önceki örnekteki menü `IDG_VS_MM_TOOLSADDINS` grubun bir alt öğesidir ve bu grup Visual Studio menü çubuğunun bir alt öğesidir. Aşağıdaki örnekteki grup, önceki örnekte menünün bir alt öğesidir.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Bir menünün parçası olduğundan, bu grup genellikle komutları içerir. Ancak, diğer menüleri de içerebilir. Aşağıdaki örnekte gösterildiği gibi alt menüler bu şekilde tanımlanır.

```xml
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu" priority="0x0100" type="Menu">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>
  <Strings>
    <ButtonText>Sub Menu</ButtonText>
    <CommandName>Sub Menu</CommandName>
  </Strings>
</Menu>
```

#### <a name="commands"></a>Komutlar
IDE'ye sağlanan bir komut [Düğme öğesi](../../extensibility/button-element.md) veya [Combo öğesi](../../extensibility/combo-element.md)olarak tanımlanır. Bir menüde veya araç çubuğunda görünmesi için komutun üst öğesi olarak bir grubu olması gerekir.

##### <a name="buttons"></a>Düğmeler
Düğmeler `Buttons` bölümde tanımlanır. Bir kullanıcının tek bir komutu yürütmek için tıklatdığı herhangi bir menü öğesi, düğme veya diğer öğe düğme olarak kabul edilir. Bazı düğme türleri liste işlevselliği de içerebilir. Düğmeler menülerde sahip olduğu aynı gerekli ve isteğe bağlı özniteliklere sahiptir ve IDE'deki düğmeyi temsil eden bit eşlemenin GUID ve kimliğini belirten bir [Simge öğesine](../../extensibility/icon-element.md) de sahip olabilir. Düğmeler ve öznitelikleri hakkında daha fazla bilgi için [Düğmeler öğesi](../../extensibility/buttons-element.md) belgelerine bakın.

Aşağıdaki örnekteki düğme, önceki örnekte grubun bir alt öğesidir ve ide'de bu grubun üst menüsünde menü öğesi olarak görünür.

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

##### <a name="combos"></a>Tarak
Kombolar `Combos` bölümde tanımlanır. Her `Combo` öğe, IDE'deki açılır liste kutusunu temsil eder. Liste kutusu, açılan özelliğin `type` değerine bağlı olarak kullanıcılar tarafından yazılabilir veya yazılabilir olmayabilir. Kombinasyonlar düğmelerin sahip olduğu aynı öğelere ve davranışa sahiptir ve aşağıdaki ek özniteliklere de sahip olabilir:

- `defaultWidth` Piksel genişliğini belirten bir öznitelik.

- `idCommandList` Liste kutusunda görüntülenen öğeleri içeren bir liste belirten bir öznitelik. Komut listesi, açılan içeren `GuidSymbol` aynı düğümde bildirilmelidir.

Aşağıdaki örnekbir açılan öğeyi tanımlar.

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
Bir simgeyle birlikte görüntülenecek komutlar, `Icon` GUID ve Kimliğini kullanarak bit eşlebesine başvuran bir öğe içermelidir. Her bit `Bitmaps` eşlemi, bölümdeki [bitmap öğesi](../../extensibility/bitmap-element.md) olarak tanımlanır. Bir `Bitmap` tanım için gereken `guid` tek `href`öznitelikler ve kaynak dosyayı işaret eden. Kaynak dosya bir kaynak şeridiyse, şeritteki kullanılabilir görüntüleri listelemek için **usedList** özniteliği de gereklidir. Daha fazla bilgi için [Bitmap öğesi](../../extensibility/bitmap-element.md) belgelerine bakın.

### <a name="parenting"></a>Ebeveyn -lik
Aşağıdaki kurallar, bir öğenin başka bir öğeyi üst öğesi olarak nasıl çağırabileceğini yönetir.

|Öğe|Komut Tablosunun bu bölümünde tanımlanan|İçerdiği olabilir (ebeveyn olarak veya `CommandPlacements` bölüme yerleştirilerek veya her ikisi birden)|Içerebilir (üst olarak adlandırılır)|
|-------------| - | - | - |
|Grup|[Gruplar öğesi,](../../extensibility/groups-element.md)IDE, diğer VSPackages|Bir menü, bir grup, öğenin kendisi|Menüler, gruplar ve komutlar|
|Menü|[Menüler öğesi](../../extensibility/menus-element.md), IDE, diğer VSPackages|1 'den *n'ye* gruplar|0 'den *n'ye* gruplar|
|Araç Çubuğu|[Menüler öğesi](../../extensibility/menus-element.md), IDE, diğer VSPackages|Öğenin kendisi|0 'den *n'ye* gruplar|
|Menü Öğesi|[Düğmeler öğesi,](../../extensibility/buttons-element.md)IDE, diğer VSPackages|1'den *n'ye* gruplar, öğenin kendisi|-0 'den *n'ye* gruplar|
|Düğme|[Düğmeler öğesi,](../../extensibility/buttons-element.md)IDE, diğer VSPackages|1'den *n'ye* gruplar, öğenin kendisi||
|Birleşik|[Kombinasyon elemanı,](../../extensibility/combos-element.md)IDE, diğer VSPackages|1'den *n'ye* gruplar, öğenin kendisi||

### <a name="menu-command-and-group-placement"></a>Menü, komut ve grup yerleşimi
Bir menü, grup veya komut IDE'de birden fazla konumda görünebilir. Bir öğenin birden çok konumda görünmesi için, `CommandPlacements` [bölüme Komut Yerleştirme öğesi](../../extensibility/commandplacement-element.md)olarak eklenmesi gerekir. Herhangi bir menü, grup veya komut komut yerleştirme olarak eklenebilir. Ancak, araç çubukları birden çok içeriğe duyarlı konumlarda görüntülenemediğinden bu şekilde konumlandırılamaz.

Komut yerleşimleri `guid` `id`, `priority` ve öznitelikleri vardır. GUID ve KIMLIK, konumlandırılmış öğeninkilerle eşleşmelidir. Öznitelik, `priority` maddenin diğer öğelerle ilgili yerleşimini yönetir. IDE, aynı önceliğe sahip iki veya daha fazla öğeyi birleştirdiğinde, IDE paket kaynaklarının paket her oluşturulduğunda aynı sırada okunmasını garanti etmediğinden, yerleşimleri tanımsız kalır.

Birden çok konumda bir menü veya grup görünüyorsa, her örnekte o menünün veya grubun tüm alt çocukları görünür.

## <a name="command-visibility-and-context"></a>Komut görünürlüğü ve bağlamı
Birden çok VSPackages yüklendiğinde, menüler, menü öğeleri ve araç çubukları bir bolluk IDE yığılmayı olabilir. Bu sorunu önlemek için, *görünürlük kısıtlamaları* ve komut bayrakları kullanarak tek tek UI öğelerinin görünürlüğünü denetleyebilirsiniz.

### <a name="visibility-constraints"></a>Görünürlük kısıtlamaları
Görünürlük `VisibilityConstraints` kısıtlaması, bölümdeki [Bir Görünürlük Öğesi öğesi](../../extensibility/visibilityitem-element.md) olarak ayarlanır. Görünürlük kısıtlaması, hedef öğenin görünür olduğu belirli Ara birimi bağlamlarını tanımlar. Bu bölümde yer alan bir menü veya komut yalnızca tanımlanan bağlamlardan biri etkin olduğunda görünür. Bu bölümde bir menü veya komut başvurulmuyorsa, varsayılan olarak her zaman görünür. Bu bölüm gruplar için geçerli değildir.

`VisibilityItem`öğeleri aşağıdaki gibi üç öznitelikleri `guid` `id` olmalıdır: ve hedef UI öğesi ve `context`. Öznitelik, `context` hedef öğenin ne zaman görünür olacağını belirtir ve değeri olarak geçerli bir ara bilgi öğesini alır. Visual Studio için Ara bilgi bağlam sabitleri <xref:Microsoft.VisualStudio.VSConstants> sınıfın üyeleridir. Her `VisibilityItem` öğe yalnızca bir bağlam değeri alabilir. İkinci bir bağlam uygulamak için, aşağıdaki örnekte gösterildiği gibi aynı öğeyi işaret eden ikinci `VisibilityItem` bir öğe oluşturun.

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

### <a name="command-flags"></a>Komut bayrakları
Aşağıdaki komut bayrakları, uyguladıkları menülerin ve komutların görünürlüğünü etkileyebilir.

`AlwaysCreate`Menü, grubu veya düğmesi olmasa bile oluşturulur.

Geçerli:`Menu`

`CommandWellOnly`Komut üst düzey menüde görünmüyorsa ve ek kabuk özelleştirmesi için kullanılabilir hale getirmek istiyorsanız, örneğin bir anahtara bağlamak için bu bayrağı uygulayın. VSPackage yüklendikten sonra, bir kullanıcı **Seçenekler** iletişim kutusunu açarak ve ardından **Klavye Ortamı** kategorisi altında komut yerleşimini düzenleyerek bu komutları özelleştirebilir. Kısayol menülerinde, araç çubuklarına, menü denetleyicilerine veya alt menülere yerleştirmeyi etkilemez.

Geçerli: `Button`,`Combo`

`DefaultDisabled`Varsayılan olarak, komutu uygulayan VSPackage yüklenmezse veya QueryStatus yöntemi çağrılmazsa komut devre dışı bırakılır.

Geçerli: `Button`,`Combo`

`DefaultInvisible`Varsayılan olarak, komutu uygulayan VSPackage yüklenmezse veya QueryStatus yöntemi çağrılmadıysa komut görünmezdir.

`DynamicVisibility` Bayrakla birleştirilmelidir.

Geçerli: `Button`, `Combo`,`Menu`

`DynamicVisibility`Komutun görünürlüğü `QueryStatus` yöntem veya `VisibilityConstraints` bölümde yer alan bir bağlam GUID kullanılarak değiştirilebilir.

Menülerde görünen komutlar için geçerlidir, araç çubuklarında değil. Üst düzey araç çubuğu öğeleri, `OLECMDF_INVISIBLE` bayrak `QueryStatus` yöntemden döndürüldüğünde devre dışı edilebilir, ancak gizli tutulamaz.

Menüde, bu bayrak, üyeleri gizlendiğinde otomatik olarak gizlenmesi gerektiğini de gösterir. Üst düzey menülerde zaten bu davranış olduğundan, bu bayrak genellikle alt menülere atanır.

`DefaultInvisible` Bayrakla birleştirilmelidir.

Geçerli: `Button`, `Combo`,`Menu`

`NoShowOnMenuController`Bu bayrağı olan bir komut menü denetleyicisinde konumlandırılmışsa, komut açılır listede görünmez.

Geçerli:`Button`

Komut bayrakları hakkında daha fazla bilgi için [CommandFlag öğesi](../../extensibility/command-flag-element.md) belgelerine bakın.

#### <a name="general-requirements"></a>Genel gereksinimler
Komutunuzun görüntülenmeden ve etkinleştirilmeden önce aşağıdaki test serilerini geçmesi gerekir:

- Komut doğru konumlandırılır.

- Bayrak `DefaultInvisible` ayarlanmadı.

- Üst menü veya araç çubuğu görünür.

- Komut, [Görünürlük Kısıtlamaları öğesi](../../extensibility/visibilityconstraints-element.md) bölümündeki bir bağlam girişi nedeniyle görünmez değildir.

- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Arayüz ekranlarını uygulayan ve komutunuzu sağlayan VSPackage kodu. Hiçbir arayüz kodu onu ele geçirip harekete geçmedi.

- Bir kullanıcı komutunuzu tıklattığında, [Yönlendirme algoritmasında](../../extensibility/internals/command-routing-algorithm.md)özetlenen yordamın tabi olur.

## <a name="call-pre-defined-commands"></a>Önceden tanımlanmış komutları arama
[UsedCommands öğesi,](../../extensibility/usedcommands-element.md) VSPackages'in diğer VSPackages veya IDE tarafından sağlanan komutlara erişmesini sağlar. Bunu yapmak için, kullanılacak komutun GUID ve Kimliği'ne sahip bir [UsedCommand öğesi](../../extensibility/usedcommand-element.md) oluşturun. Bu, geçerli Visual Studio yapılandırmasının bir parçası olmasa bile komutun Visual Studio tarafından yüklenmesini sağlar. Daha fazla bilgi için [Bkz. UsedCommand öğesi.](../../extensibility/usedcommand-element.md)

## <a name="interface-element-appearance"></a>Arabirim öğesi görünümü
Komut öğelerini seçmek ve konumlandırmak için dikkat edilmesi gerekenler şunlardır:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]yerleşime bağlı olarak farklı görünen birçok UI öğesi sunar.

- `DefaultInvisible` Bayrağı kullanarak tanımlanan bir UI öğesi, <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> yöntemin VSPackage uygulamasıyla görüntülenmedikçe veya `VisibilityConstraints` bölümdeki belirli bir UI bağlamıyla ilişkilendirilmedikçe IDE'de görüntülenmez.

- Başarıyla konumlandırılmış bir komut bile görüntülenmeyebilir. Bunun nedeni, IDE'nin VSPackage'ın uyguladığı (veya uygulamadığı) arabirimlere bağlı olarak bazı komutları otomatik olarak gizlemesi veya görüntülemesidir. Örneğin, BIR VSPackage'ın bazı yapı arabirimleri uygulaması, yapıyla ilgili menü öğelerinin otomatik olarak gösterilmesine neden olur.

- Kullanıcı Gücü `CommandWellOnly` öğesinin tanımında bayrak uygulanması, komutun yalnızcılıkla eklenebilir.

- Komutlar yalnızca belirli Web Arabirimi bağlamlarında kullanılabilir, örneğin, yalnızca IDE tasarım görünümündeyken bir iletişim kutusu görüntülendiğinde.

- Belirli UI öğelerinin IDE'de görüntülenmesine neden olmak için bir veya daha fazla arabirim uygulamanız veya bazı kodlar yazmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md)
