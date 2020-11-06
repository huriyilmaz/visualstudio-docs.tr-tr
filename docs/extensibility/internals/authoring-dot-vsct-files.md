---
title: Özgün. Vsct dosyaları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54e67a28d59cb739abbeab188ff1f100751f2aa8
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413922"
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

2. `CommandTable`Aşağıdaki örnekte gösterildiği gibi, gerekli ad alanlarını öğesine ekleyin:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Öğesinde, `CommandTable` `Commands` tüm özel menülerinizi, araç çubuklarınızı, komut gruplarınızı ve komutları barındırmak için bir öğe ekleyin. Özel UI öğelerinizin yüklenmesine `Commands` `Package` izin vermek için, öğesinin özniteliği paketin adına ayarlanmış olmalıdır.

     Öğesinden sonra `Commands` , `Symbols` paket Için GUID 'leri ve Kullanıcı arabirimi öğelerinizin adlarını ve komut kimliklerini tanımlayacak bir öğe ekleyin.

### <a name="include-visual-studio-resources"></a>Visual Studio kaynaklarını dahil et
 Visual Studio komutlarını ve Kullanıcı arabirimi öğelerinizi IDE 'ye koymak için gereken menüleri tanımlayan dosyalara erişmek için [extern](../../extensibility/extern-element.md) öğesini kullanın. Paketinizin dışında tanımlanan komutları kullanacaksanız, Visual Studio 'Yu bilgilendirmek için [UsedCommands](../../extensibility/usedcommands-element.md) öğesini kullanın.

#### <a name="to-include-visual-studio-resources"></a>Visual Studio kaynaklarını dahil etmek için

1. Öğesinin üst kısmında `CommandTable` , `Extern` başvurulacak her harici dosya için bir öğe ekleyin ve `href` özniteliği dosyanın adı olarak ayarlayın. Visual Studio kaynaklarına erişmek için aşağıdaki üst bilgi dosyalarına başvurabilirsiniz:

   - *Stdidcmd. h* : Visual Studio tarafından kullanıma sunulan tüm komutların kimliklerini tanımlar.

   - *Vsshlıds. h* : Visual Studio menülerinin komut kimliklerini içerir.

2. Paketiniz Visual Studio veya diğer paketler tarafından tanımlanan komutları çağırırsa, `UsedCommands` öğesinden sonra bir öğe ekleyin `Commands` . Bu öğeyi, paketinizin bir parçası olmayan çağırdığınız her komut için bir [UsedCommand](../../extensibility/usedcommand-element.md) öğesiyle doldurun. `guid` `id` Öğelerinin ve özniteliklerini, `UsedCommand` çağrılacak KOMUTLARıN GUID ve ID değerleriyle ayarlayın.

   Visual Studio komutlarının GUID 'Leri ve kimliklerini bulma hakkında daha fazla bilgi için bkz. [Visual Studio komutlarının GUID 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Diğer paketlerdeki komutları çağırmak için, bu paketler için *. vsct* dosyasında tanımlanan GUID ve komut kimliğini kullanın.

### <a name="declare-ui-elements"></a>UI öğelerini bildirin
 `Symbols` *. Vsct* dosyasının bölümündeki tüm yeni kullanıcı arabirimi öğelerini bildirin.

#### <a name="to-declare-ui-elements"></a>UI öğelerini bildirmek için

1. `Symbols`Öğesinde, üç [GuidSymbol](../../extensibility/guidsymbol-element.md) öğesi ekleyin. Her `GuidSymbol` öğenin bir `name` özniteliği ve özniteliği vardır `value` . `name`Özniteliğini öğenin amacını yansıtacak şekilde ayarlayın. `value`Öznitelik BIR GUID alır. (Bir GUID oluşturmak için, **Araçlar** menüsünde **GUID oluştur** ' u seçin ve **kayıt defteri biçimi** ' ni seçin.)

     İlk `GuidSymbol` öğe paketinizi temsil eder ve genellikle alt öğeye sahip olmaz. İkinci `GuidSymbol` öğe, komut kümesini temsil eder ve menülerinizi, gruplarınızı ve komutlarınızı tanımlayan bütün sembolleri içerir. Üçüncü `GuidSymbol` öğe, görüntü deponuzi temsil eder ve komutlarınız için tüm simgelere yönelik semboller içerir. Simgeler kullanan komutlarınız yoksa, üçüncü `GuidSymbol` öğeyi atlayabilirsiniz.

2. `GuidSymbol`Komut kümesini temsil eden öğede bir veya daha fazla [IDSymbol](../../extensibility/idsymbol-element.md) öğesi ekleyin. Her biri, Kullanıcı arabirimine eklemekte olduğunuz bir menü, araç çubuğu, Grup veya komutu temsil eder.

     Her `IDSymbol` öğe için, `name` özniteliğini ilgili menü, Grup veya komuta başvurmak için kullanacağınız ada ayarlayın ve ardından `value` ÖĞESINI, komut kimliğini temsil edecek bir onaltılı sayı olarak ayarlayın. `IDSymbol`Aynı üst öğeye sahip iki öğe aynı değere sahip olamaz.

3. Kullanıcı arabirimi öğelerinden herhangi biri simge gerektiriyorsa, `IDSymbol` `GuidSymbol` görüntü deponuzu temsil eden öğeye her bir simge için bir öğe ekleyin.

### <a name="put-ui-elements-in-the-ide"></a>IDE 'ye UI öğeleri yerleştirme
 [Menüler](../../extensibility/menus-element.md), [gruplar](../../extensibility/groups-element.md)ve [düğmeler](../../extensibility/buttons-element.md) öğeleri, paketinizdeki tanımlı tüm menülere, gruplara ve komutlara ilişkin tanımları içerir. Bu menüleri, grupları ve komutları, UI öğesi tanımının bir parçası olan bir [üst](../../extensibility/parent-element.md) öğe kullanarak ya da başka bir yerde tanımlanmış bir [commandyerleştirme](../../extensibility/commandplacement-element.md) öğesi kullanarak, IDE 'ye yerleştirin.

 Her `Menu` , `Group` ve `Button` öğesi bir `guid` özniteliğe ve bir özniteliğe sahiptir `id` . Özniteliğini her zaman, `guid` `GuidSymbol` komut grubunuzu temsil eden öğenin adıyla eşleşecek şekilde ayarlayın ve `id` özniteliği, `IDSymbol` bölümünde menü, Grup veya komutu temsil eden öğenin adına ayarlayın `Symbols` .

#### <a name="to-define-ui-elements"></a>UI öğelerini tanımlamak için

1. Yeni menüler, alt menüler, kısayol menüleri veya araç çubukları tanımlıyorsanız, `Menus` öğeye bir öğe ekleyin `Commands` . Ardından, her bir menünün oluşturulması için öğesine bir [menü](../../extensibility/menu-element.md) öğesi ekleyin `Menus` .

    `guid` `id` Öğesinin ve özniteliklerini ayarlayın `Menu` ve ardından `type` özniteliği istediğiniz menü türü olarak ayarlayın. Ayrıca, `priority` üst gruptaki menünün göreli konumunu oluşturmak için özniteliğini de ayarlayabilirsiniz.

   > [!NOTE]
   > `priority`Öznitelik, araç çubuklarına ve bağlam menülerine uygulanmaz.

2. Visual Studio IDE 'deki tüm komutlar, menülerin ve araç çubuklarının doğrudan alt öğeleri olan komut grupları tarafından barındırılmalıdır. IDE 'ye yeni menüler veya araç çubukları ekliyorsanız, bu yeni komut grupları içermelidir. Ayrıca komutlarınızı görsel olarak gruplandırabilmeniz için mevcut menülere ve araç çubuklarına komut grupları ekleyebilirsiniz.

    Yeni komut grupları eklediğinizde, önce bir `Groups` öğesi oluşturmanız ve ardından her bir komut grubu için bir [Grup](../../extensibility/group-element.md) öğesine eklemeniz gerekir.

    `guid` `id` Her öğenin ve özniteliklerini ayarlayın `Group` ve sonra `priority` üst menüdeki grubun göreli konumunu oluşturmak için özniteliğini ayarlayın. Daha fazla bilgi için bkz. yeniden [kullanılabilir düğme grupları oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).

3. IDE 'ye yeni komutlar ekliyorsanız, öğesine bir `Buttons` öğesi ekleyin `Commands` . Ardından, her komut için öğesine bir [Button](../../extensibility/button-element.md) öğesi ekleyin `Buttons` .

   1. `guid` `id` Her öğenin ve özniteliklerini ayarlayın `Button` ve ardından `type` özniteliği istediğiniz düğme türüne ayarlayın. Ayrıca, `priority` üst grupta komutun göreli konumunu oluşturmak için özniteliğini de ayarlayabilirsiniz.

       > [!NOTE]
       > `type="button"`Araç çubuklarındaki standart menü komutları ve düğmeleri için kullanın.

   2. `Button`Öğesinde, bir [ButtonText](../../extensibility/buttontext-element.md) öğesi ve [CommandName](../../extensibility/commandname-element.md) öğesi içeren bir [dizeler](../../extensibility/strings-element.md) öğesi ekleyin. `ButtonText`Öğesi, bir menü öğesi için metin etiketi veya bir araç çubuğu düğmesi için araç ipucu sağlar. `CommandName`Öğesi komut kutusu içinde kullanılacak komutun adını sağlar.

   3. Komutunuz bir simgeye sahip olur, öğesinde bir [simge](../../extensibility/icon-element.md) öğesi oluşturun `Button` ve `guid` ve `id` özniteliklerini `Bitmap` simgenin öğesi olarak ayarlayın.

       > [!NOTE]
       > Araç çubuğu düğmelerinde simgeler olmalıdır.

   Daha fazla bilgi için bkz. [MenuCommands vs. OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

4. Komutlarınızın herhangi biri simge gerektiriyorsa, öğeye bir [bit eşlem](../../extensibility/bitmaps-element.md) öğesi ekleyin `Commands` . Ardından, her simge için öğesine bir [bit eşlem](../../extensibility/bitmap-element.md) öğesi ekleyin `Bitmaps` . Bu, bit eşlem kaynağının konumunu belirlediğiniz yerdir. Daha fazla bilgi için bkz. [menü komutlarına simgeler ekleme](../../extensibility/adding-icons-to-menu-commands.md).

   En fazla menü, Grup ve komutları doğru şekilde yerleştirmek için üst yapıya sahip olabilirsiniz. Çok büyük komut kümelerinde veya bir menü, Grup veya komutun birden çok yerde görünmesi gerektiğinde, komut yerleşimini belirtmenizi öneririz.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE 'ye UI öğeleri yerleştirmek için üst öğeye güvenme

1. Tipik bir üst öğe için, `Parent` her, `Menu` `Group` , ve içinde bir öğesi oluşturun `Command` .

    Öğesinin hedefi, `Parent` menü, Grup veya komutu içerecek olan menü ya da gruptur.

   1. Özniteliği, `guid` `GuidSymbol` komut kümesini tanımlayan öğenin adına ayarlayın. Hedef öğe paketinizin bir parçası değilse, ilgili *. vsct* dosyasında tanımlandığı şekilde, bu komut kümesi için GUID kullanın.

   2. `id`Özniteliği `id` hedef menünün veya grubun özniteliğiyle eşleşecek şekilde ayarlayın. Visual Studio tarafından sunulan menülerin ve grupların listesi için bkz. Visual [Studio menülerinin GUID 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) , [Visual Studio araç çubuklarının GUID 'leri ve kimlikleri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   IDE 'ye yerleştirilecek çok sayıda UI öğesi varsa veya birden fazla yerde görünmesi gereken öğeleriniz varsa, aşağıdaki adımlarda gösterildiği gibi, bu öğelerin konumlarını [CommandPlacements](../../extensibility/commandplacements-element.md) öğesinde tanımlayın.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>IDE 'ye UI öğeleri yerleştirmek için komut yerleşimini kullanmak için

1. `Commands` öğesinden sonra `CommandPlacements` öğesini ekleyin.

2. Öğesinde, `CommandPlacements` `CommandPlacement` yerleştirilecek her menü, Grup veya komut için bir öğe ekleyin.

    Her `CommandPlacement` öğe veya `Parent` öğe bir IDE konumunda bir menü, Grup veya komut koyar. UI öğesi yalnızca bir üst öğeye sahip olabilir, ancak birden fazla komut yerleşimi olabilir. Birden çok konuma bir UI öğesi yerleştirmek için, `CommandPlacement` her konum için bir öğe ekleyin.

3. `guid` `id` Her öğenin ve özniteliklerini `CommandPlacement` bir öğesi için yaptığınız gibi barındırma menüsüne veya gruba ayarlayın `Parent` . Ayrıca, `priority` Kullanıcı arabirimi öğesinin göreli konumunu oluşturmak için özniteliğini de ayarlayabilirsiniz.

   Yerleşimi, olma ve komut yerleşimi ile karıştırabilirsiniz. Ancak, çok büyük komut kümeleri için yalnızca komut yerleşimini kullanmanızı öneririz.

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
- [Visual Studio komut tablosu (. vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)