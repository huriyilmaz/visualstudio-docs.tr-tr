---
title: Özgün. Vsct dosyaları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186659"
---
# <a name="author-vsct-files"></a>Author. vsct dosyaları
Bu belgede, Visual Studio tümleşik geliştirme ortamına (IDE) menü öğeleri, araç çubukları ve diğer kullanıcı arabirimi (UI) öğeleri eklemek için bir *. vsct* dosyasının nasıl yazılacağı gösterilmektedir. Zaten bir *. vsct* dosyası olmayan bir Visual Studio paketine (VSPackage) Kullanıcı arabirimi öğeleri eklediğinizde bu adımları kullanın.

 Yeni projelerde, seçimlerinize bağlı olarak bir menü komutu, bir araç penceresi veya özel bir düzenleyici için gereken öğelere zaten sahip olan bir *. vsct* dosyası oluşturduğundan, Visual Studio paket şablonunu kullanmanızı öneririz. VSPackage 'ın gereksinimlerini karşılamak için bu *. vsct* dosyasını değiştirebilirsiniz. *. Vsct* dosyasını değiştirme hakkında daha fazla bilgi için bkz. [genişletme menüleri ve komutları](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Dosyayı yazın
 Bu aşamalardan bir *. vsct* dosyası Yazar: dosyalar ve kaynaklar Için yapıyı oluşturun, UI öğelerini BILDIRIN, IDE 'ye Kullanıcı arabirimi öğelerini koyun ve tüm özel davranışları ekleyin.

### <a name="file-structure"></a>Dosya yapısı
 Bir *. vsct* dosyasının temel yapısı, bir [Commands](../../extensibility/commands-element.md) öğesi ve bir [Symbols](../../extensibility/symbols-element.md) öğesi içeren bir [CommandTable](../../extensibility/commandtable-element.md) kök öğesidir.

#### <a name="to-create-the-file-structure"></a>Dosya yapısını oluşturmak için

1. [Nasıl yapılır: bir. vsct dosyası oluşturma](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)bölümündeki adımları izleyerek projenize bir *. vsct* dosyası ekleyin.

2. Aşağıdaki örnekte gösterildiği gibi, gerekli ad alanlarını `CommandTable` öğesine ekleyin:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. `CommandTable` öğesinde, tüm özel menülerinizi, araç çubuklarınızı, komut gruplarınızı ve komutları barındırmak için bir `Commands` öğesi ekleyin. Özel UI öğelerinizin yüklenmesine izin vermek için `Commands` öğesi, `Package` özniteliğinin paketin adına ayarlanmış olması gerekir.

     `Commands` öğeden sonra, paket için GUID 'Leri ve Kullanıcı arabirimi öğelerinizin adlarını ve komut kimliklerini tanımlamak üzere bir `Symbols` öğesi ekleyin.

### <a name="include-visual-studio-resources"></a>Visual Studio kaynaklarını dahil et
 Visual Studio komutlarını ve Kullanıcı arabirimi öğelerinizi IDE 'ye koymak için gereken menüleri tanımlayan dosyalara erişmek için [extern](../../extensibility/extern-element.md) öğesini kullanın. Paketinizin dışında tanımlanan komutları kullanacaksanız, Visual Studio 'Yu bilgilendirmek için [UsedCommands](../../extensibility/usedcommands-element.md) öğesini kullanın.

#### <a name="to-include-visual-studio-resources"></a>Visual Studio kaynaklarını dahil etmek için

1. `CommandTable` öğesinin üst kısmında, başvurulacak her harici dosya için bir `Extern` öğesi ekleyin ve `href` özniteliğini dosyanın adı olarak ayarlayın. Visual Studio kaynaklarına erişmek için aşağıdaki üst bilgi dosyalarına başvurabilirsiniz:

   - *Stdidcmd. h*: Visual Studio tarafından kullanıma sunulan tüm komutların kimliklerini tanımlar.

   - *Vsshlıds. h*: Visual Studio menülerinin komut kimliklerini içerir.

2. Paketiniz Visual Studio veya diğer paketler tarafından tanımlanan komutları çağırırsa, `Commands` öğesinden sonra bir `UsedCommands` öğesi ekleyin. Bu öğeyi, paketinizin bir parçası olmayan çağırdığınız her komut için bir [UsedCommand](../../extensibility/usedcommand-element.md) öğesiyle doldurun. `UsedCommand` öğelerin `guid` ve `id` özniteliklerini çağrılacak komutların GUID ve ID değerleri olarak ayarlayın.

   Visual Studio komutlarının GUID 'Leri ve kimliklerini bulma hakkında daha fazla bilgi için bkz. [Visual Studio komutlarının GUID 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Diğer paketlerdeki komutları çağırmak için, bu paketler için *. vsct* dosyasında tanımlanan GUID ve komut kimliğini kullanın.

### <a name="declare-ui-elements"></a>UI öğelerini bildirin
 *. Vsct* dosyasının `Symbols` bölümünde tüm yeni kullanıcı arabirimi öğelerini bildirin.

#### <a name="to-declare-ui-elements"></a>UI öğelerini bildirmek için

1. `Symbols` öğesinde üç [GuidSymbol](../../extensibility/guidsymbol-element.md) öğesi ekleyin. Her `GuidSymbol` öğesi bir `name` özniteliğe ve bir `value` özniteliğine sahiptir. Öğesinin amacını yansıtması için `name` özniteliğini ayarlayın. `value` özniteliği bir GUID alır. (Bir GUID oluşturmak için, **Araçlar** menüsünde **GUID oluştur**' u seçin ve **kayıt defteri biçimi**' ni seçin.)

     İlk `GuidSymbol` öğesi paketinizi temsil eder ve genellikle alt öğeye sahip olmaz. İkinci `GuidSymbol` öğesi, komut kümesini temsil eder ve menülerinizi, gruplarınızı ve komutlarınızı tanımlayan bütün sembolleri içerir. Üçüncü `GuidSymbol` öğesi görüntü deponuzi temsil eder ve komutlarınız için tüm simgelere yönelik semboller içerir. Simgeler kullanan komutlarınız yoksa, üçüncü `GuidSymbol` öğesini atlayabilirsiniz.

2. Komut kümesini temsil eden `GuidSymbol` öğesinde bir veya daha fazla [IDSymbol](../../extensibility/idsymbol-element.md) öğesi ekleyin. Her biri, Kullanıcı arabirimine eklemekte olduğunuz bir menü, araç çubuğu, Grup veya komutu temsil eder.

     Her `IDSymbol` öğesi için, `name` özniteliğini ilgili menü, Grup veya komuta başvurmak için kullanacağınız ada ayarlayın ve ardından `value` öğesini komut KIMLIĞINI temsil edecek bir onaltılı sayı olarak ayarlayın. Aynı üst öğeye sahip iki `IDSymbol` öğesi aynı değere sahip olamaz.

3. Kullanıcı arabirimi öğelerinden herhangi biri simge gerektiriyorsa, görüntü deponuzu temsil eden `GuidSymbol` öğesine her simge için bir `IDSymbol` öğesi ekleyin.

### <a name="put-ui-elements-in-the-ide"></a>IDE 'ye UI öğeleri yerleştirme
 [Menüler](../../extensibility/menus-element.md), [gruplar](../../extensibility/groups-element.md)ve [düğmeler](../../extensibility/buttons-element.md) öğeleri, paketinizdeki tanımlı tüm menülere, gruplara ve komutlara ilişkin tanımları içerir. Bu menüleri, grupları ve komutları, UI öğesi tanımının bir parçası olan bir [üst](../../extensibility/parent-element.md) öğe kullanarak ya da başka bir yerde tanımlanmış bir [commandyerleştirme](../../extensibility/commandplacement-element.md) öğesi kullanarak, IDE 'ye yerleştirin.

 Her `Menu`, `Group`ve `Button` öğesinin bir `guid` özniteliği ve bir `id` özniteliği vardır. `guid` özniteliğini her zaman, komut grubunuzu temsil eden `GuidSymbol` öğesinin adıyla eşleşecek şekilde ayarlayın ve `id` özniteliğini `Symbols` bölümünde menü, Grup veya komutlarınızı temsil eden `IDSymbol` öğesinin adı olarak ayarlayın.

#### <a name="to-define-ui-elements"></a>UI öğelerini tanımlamak için

1. Yeni menüler, alt menüler, kısayol menüleri veya araç çubukları tanımlıyorsanız, `Commands` öğesine bir `Menus` öğesi ekleyin. Ardından, her bir menünün oluşturulması için `Menus` öğesine bir [menü](../../extensibility/menu-element.md) öğesi ekleyin.

    `Menu` öğesinin `guid` ve `id` özniteliklerini ayarlayın ve sonra `type` özniteliğini istediğiniz menü türü olarak ayarlayın. Ayrıca, üst gruptaki menünün göreli konumunu oluşturmak için `priority` özniteliğini de ayarlayabilirsiniz.

   > [!NOTE]
   > `priority` özniteliği, araç çubuklarına ve bağlam menülerine uygulanmaz.

2. Visual Studio IDE 'deki tüm komutlar, menülerin ve araç çubuklarının doğrudan alt öğeleri olan komut grupları tarafından barındırılmalıdır. IDE 'ye yeni menüler veya araç çubukları ekliyorsanız, bu yeni komut grupları içermelidir. Ayrıca komutlarınızı görsel olarak gruplandırabilmeniz için mevcut menülere ve araç çubuklarına komut grupları ekleyebilirsiniz.

    Yeni komut grupları eklediğinizde, önce bir `Groups` öğesi oluşturmanız ve ardından her bir komut grubu için bir [Grup](../../extensibility/group-element.md) öğesine eklemeniz gerekir.

    Her bir `Group` öğesinin `guid` ve `id` özniteliklerini ayarlayın ve sonra üst menüdeki grubun göreli konumunu oluşturmak için `priority` özniteliğini ayarlayın. Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).

3. IDE 'ye yeni komutlar ekliyorsanız, `Commands` öğesine bir `Buttons` öğesi ekleyin. Ardından, her komut için `Buttons` öğesine bir [Button](../../extensibility/button-element.md) öğesi ekleyin.

   1. Her bir `Button` öğesinin `guid` ve `id` özniteliklerini ayarlayın ve sonra `type` özniteliğini istediğiniz düğme türüne ayarlayın. Ayrıca, üst grupta komutun göreli konumunu oluşturmak için `priority` özniteliğini de ayarlayabilirsiniz.

       > [!NOTE]
       > Araç çubuklarındaki standart menü komutları ve düğmeleri için `type="button"` kullanın.

   2. `Button` öğesinde, bir [ButtonText](../../extensibility/buttontext-element.md) öğesi ve [CommandName](../../extensibility/commandname-element.md) öğesi içeren bir [dizeler](../../extensibility/strings-element.md) öğesi ekleyin. `ButtonText` öğesi, bir menü öğesi için metin etiketi veya bir araç çubuğu düğmesi için araç ipucu sağlar. `CommandName` öğesi komut kutusu içinde kullanılacak komutun adını sağlar.

   3. Komutunuz bir simgeye sahip olur, `Button` öğesinde bir [simge](../../extensibility/icon-element.md) öğesi oluşturun ve `guid` ve `id` özniteliklerini simgenin `Bitmap` öğesi olarak ayarlayın.

       > [!NOTE]
       > Araç çubuğu düğmelerinde simgeler olmalıdır.

   Daha fazla bilgi için bkz. [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Komutlarınız simge gerektiriyorsa, `Commands` öğesine bir [bit eşlem](../../extensibility/bitmaps-element.md) öğesi ekleyin. Ardından, her simge için `Bitmaps` öğesine bir [bit eşlem](../../extensibility/bitmap-element.md) öğesi ekleyin. Bu, bit eşlem kaynağının konumunu belirlediğiniz yerdir. Daha fazla bilgi için bkz. [menü komutlarına simgeler ekleme](../../extensibility/adding-icons-to-menu-commands.md).

   En fazla menü, Grup ve komutları doğru şekilde yerleştirmek için üst yapıya sahip olabilirsiniz. Çok büyük komut kümelerinde veya bir menü, Grup veya komutun birden çok yerde görünmesi gerektiğinde, komut yerleşimini belirtmenizi öneririz.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE 'ye UI öğeleri yerleştirmek için üst öğeye güvenme

1. Tipik üst öğe için, paketinizdeki tanımlı her bir `Menu`, `Group`ve `Command` öğesi `Parent` bir öğe oluşturun.

    `Parent` öğesinin hedefi menü, Grup veya komutu içerecek olan menü ya da gruptur.

   1. `guid` özniteliğini, komut kümesini tanımlayan `GuidSymbol` öğesinin adı olarak ayarlayın. Hedef öğe paketinizin bir parçası değilse, ilgili *. vsct* dosyasında tanımlandığı şekilde, bu komut kümesi için GUID kullanın.

   2. `id` özniteliğini hedef menünün veya grubun `id` özniteliğiyle eşleşecek şekilde ayarlayın. Visual Studio tarafından sunulan menülerin ve grupların listesi için bkz. Visual [Studio menülerinin GUID 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) , [Visual Studio araç çubuklarının GUID 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   IDE 'ye yerleştirilecek çok sayıda UI öğesi varsa veya birden fazla yerde görünmesi gereken öğeleriniz varsa, aşağıdaki adımlarda gösterildiği gibi, bu öğelerin konumlarını [CommandPlacements](../../extensibility/commandplacements-element.md) öğesinde tanımlayın.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>IDE 'ye UI öğeleri yerleştirmek için komut yerleşimini kullanmak için

1. `Commands` öğeden sonra bir `CommandPlacements` öğesi ekleyin.

2. `CommandPlacements` öğesinde, her menü, Grup veya komutun yerleştirileceği bir `CommandPlacement` öğesi ekleyin.

    Her `CommandPlacement` öğesi veya `Parent` öğesi bir IDE konumunda bir menü, Grup veya komut koyar. UI öğesi yalnızca bir üst öğeye sahip olabilir, ancak birden fazla komut yerleşimi olabilir. Birden çok konuma bir UI öğesi yerleştirmek için, her konum için bir `CommandPlacement` öğesi ekleyin.

3. Her bir `CommandPlacement` öğesinin `guid` ve `id` özniteliklerini, tıpkı bir `Parent` öğesi gibi barındıran menü veya grup olarak ayarlayın. Ayrıca, Kullanıcı arabirimi öğesinin göreli konumunu oluşturmak için `priority` özniteliğini de ayarlayabilirsiniz.

   Yerleşimi, olma ve komut yerleşimi ile karıştırabilirsiniz. Ancak, çok büyük komut kümeleri için yalnızca komut yerleşimini kullanmanızı öneririz.

### <a name="add-specialized-behaviors"></a>Özel davranışlar ekleyin
 Menü ve komutların davranışını değiştirmek, örneğin görünüşünü ve görünürlüğünü değiştirmek için [CommandFlag](../../extensibility/command-flag-element.md) öğesini kullanabilirsiniz. Ayrıca, [Visibilitykısıtlamalar](../../extensibility/visibilityconstraints-element.md) öğesini kullanarak bir komutun ne zaman görünür olduğunu veya [keybindings](../../extensibility/keybindings-element.md) öğesini kullanarak klavye kısayolları eklemeyi de etkileyebilirsiniz. Bazı menü ve komut türleri, içinde yerleşik olan özel davranışları zaten vardır.

#### <a name="to-add-specialized-behaviors"></a>Özel davranışlar eklemek için

1. Bir UI öğesini yalnızca belirli kullanıcı arabirimi bağlamlarında görünür hale getirmek için örneğin, bir çözüm yüklendiğinde görünürlük kısıtlamalarını kullanın.

   1. `Commands` öğeden sonra bir `VisibilityConstraints` öğesi ekleyin.

   2. Kısıtlamak için her kullanıcı arabirimi öğesi için bir [VisibilityItem](../../extensibility/visibilityitem-element.md) öğesi ekleyin.

   3. Her `VisibilityItem` öğesi için, `guid` ve `id` özniteliklerini menü, Grup veya komutla ayarlayın ve ardından `context` özniteliğini <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> sınıfında tanımlandığı şekilde istediğiniz kullanıcı arabirimi bağlamına ayarlayın.

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

5. Menüye veya menüdeki bir öğeye menü bağımlı klavye kısayolu eklemek için, menü ya da menü öğesi için `ButtonText` öğesinde bir ampersan (&) ekleyin. Ve işaretini izleyen karakter, üst menü açık olduğunda etkin klavye kısayoludur.

6. Bir komuta menü bağımsız klavye kısayolu eklemek için, [keybindings](../../extensibility/keybindings-element.md) öğesini kullanın. Daha fazla bilgi için bkz. [KeyBinding](../../extensibility/keybinding-element.md) öğesi.

7. Menü metnini yerelleştirmek için `LocCanonicalName` öğesini kullanın. Daha fazla bilgi için bkz. [dizeler](../../extensibility/strings-element.md) öğesi.

   Bazı menü ve düğme türleri özel davranışları içerir. Aşağıdaki listede bazı özel menü ve düğme türleri açıklanmaktadır. Diğer türler için, [menü](../../extensibility/menu-element.md), [düğme](../../extensibility/button-element.md)ve [Birleşik](../../extensibility/combo-element.md) öğeler içindeki `types` özniteliği açıklamalarını inceleyin.

   - Birleşik giriş kutusu: bir açılan kutu, bir araç çubuğunda kullanılabilen bir açılan listesidir. Kullanıcı arabirimine Birleşik giriş kutuları eklemek için `Commands` öğesinde bir [combos](../../extensibility/combos-element.md) öğesi oluşturun. Sonra eklenecek her Birleşik giriş kutusu için bir `Combo` öğesi `Combos` öğesine ekleyin. `Combo` öğeler `Button` öğeleriyle aynı özniteliklere ve alt öğelere sahiptir ve ayrıca `DefaultWidth` ve `idCommandList` özniteliklerine sahiptir. `DefaultWidth` özniteliği piksel cinsinden genişliği ayarlar ve `idCommandList` özniteliği Birleşik giriş kutusunu doldurmak için kullanılan bir komut KIMLIĞINI gösterir.

   - Menü denetleyicisi: menü denetleyicisi, yanında bir ok olan bir düğmedir. Oka tıkladığınızda bir liste açılır. Kullanıcı arabirimine bir menü denetleyicisi eklemek için bir `Menu` öğesi oluşturun ve `type` özniteliğini istediğiniz davranışa göre `MenuController` veya `MenuControllerLatched`olarak ayarlayın. Bir menü denetleyicisini doldurmak için, bir `Group` öğesinin üst öğesi olarak ayarlayın. Menü denetleyicisi açılan listesinde bu grubun tüm alt öğelerini görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları Genişlet](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)