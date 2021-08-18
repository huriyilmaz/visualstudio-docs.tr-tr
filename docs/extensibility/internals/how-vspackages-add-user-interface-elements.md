---
title: VSPackage'lar Kullanıcı Arabirimi Öğeleri | Microsoft Docs
description: VSPackage'ların menüler, araç çubukları ve araç pencereleri gibi kullanıcı arabirimi (UI) öğelerini Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8234183455083a05095acef1d73ad87917100660
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063245"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackage'lar kullanıcı arabirimi öğelerini nasıl ekler?
VSPackage, *.vsct* dosyası ile kullanıcı arabirimi (UI) öğeleri (menüler, araç çubukları ve araç pencereleri Visual Studio öğeleri ekleyebilir.

Kullanıcı deneyimi yönergelerini kullanarak kullanıcı arabirimi [öğelerine Visual Studio yönergelerini bulabilirsiniz.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="the-visual-studio-command-table-architecture"></a>Komut Visual Studio mimarisi
Yukarıda da olduğu gibi, komut tablosu mimarisi, yukarıda belirtilen mimari ilkelerini destekler. Komut tablosu mimarisinin soyutlamalarının, veri yapılarının ve araçlarının ardındaki kavramlar aşağıdaki gibidir:

- Üç temel öğe türü vardır: menüler, komutlar ve gruplar. Menüler kullanıcı arabiriminde menüler, alt menüler, araç çubukları veya araç pencereleri olarak gösterebilirsiniz. Komutlar, kullanıcının IDE'de yürütebilirsiniz yordamlarıdır ve bunlar menü öğeleri, düğmeler, liste kutuları veya diğer denetimler olarak gösterebilirsiniz. Gruplar hem menüler hem de komutlar için kapsayıcıdır.

- Her öğe, öğeyi, diğer öğelere göre önceliğini ve davranışını değiştiren bayrakları açıklayan bir tanım tarafından belirtilir.

- Her öğenin, öğenin üst öğesini açıklayan bir yerleşimi vardır. Bir öğenin kullanıcı arabiriminde birden çok konumda görünmesi için birden çok ebeveynleri olabilir.

Bu gruptaki tek alt öğe olsa bile her komutun üst öğesi olarak bir grubu olması gerekir. Her standart menüde bir üst grup da olması gerekir. Araç çubukları ve araç pencereleri kendi ebeveynleri gibi davranır. Bir grubun ana menü çubuğunda veya herhangi bir Visual Studio araç çubuğu ya da araç penceresi olabilir.

### <a name="how-items-are-defined"></a>Öğelerin nasıl tanımlandığı
*.vsct dosyası* XML biçiminde biçimlendirildi. Bir paket için kullanıcı arabirimi öğelerini tanımlar ve bu öğelerin IDE'de nerede görün olduğunu belirler. Pakette yer alan her menüye, gruba veya komuta öncelikle bölümünde bir GUID ve kimlik `Symbols` atanır. *.vsct* dosyasının geri kalanında her menü, komut ve grup, GUID ve kimlik bileşimiyle tanımlanır. Aşağıdaki örnekte, şablonda bir Menü Komutu seçildiğinde Visual Studio paketi `Symbols` şablonu tarafından oluşturulan tipik bir bölüm görüntülenir. 

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

bölümünün üst düzey öğesi `Symbols` [GuidSymbol öğesidir.](../../extensibility/guidsymbol-element.md) `GuidSymbol` öğeleri, paketleri ve bileşen parçalarını tanımlamak için IDE tarafından kullanılan GUID'lerle eşler.

> [!NOTE]
> GUID'ler, otomatik olarak Visual Studio şablonu tarafından oluşturulur. Araçlar menüsünde GUID Oluştur'a tıklayarak **da benzersiz bir GUID** **oluşturabilirsiniz.**

İlk `GuidSymbol` öğesi olan `guid<PackageName>Pkg` , paketin kendi GUID'idir. Bu, paketi yüklemek için Visual Studio GUID'tir. Genellikle alt öğelerine sahip değildir.

Kurala göre menüler ve komutlar ikinci bir öğe altında `GuidSymbol` gruplandı `guid<PackageName>CmdSet` ve bit eşlemler üçüncü öğe `GuidSymbol` olan altında yer `guidImages` almaktadır. Bu kuralı izlemeniz gerek yoktur, ancak her menü, grup, komut ve bit eşlem bir öğenin alt öğesi `GuidSymbol` olması gerekir.

Paket komut `GuidSymbol` kümelerini temsil eden ikinci öğede birkaç öğe `IDSymbol` vardır. Her [IDSymbol](../../extensibility/idsymbol-element.md) öğesi bir adı sayısal değerle eşler ve komut kümesine bir menü, grup veya komutu temsil ediyor olabilir. Üçüncü `IDSymbol` öğedeki `GuidSymbol` öğeler, komutlar için simge olarak kullanılan bit eşlemleri temsil ediyor. GUID/ID çiftlerinin bir uygulamada benzersiz olması gerekir, çünkü aynı öğenin iki öğesi `GuidSymbol` aynı değere sahip olabilir.

### <a name="menus-groups-and-commands"></a>Menüler, gruplar ve komutlar
Bir menü, grup veya komutun GUID ve kimliği olduğunda IDE'ye eklenebilir. Her kullanıcı arabirimi öğesi aşağıdakilere sahip olmalı:

- Kullanıcı `guid` arabirimi öğesinin altında `GuidSymbol` tanımlandığı öğenin adıyla eşleşen bir öznitelik.

- `id`İlişkili öğenin adıyla eşleşen bir `IDSymbol` öznitelik.

ve öznitelikleri `guid` `id` birlikte ui öğesinin *imzasını* oluştur.

- Kullanıcı `priority` arabirimi öğesinin üst menüsünde veya grubunda yerleşimini belirleyen öznitelik.

- Üst [menü veya](../../extensibility/parent-element.md) grubun `guid` `id` imzasını belirten ve özniteliklerine sahip üst öğe.

#### <a name="menus"></a>Menüler
Her menü, bölümünde [Bir Menü öğesi](../../extensibility/menu-element.md) olarak `Menus` tanımlanır. Menülerde `guid` , `id` , ve öznitelikleri ve bir öğesi ve ayrıca aşağıdaki ek `priority` `Parent` öznitelikler ve çocukların olması gerekir:

- Men sunucunun IDE'de bir tür menü olarak mı yoksa araç çubuğu olarak mı `type` görünmesi gerektiğini belirten öznitelik.

- IDE'deki mengemin başlığını belirten [ButtonText](../../extensibility/buttontext-element.md)öğesi ve menüye erişmek için Komut penceresinde kullanılan adı belirten [CommandName](../../extensibility/commandname-element.md)öğesi içeren  [Dizeler](../../extensibility/strings-element.md) öğesi.

- İsteğe bağlı bayraklar. IDE'de görünümünü veya davranışını değiştirmek için bir menü tanımında [CommandFlag](../../extensibility/command-flag-element.md) öğesi görünebilir.

Araç `Menu` çubuğu gibi yerleştirilebilir bir öğe olmadığı sürece her öğenin üst öğesi olarak bir grubu olması gerekir. Yerleştirilebilir menü kendi üst öğesidir. Özniteliğin menüleri ve değerleri hakkında daha fazla `type` bilgi için Menü öğesi [belgelerine](../../extensibility/menu-element.md) bakın.

Aşağıdaki örnekte, Araçlar menüsünün yanında Visual Studio menü çubuğunda görünen bir **menü görüntülenir.**

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
Grup, `Groups` *.vsct* dosyasının bölümünde tanımlanan bir öğedir. Gruplar yalnızca kapsayıcıdır. Bunlar IDE'de, menüde bölünen bir satır olarak görünmeleri dışında görünmez. Bu nedenle, [bir Group](../../extensibility/group-element.md) öğesi yalnızca imza, öncelik ve üst öğe tarafından tanımlanır.

Bir grubun bir menüsü, başka bir grubu veya kendisi üst öğe olabilir. Ancak üst öğe genellikle bir menü veya araç çubuğu olabilir. Önceki örnekte yer alan menü, grubun alt öğesidir ve bu grup da Visual Studio `IDG_VS_MM_TOOLSADDINS` alt öğesidir. Aşağıdaki örnekte yer alan grup, önceki örnekte yer alan menenin alt öğesidir.

```xml
<Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" priority="0x0600">
  <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
</Group>
```

Bir menenin parçası olduğundan, bu grup genellikle komutlar içerir. Ancak, başka menüler de içerebilir. Aşağıdaki örnekte gösterildiği gibi altmenüsler bu şekilde tanımlanır.

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
IDE'ye sağlanan bir komut, Button öğesi veya [Birleşik giriş](../../extensibility/button-element.md) öğesi [olarak tanımlanır.](../../extensibility/combo-element.md) Bir menüde veya araç çubuğunda görünmesi için, komutun üst öğesi olarak bir grubu olması gerekir.

##### <a name="buttons"></a>Düğmeler
Düğmeler bölümünde `Buttons` tanımlanır. Bir kullanıcının tek bir komutu yürütmek için tıkladığında herhangi bir menü öğesi, düğme veya diğer öğe bir düğme olarak kabul edilir. Bazı düğme türleri liste işlevlerini de içerebilir. Düğmeler, menülerin sahip olduğu gerekli ve isteğe bağlı özniteliklere sahiptir ve IDE'deki düğmeyi temsil eden bit eşlem GUID'lerini ve kimliğini belirten bir [Icon](../../extensibility/icon-element.md) öğesine de sahip olabilir. Düğmeler ve öznitelikleri hakkında daha fazla bilgi için Düğmeler öğesi [belgelerine](../../extensibility/buttons-element.md) bakın.

Aşağıdaki örnekte yer alan düğme, önceki örnekte grubun alt öğesidir ve IDE'de bu grubun üst menüsünde menü öğesi olarak görünür.

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
Birleşik girişler bölümünde `Combos` tanımlanır. Her `Combo` öğe IDE'de bir açılan liste kutusunu temsil eder. Birleşik giriş özniteliğinin değerine bağlı olarak liste kutusu kullanıcılar tarafından yazılabilir `type` veya yazılamaz. Birleşik girişler, düğmelerin sahip olduğu öğelere ve davranışlara sahiptir ve aşağıdaki ek özniteliklere de sahip olabilir:

- Piksel `defaultWidth` genişliğini belirten bir öznitelik.

- `idCommandList`Liste kutusunda görüntülenen öğeleri içeren bir listeyi belirten öznitelik. Komut listesi, birleşik giriş içeren aynı `GuidSymbol` düğümde bildir gerekir.

Aşağıdaki örnek bir birleşik giriş öğesini tanımlar.

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
Bir simgeyle birlikte görüntülenecek komutlar, GUID ve kimliği kullanılarak bit eşlem öğesine `Icon` başvuran bir öğe içermeli. Her bit eşlem, bölümünde [bir Bit Eşlem](../../extensibility/bitmap-element.md) öğesi olarak `Bitmaps` tanımlanır. Bir tanım için gereken tek `Bitmap` öznitelikler, kaynak `guid` dosyaya göre ve `href` öznitelikleridir. Kaynak dosya bir kaynak şeridi ise, şeritte kullanılabilir görüntüleri listeley için bir **usedList** özniteliği de gereklidir. Daha fazla bilgi için Bitmap öğesi [belgelerine](../../extensibility/bitmap-element.md) bakın.

### <a name="parenting"></a>Ebeveyn -lik
Aşağıdaki kurallar, bir öğenin üst öğe olarak başka bir öğeyi nasıl çağırasını yönetir.

|Öğe|Komut Tablosu'nın bu bölümünde tanımlanmıştır|Içerebilir (üst öğe olarak veya bölüme yerleştirme ya da `CommandPlacements` her ikisini birden)|içerebilir (üst olarak adlandırılır)|
|-------------| - | - | - |
|Grup|[Groups öğesi,](../../extensibility/groups-element.md)IDE, diğer VSPackage'lar|Menü, grup ve öğenin kendisi|Menüler, gruplar ve komutlar|
|Menü|[Menü öğesi,](../../extensibility/menus-element.md)IDE, diğer VSPackage'lar|*1-n* grup|0 *-n* grup|
|Araç Çubuğu|[Menü öğesi,](../../extensibility/menus-element.md)IDE, diğer VSPackage'lar|Öğenin kendisi|0 *-n* grup|
|Menü Öğesi|[Düğmeler öğesi,](../../extensibility/buttons-element.md)IDE, diğer VSPackage'lar|*1-n* grup, öğenin kendisi|-0 *-n gruplara*|
|Düğme|[Düğmeler öğesi,](../../extensibility/buttons-element.md)IDE, diğer VSPackage'lar|*1-n* grup, öğenin kendisi||
|Birleşik|[Combos öğesi,](../../extensibility/combos-element.md)IDE, diğer VSPackage'lar|*1-n* grup, öğenin kendisi||

### <a name="menu-command-and-group-placement"></a>Menü, komut ve grup yerleşimi
IDE'de bir menü, grup veya komut birden fazla konumda görünebilir. Bir öğenin birden çok konumda görünmesi için bir `CommandPlacements` [CommandPlacement](../../extensibility/commandplacement-element.md)öğesi olarak bölümüne eklenmiştir. Herhangi bir menü, grup veya komut, komut yerleştirme olarak eklenebilir. Ancak, araç çubukları bağlama duyarlı birden çok konumda görünemleri nedeniyle bu şekilde konum olamaz.

Komut yerleştirmeleri `guid` , `id` ve `priority` özniteliklerine sahip. GUID ve kimlik, konumlara sahip öğeninkilerle eşleşmesi gerekir. özniteliği, `priority` öğenin diğer öğelerle ilgili yerleşimini yönetir. IDE, aynı önceliğe sahip iki veya daha fazla öğeyi birleştirmiş olduğunda, IDE paket kaynaklarının paket her edinde aynı sırayla okunacaklarını garanti etmez.

Bir menü veya grup birden çok konumda görünürse, bu menü veya grubun tüm öğeleri her örnekte görünür.

## <a name="command-visibility-and-context"></a>Komut görünürlüğü ve bağlamı
Birden çok VSPackage yüklü olduğunda, menülerin, menü öğelerinin ve araç çubuklarının yayılması IDE'de dağınıklığa neden olabilir. Bu sorunu önlemek için görünürlük kısıtlamalarını ve komut bayraklarını kullanarak tek tek kullanıcı arabirimi *öğelerinin görünürlüğünü* kontrol altına aabilirsiniz.

### <a name="visibility-constraints"></a>Görünürlük kısıtlamaları
Görünürlük kısıtlaması, bölümünde [VisibilityItem öğesi](../../extensibility/visibilityitem-element.md) olarak `VisibilityConstraints` ayarlanır. Görünürlük kısıtlaması, hedef öğenin görünür olduğu belirli kullanıcı arabirimi bağlamlarını tanımlar. Bu bölümde yer alan bir menü veya komut yalnızca tanımlı bağlamlardan biri etkin olduğunda görünür. Bu bölümde bir menüye veya komuta başvurulmazsa, bu her zaman varsayılan olarak görünür durumdadır. Bu bölüm gruplar için geçerli değildir.

`VisibilityItem` öğelerinin üç özniteliği olmalıdır: hedef kullanıcı arabirimi öğesinin ve `guid` `id` ve `context` . özniteliği, `context` hedef öğenin ne zaman görünür olacağını belirtir ve değeri olarak geçerli ui bağlamını alır. Kullanıcı arabirimi bağlam sabitleri Visual Studio sınıfının <xref:Microsoft.VisualStudio.VSConstants> üyeleridir. Her `VisibilityItem` öğe yalnızca bir bağlam değeri alır. İkinci bir bağlam uygulamak için, aşağıdaki örnekte gösterildiği gibi aynı öğeyi `VisibilityItem` ifade eden ikinci bir öğe oluşturun.

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
Aşağıdaki komut bayrakları, uygulanabilecek menülerin ve komutların görünürlüğünü etkileyebilir.

`AlwaysCreate` Menü, grup veya düğme yoksa bile oluşturulur.

Şu için geçerlidir: `Menu`

`CommandWellOnly` Komut üst düzey menüde görünmüyorsa ve ek kabuk özelleştirmesi için kullanılabilir hale (örneğin, bir anahtara bağlama) bu bayrağı uygulayabilirsiniz. VSPackage yüklendikten sonra, kullanıcı Seçenekler iletişim kutusunu  açıp klavye ortamı kategorisindeki komut yerleşimini düzenleyerek bu **komutları özelleştirilebilir.** Kısayol menüleri, araç çubukları, menü denetleyicileri veya alt menülerin yerleşimini etkilemez.

Şu için geçerlidir: `Button` , `Combo`

`DefaultDisabled` Varsayılan olarak, komutu uygulayan VSPackage yüklenmezse veya QueryStatus yöntemi çağrılmasa komut devre dışı bırakılır.

Şu için geçerlidir: `Button` , `Combo`

`DefaultInvisible` Varsayılan olarak, komutu uygulayan VSPackage yüklenmezse veya QueryStatus yöntemi çağrılmasa komut görünmez.

bayrağıyla `DynamicVisibility` birleştirildi.

Şu için geçerlidir: `Button` , `Combo` , `Menu`

`DynamicVisibility` Komutun görünürlüğü, bölümüne dahil edilen bir bağlam `QueryStatus` GUID'si veya yöntemi kullanılarak `VisibilityConstraints` değiştirilebilir.

Araç çubuklarında değil, menülerde görünen komutlar için geçerlidir. En üst düzey araç çubuğu öğeleri, yönteminden bayrağı döndürül olduğunda devre dışı `OLECMDF_INVISIBLE` bırakılabilir, ancak `QueryStatus` gizlenemez.

Bir menüde bu bayrak ayrıca üyeleri gizlenirken otomatik olarak gizlenir. Üst düzey menüler zaten bu davranışa sahip olduğundan bu bayrak genellikle alt menülere atanır.

bayrağıyla `DefaultInvisible` birleştirildi.

Şu için geçerlidir: `Button` , `Combo` , `Menu`

`NoShowOnMenuController` Bu bayrağı olan bir komut bir menü denetleyicisinde konumlandı ise, komut açılan listede görünmez.

Şu için geçerlidir: `Button`

Komut bayrakları hakkında daha fazla bilgi için [CommandFlag öğesi belgelerine](../../extensibility/command-flag-element.md) bakın.

#### <a name="general-requirements"></a>Genel gereksinimler
Komutun görüntülenmeden ve etkinleştirilmeden önce aşağıdaki test dizilerini geçmesi gerekir:

- Komut doğru şekilde konumlandı.

- `DefaultInvisible`Bayrağı ayarlanmaz.

- Üst menü veya araç çubuğu görünür durumdadır.

- [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) öğesi bölümündeki bir bağlam girişi nedeniyle komut görünmez.

- Arabirimi uygulayan VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> kodu komutu görüntüler ve sağlar. Arabirim koduna müdahale etti ve üzerinde eylemde bulundu.

- Kullanıcı komutuna tıkladığında, Yönlendirme algoritmasında özetlenen yordama [tabi olur.](../../extensibility/internals/command-routing-algorithm.md)

## <a name="call-pre-defined-commands"></a>Önceden tanımlanmış komutları çağırma
[UsedCommands öğesi,](../../extensibility/usedcommands-element.md) VSPackage'ların diğer VSPackage'lar veya IDE tarafından sağlanan komutlara erişmelerini sağlar. Bunu yapmak için kullanılacak komutun GUID ve kimliğine sahip bir [UsedCommand](../../extensibility/usedcommand-element.md) öğesi oluşturun. Bu, geçerli yapılandırmanın parçası Visual Studio bile komutun Visual Studio sağlar. Daha fazla bilgi için [bkz. UsedCommand öğesi.](../../extensibility/usedcommand-element.md)

## <a name="interface-element-appearance"></a>Arabirim öğesi görünümü
Komut öğelerini seçme ve konumlandırma ile ilgili dikkat edilmesi gerekenler şunlardır:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , yerleştirmeye bağlı olarak farklı görünen birçok kullanıcı arabirimi öğeleri sunar.

- bayrağı kullanılarak tanımlanan kullanıcı arabirimi öğesi, yöntemin VSPackage uygulaması tarafından görüntülenmediği veya bölümdeki belirli bir kullanıcı arabirimi bağlamıyla ilişkilendirildiği sürece `DefaultInvisible` IDE'de <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> `VisibilityConstraints` görüntülenmez.

- Başarıyla konumlara alınan bir komut bile görüntülenmez. Bunun nedeni, VSPackage'ın uygulanmış (veya uygulanmamış) arabirimlere bağlı olarak IDE'nin bazı komutları otomatik olarak gizlemesi veya görüntülemesidir. Örneğin, vsPackage'ın bazı derleme arabirimlerini uygulaması, derlemeyle ilgili menü öğelerinin otomatik olarak gösterilmeye neden olur.

- Bayrağın `CommandWellOnly` kullanıcı arabirimi öğesinin tanımına uygulanması, komutun yalnızca özelleştirmeyle eklen kullanılabilir olduğu anlamına gelir.

- Komutlar yalnızca belirli kullanıcı arabirimi bağlamlarında kullanılabilir, örneğin yalnızca IDE tasarım görünümündeyken bir iletişim kutusu görüntülendiğinde.

- Belirli kullanıcı arabirimi öğelerinin IDE'de görüntülenebilir olması için bir veya daha fazla arabirim uygulamalı veya kod yazmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md)
