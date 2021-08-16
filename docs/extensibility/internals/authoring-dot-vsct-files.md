---
title: Yazma. Vsct Dosyaları | Microsoft Docs
description: Tümleşik geliştirme ortamına (IDE) menü öğeleri, araç çubukları ve diğer kullanıcı arabirimi öğeleri Visual Studio .vsct dosyaları yazmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 44b8dff74a15434e91e55efa37454a0827447f76a936f35ec7aafb54c7840f54
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432624"
---
# <a name="author-vsct-files"></a>.vsct dosyaları yazma
Bu belgede, tümleşik geliştirme ortamına (IDE) menü öğeleri, araç çubukları ve diğer kullanıcı arabirimi (UI) öğeleri eklemek için bir *.vsct* Visual Studio nasıl yazılmalıdır? Kullanıcı arabirimi öğelerini zaten *bir .vsct* dosyası Visual Studio bir pakete (VSPackage) eklerken bu adımları kullanın.

 Yeni projeler için, seçimlerinizi bağlı olarak bir menü komutu, araç penceresi veya özel bir düzenleyici için gerekli öğeleri zaten içeren *bir .vsct* dosyası oluşturması nedeniyle Visual Studio paket şablonunu kullanmanızı öneririz. Bu *.vsct dosyasını* VSPackage'nizin gereksinimlerini karşılayacak şekilde değiştirebilirsiniz. Bir *.vsct* dosyasını değiştirme hakkında daha fazla bilgi için Menüleri ve komutları [genişletme'de yer alan örneklere bakın.](../../extensibility/extending-menus-and-commands.md)

## <a name="author-the-file"></a>Dosyayı yazma
 Şu *aşamalarda bir .vsct* dosyası yazma: Dosyalar ve kaynaklar için yapı oluşturun, kullanıcı arabirimi öğelerini bildirin, KULLANıCı arabirimi öğelerini IDE'ye ekleyin ve özel davranışları ekleyin.

### <a name="file-structure"></a>Dosya yapısı
 *.vsct* dosyasının temel yapısı, Commands öğesini ve Symbols öğesini içeren [bir](../../extensibility/commands-element.md) [CommandTable](../../extensibility/commandtable-element.md) kök [öğesidir.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Dosya yapısını oluşturmak için

1. Projenize *bir .vsct* dosyası eklemek için Nasıl: [.vsct dosyası oluşturma adımlarını izleyin.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

2. Aşağıdaki örnekte gösterildiği gibi `CommandTable` gerekli ad alanlarını öğesine ekleyin:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. `CommandTable`öğesinde, tüm özel `Commands` menülerinizi, araç çubuklarınızı, komut gruplarınızı ve komutlarınızı barındırmak için bir öğesi ekleyin. Özel kullanıcı arabirimi öğelerinizin yüklenemediklerine göre, öğenin `Commands` `Package` özniteliği paketin adına ayarlanmış olması gerekir.

     öğesi `Commands` sonrasında, paketin GUID'lerini ve kullanıcı arabirimi öğelerinizin adlarını ve `Symbols` komut kimliklerini tanımlamak için bir öğesi ekleyin.

### <a name="include-visual-studio-resources"></a>Kaynak Visual Studio dahil
 Kullanıcı arabirimi öğelerinizi IDE'ye koymak için gereken Visual Studio ve menüleri tanımlayan dosyalara erişmek için [Extern](../../extensibility/extern-element.md) öğesini kullanın. Paketinizin dışında tanımlanan komutları kullanırsanız, kullanıcılarınızı bilgilendirmek için [UsedCommands](../../extensibility/usedcommands-element.md) Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Kaynak eklemek Visual Studio için

1. Öğesinin en üstüne, başvurul olacak her dış dosya için bir öğe ekleyin ve `CommandTable` `Extern` `href` özniteliğini dosyanın adına ayarlayın. Veri kaynaklarına erişmek için aşağıdaki üst bilgi Visual Studio başvurabilirsiniz:

   - *Stdidcmd.h:* Uygulama tarafından açığa çıkarlan tüm komutlar için Visual Studio.

   - *Vsshlids.h:* Menüler için komut Visual Studio içerir.

2. Paketiniz, uygulama tarafından veya diğer paketler Visual Studio herhangi bir komutu çağırıyorsa, `UsedCommands` öğesin sonra bir öğesi `Commands` ekleyin. Bu öğeyi, çağıran ve paketinizin parçası olan her komut için bir [UsedCommand](../../extensibility/usedcommand-element.md) öğesiyle doldurmak. Öğelerin `guid` ve `id` özniteliklerini, `UsedCommand` çağrılma komutların GUID ve kimlik değerlerine ayarlayın.

   Komut komutlarının GUID'lerini ve kimliklerini bulma hakkında daha fazla Visual Studio için bkz. komutlarının [GUID'Visual Studio.](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md) Diğer paketlerden komutları çağırarak, bu paketler için *.vsct* dosyasında tanımlandığı gibi komutun GUID ve kimliğini kullanın.

### <a name="declare-ui-elements"></a>Kullanıcı arabirimi öğelerini bildir
 .vsct dosyasının bölümünde `Symbols` tüm yeni kullanıcı arabirimi *öğelerini* bildirebilirsiniz.

#### <a name="to-declare-ui-elements"></a>Kullanıcı arabirimi öğelerini bildir

1. öğesine `Symbols` üç [GuidSymbol öğesi](../../extensibility/guidsymbol-element.md) ekleyin. Her `GuidSymbol` öğenin bir `name` özniteliği ve bir özniteliği `value` vardır. `name`özniteliğini, öğesinin amacını yansıtacak şekilde ayarlayın. özniteliği `value` bir GUID alır. (GUID oluşturmak için Araçlar  menüsünde GUID Oluştur'a ve **ardından** Kayıt Defteri **Biçimi'ni seçin.)**

     İlk öğe `GuidSymbol` paketinizi temsil eder ve genellikle alt öğesi yoktur. İkinci öğe `GuidSymbol` komut kümenizi temsil eder ve menülerinizi, gruplarınızı ve komutlarınızı tanımlayan tüm sembolleri içerir. Üçüncü öğe `GuidSymbol` görüntü deponızı temsil eder ve komutlarınız için tüm simgelerin sembollerini içerir. Simgeler kullanan bir komut yoksa üçüncü öğeyi `GuidSymbol` atabilirsiniz.

2. Komut `GuidSymbol` kümenizi temsil eden öğeye bir veya daha fazla [IDSymbol öğesi](../../extensibility/idsymbol-element.md) ekleyin. Bunların her biri kullanıcı arabirimine eklemekte olduğunuz menü, araç çubuğu, grup veya komutu temsil ediyor.

     Her öğe için özniteliğini ilgili menüye, gruba veya komuta başvurmak için kullanmak üzere ad olarak ayarlayın ve ardından öğesini komut kimliğini temsil edecek onaltılık bir `IDSymbol` `name` `value` sayıya ayarlayın. Aynı `IDSymbol` üst öğeye sahip iki öğe aynı değere sahip olmaz.

3. Kullanıcı arabirimi öğelerinizin herhangi biri simge gerektirirse, görüntü depolarınızı temsil eden öğeye `IDSymbol` her simge için bir öğe `GuidSymbol` ekleyin.

### <a name="put-ui-elements-in-the-ide"></a>Kullanıcı arabirimi öğelerini IDE'ye koyma
 [Menüler,](../../extensibility/menus-element.md) [Gruplar](../../extensibility/groups-element.md)ve [Düğmeler](../../extensibility/buttons-element.md) öğeleri, paketiniz içinde tanımlanan tüm menülerin, grupların ve komutların tanımlarını içerir. Bu menüleri, grupları ve komutları IDE'ye ui öğesi tanımının parçası olan [bir Parent](../../extensibility/parent-element.md) öğesi veya başka bir yerde tanımlanan [CommandPlacement](../../extensibility/commandplacement-element.md) öğesi kullanarak koyabilirsiniz.

 Her `Menu` , `Group` ve `Button` öğesinin bir özniteliği ve bir özniteliği `guid` `id` vardır. Özniteliği her zaman komut kümenizi temsil eden öğenin adıyla eşecek şekilde ayarlayın ve özniteliğini bölümünde menü, grup veya komutu temsil eden öğenin adına `guid` `GuidSymbol` `id` `IDSymbol` `Symbols` ayarlayın.

#### <a name="to-define-ui-elements"></a>Kullanıcı arabirimi öğelerini tanımlamak için

1. Yeni menüler, alt menüler, kısayol menüleri veya araç çubukları tanımıyorsanız `Menus` öğeye bir öğe `Commands` ekleyin. Ardından, oluşturulacak her menü için öğesine [bir Menü](../../extensibility/menu-element.md) öğesi `Menus` ekleyin.

    öğesinin `guid` `id` ve özniteliklerini `Menu` ayarlayın ve ardından `type` özniteliğini istediğiniz menüye ayarlayın. Ayrıca, üst `priority` grupta menenin göreli konumunu kurmak için özniteliğini de ayarlayabilirsiniz.

   > [!NOTE]
   > özniteliği, `priority` araç çubukları ve bağlam menüleri için geçerli değildir.

2. IDE'Visual Studio komutlar, menülerin ve araç çubuklarının doğrudan öğeleri olan komut grupları tarafından barındırıldı. IDE'ye yeni menüler veya araç çubukları ekliyorsanız, bunların yeni komut grupları içermesi gerekir. Komutlarınızı görsel olarak gruplandırabilirsiniz.

    Yeni komut grupları eklerken önce bir öğe oluşturmanız ve ardından buna `Groups` her komut grubu için bir [Grup](../../extensibility/group-element.md) öğesi eklemeniz gerekir.

    Her `guid` öğenin ve özniteliklerini ayarlayın ve ardından üst menüde grubun göreli konumunu `id` kurmak için `Group` `priority` özniteliğini ayarlayın. Daha fazla bilgi için [bkz. Yeniden kullanılabilir düğme grupları oluşturma.](../../extensibility/creating-reusable-groups-of-buttons.md)

3. IDE'ye yeni komutlar ekliyorsanız öğesine `Buttons` bir öğesi `Commands` ekleyin. Ardından, her komut için öğesine [bir Button](../../extensibility/button-element.md) öğesi `Buttons` ekleyin.

   1. Her `guid` `id` öğenin ve `Button` özniteliklerini ayarlayın ve ardından `type` özniteliğini istediğiniz düğmenin türe ayarlayın. Ayrıca, üst `priority` grupta komutun göreli konumunu kurmak için özniteliğini de ayarlayabilirsiniz.

       > [!NOTE]
       > Araç `type="button"` çubuklarında standart menü komutları ve düğmeler için kullanın.

   2. öğesine `Button` ButtonText [öğesi ve CommandName](../../extensibility/strings-element.md) öğesi [içeren bir](../../extensibility/buttontext-element.md) Strings [öğesi](../../extensibility/commandname-element.md) ekleyin. öğesi, `ButtonText` bir menü öğesinin metin etiketini veya araç çubuğu düğmesinin araç ipucu'nu sağlar. `CommandName`öğesi, komut içinde kullanmak üzere komutun adını sağlar.

   3. Komutunuz bir simgeye sahipse, öğesinde [bir Icon](../../extensibility/icon-element.md) öğesi oluşturun ve ve özniteliklerini `Button` `guid` `id` `Bitmap` simgenin öğesine ayarlayın.

       > [!NOTE]
       > Araç çubuğu düğmelerinin simgeleri olması gerekir.

   Daha fazla bilgi için bkz. [MenuCommands ile OleMenuCommands karşılaştırması.](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015)

4. Komutlardan herhangi biri simge gerektirirse, öğesine [bir Bit](../../extensibility/bitmaps-element.md) Eşlemler öğesi `Commands` ekleyin. Ardından, her simge için öğesine [bir Bitmap](../../extensibility/bitmap-element.md) öğesi `Bitmaps` ekleyin. Bit eşlem kaynağının konumunu burada belirtirsiniz. Daha fazla bilgi için [bkz. Menü komutlarına simge ekleme.](../../extensibility/adding-icons-to-menu-commands.md)

   Menülerin, grupların ve komutların çoğunu doğru şekilde yer alan üst öğe yapısına güvenebilirsiniz. Çok büyük komut kümeleri için veya bir menü, grup veya komutun birden çok yerde görünmesi gerekende, komut yerleşimini belirtmenizi öneririz.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Kullanıcı arabirimi öğelerini IDE'ye yer alan üst öğeye güvenmek için

1. Tipik üst öğe için, `Parent` paketinde tanımlanan `Menu` her , ve `Group` `Command` öğesinde bir öğesi oluşturun.

    Öğenin hedefi `Parent` menü, grup veya komutu içeren menü veya grupdur.

   1. `guid`özniteliğini, komut kümesi `GuidSymbol` tanımlayan öğenin adına ayarlayın. Hedef öğe paketinizin parçası yoksa, ilgili *.vsct* dosyasında tanımlandığı gibi bu komut kümesi için guid kullanın.

   2. özniteliğini `id` hedef menü veya grubun `id` özniteliğiyle eş olacak şekilde ayarlayın. Visual Studio tarafından ortaya çıkaran menülerin ve grupların listesi için bkz. Visual Studio menülerinin [GUID'leri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ve kimlikleri ya da araç [çubuklarının GUID'Visual Studio kimlikleri.](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

   IDE'ye yerleştirmesi gereken çok sayıda kullanıcı arabirimi öğesiniz varsa veya birden çok yerde görünmesi gereken öğeleri varsa, bunların yerleşimlerini aşağıdaki adımlarda gösterildiği gibi [CommandPlacements](../../extensibility/commandplacements-element.md) öğesinde tanımlayın.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>IDE'ye kullanıcı arabirimi öğelerini yerleştirmeye komut yerleştirmeyi kullanmak için

1. `Commands` öğesinden sonra `CommandPlacements` öğesini ekleyin.

2. öğesine, `CommandPlacements` her `CommandPlacement` menü, grup veya komutun yer aç olduğu bir öğe ekleyin.

    Her `CommandPlacement` öğe veya öğe tek bir `Parent` IDE konuma bir menü, grup veya komut ayarlar. Kullanıcı arabirimi öğesinin yalnızca bir üst öğesi olabilir, ancak birden çok komut yerleştirmesi olabilir. Bir kullanıcı arabirimi öğesini birden çok konuma eklemek için her konum `CommandPlacement` için bir öğe ekleyin.

3. Bir `guid` öğe `id` için olduğu `CommandPlacement` gibi, her öğenin ve özniteliklerini barındırma menüsüne veya grubuna `Parent` ayarlayın. Kullanıcı arabirimi öğesinin `priority` göreli konumunu kurmak için özniteliğini de ayarlayın.

   Üst öğe ve komut yerleştirmeye göre yerleştirmeyi karıştırabilirsiniz. Ancak, çok büyük komut kümeleri için yalnızca komut yerleştirmeyi kullanmanız önerilir.

### <a name="add-specialized-behaviors"></a>Özel davranışlar ekleyin
 Menü ve komutların davranışını değiştirmek, örneğin görünüşünü ve görünürlüğünü değiştirmek için [CommandFlag](../../extensibility/command-flag-element.md) öğesini kullanabilirsiniz. Ayrıca, [Visibilitykısıtlamalar](../../extensibility/visibilityconstraints-element.md) öğesini kullanarak bir komutun ne zaman görünür olduğunu veya [keybindings](../../extensibility/keybindings-element.md) öğesini kullanarak klavye kısayolları eklemeyi de etkileyebilirsiniz. Bazı menü ve komut türleri, içinde yerleşik olan özel davranışları zaten vardır.

#### <a name="to-add-specialized-behaviors"></a>Özel davranışlar eklemek için

1. Bir UI öğesini yalnızca belirli kullanıcı arabirimi bağlamlarında görünür hale getirmek için örneğin, bir çözüm yüklendiğinde görünürlük kısıtlamalarını kullanın.

   1. `Commands` öğesinden sonra `VisibilityConstraints` öğesini ekleyin.

   2. Kısıtlamak için her kullanıcı arabirimi öğesi için bir [VisibilityItem](../../extensibility/visibilityitem-element.md) öğesi ekleyin.

   3. Her öğe için, `VisibilityItem` `guid` ve `id` özniteliklerini menü, Grup veya komuta ayarlayın ve ardından `context` özniteliği, sınıfında tanımlandığı şekilde istediğiniz kullanıcı arabirimi bağlamına ayarlayın <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> .

2. Koddaki bir kullanıcı arabirimi öğesinin görünürlüğünü veya kullanılabilirliğini ayarlamak için aşağıdaki komut bayraklarını bir veya daha fazla kullanın:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Daha fazla bilgi için bkz. [CommandFlag](../../extensibility/command-flag-element.md) öğesi.

3. Bir öğenin nasıl göründüğünü değiştirmek veya görünümünü dinamik olarak değiştirmek için aşağıdaki komut bayraklarını bir veya daha fazlasını kullanın:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Daha fazla bilgi için bkz. [CommandFlag](../../extensibility/command-flag-element.md) öğesi.

4. Bir öğenin komutları aldığında nasıl yeniden çalıştığını değiştirmek için, aşağıdaki komut bayraklarını bir veya daha fazlasını kullanın:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Daha fazla bilgi için bkz. [CommandFlag](../../extensibility/command-flag-element.md) öğesi.

5. Menüye veya menüdeki bir öğeye menü bağımlı klavye kısayolu eklemek için, `ButtonText` menü veya menü öğesi için öğesine bir ampersan karakteri (&) ekleyin. Ve işaretini izleyen karakter, üst menü açık olduğunda etkin klavye kısayoludur.

6. Bir komuta menü bağımsız klavye kısayolu eklemek için, [keybindings](../../extensibility/keybindings-element.md) öğesini kullanın. Daha fazla bilgi için bkz. [KeyBinding](../../extensibility/keybinding-element.md) öğesi.

7. Menü metnini yerelleştirmek için öğesini kullanın `LocCanonicalName` . Daha fazla bilgi için bkz. [dizeler](../../extensibility/strings-element.md) öğesi.

   Bazı menü ve düğme türleri özel davranışları içerir. Aşağıdaki listede bazı özel menü ve düğme türleri açıklanmaktadır. Diğer türler için, `types` [menü](../../extensibility/menu-element.md), [düğme](../../extensibility/button-element.md)ve [Birleşik](../../extensibility/combo-element.md) öğeler öğelerinin öznitelik açıklamalarını inceleyin.

   - Birleşik giriş kutusu: bir açılan kutu, bir araç çubuğunda kullanılabilen bir açılan listesidir. Kullanıcı arabirimine Birleşik giriş kutuları eklemek için, öğesinde bir [combos](../../extensibility/combos-element.md) öğesi oluşturun `Commands` . Sonra `Combos` `Combo` eklenecek her Birleşik giriş kutusu için öğesi öğesine ekleyin. `Combo` öğeler, öğelerle aynı özniteliklere ve alt öğelere sahiptir `Button` ve ayrıca `DefaultWidth` ve özniteliklerini de vardır `idCommandList` . `DefaultWidth`Özniteliği piksel cinsinden genişliği ayarlar ve `idCommandList` öznitelik, Birleşik giriş kutusunu doldurmak için kullanılan BIR komut kimliğini gösterir.

   - Menü denetleyicisi: menü denetleyicisi, yanında bir ok olan bir düğmedir. Oka tıkladığınızda bir liste açılır. Kullanıcı arabirimine bir menü denetleyicisi eklemek için bir `Menu` öğe oluşturun ve `type` özniteliğini istediğiniz `MenuController` davranışa göre veya olarak ayarlayın `MenuControllerLatched` . Bir menü denetleyicisini doldurmak için, onu bir öğesinin üst öğesi olarak ayarlayın `Group` . Menü denetleyicisi açılan listesinde bu grubun tüm alt öğelerini görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları Genişlet](../../extensibility/extending-menus-and-commands.md)
- [komut tablosu (. vsct) dosyaları Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)