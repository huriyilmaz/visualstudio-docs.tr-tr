---
title: Yazma. Vsct Dosyaları | Microsoft Dokümanlar
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
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709991"
---
# <a name="author-vsct-files"></a>Yazar .vsct dosyaları
Bu belge, Visual Studio tümleşik geliştirme ortamına (IDE) menü öğeleri, araç çubukları ve diğer kullanıcı arabirimi (UI) öğeleri eklemek için bir *.vsct* dosyasının nasıl yazılabildiğini gösterir. UI öğelerini zaten *.vsct* dosyası olmayan bir Visual Studio paketine (VSPackage) eklerken bu adımları kullanın.

 Yeni projelerde, seçimlerinize bağlı olarak menü komutu, araç penceresi veya özel bir düzenleyici için gerekli öğelere sahip bir *.vsct* dosyası oluşturduğundan Visual Studio paket şablonunu kullanmanızı öneririz. Bu *.vsct* dosyasını VSPackage'ınızın gereksinimlerini karşılayacak şekilde değiştirebilirsiniz. *.vsct* dosyasının nasıl değiştirilenhakkında daha fazla bilgi [için, Genişlet menüleri ve komutlarındaörneklere](../../extensibility/extending-menus-and-commands.md)bakın.

## <a name="author-the-file"></a>Dosyayı yazar
 Bu aşamalarda bir *.vsct* dosyası yazma: Dosya ve kaynaklar için yapı oluşturun, UI öğelerini bildirin, IDE'ye ui öğelerini koyun ve özel leştirilmiş davranışlar ekleyin.

### <a name="file-structure"></a>Dosya yapısı
 *.vsct* dosyasının temel yapısı, Bir [Commands](../../extensibility/commands-element.md) öğesi ve [Semboller](../../extensibility/symbols-element.md) öğesi içeren bir [CommandTable](../../extensibility/commandtable-element.md) kök öğesidir.

#### <a name="to-create-the-file-structure"></a>Dosya yapısını oluşturmak için

1. Nasıl yapilir' daki adımları izleyerek projenize *bir .vsct* [dosyası ekleyin: .vsct dosyası oluşturun.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

2. Aşağıdaki örnekte gösterildiği `CommandTable` gibi, öğeye gerekli ad alanlarını ekleyin:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. Öğede, `CommandTable` tüm `Commands` özel menülerinizi, araç çubuklarınızı, komut gruplarınızı ve komutlarınızı barındıracak bir öğe ekleyin. Özel Kullanıcı Arabirimi öğelerinizin `Commands` yüklenabilmesi `Package` için, öğenin özniteliğipaketin adına ayarlanmalıdır.

     Öğeden `Commands` sonra, `Symbols` paketin GUI'lerini tanımlamak için bir öğe ve Kullanıcı Arabirimi öğeleriniz için adlar ve komut adları ekleyin.

### <a name="include-visual-studio-resources"></a>Visual Studio kaynaklarını ekleyin
 Visual Studio komutlarını tanımlayan dosyalara ve Web-servis aracı öğelerinizi IDE'ye koymak için gereken menülere erişmek için [Extern](../../extensibility/extern-element.md) öğesini kullanın. Paketinizin dışında tanımlanan komutları kullanacaksanız, Visual Studio'yu bilgilendirmek için [UsedCommands](../../extensibility/usedcommands-element.md) öğesini kullanın.

#### <a name="to-include-visual-studio-resources"></a>Visual Studio kaynaklarını eklemek için

1. `CommandTable` Öğenin üst kısmında, başvurulacak her dış dosya için bir `Extern` öğe ekleyin ve dosyanın adına özniteliği ayarlayın. `href` Visual Studio kaynaklarına erişmek için aşağıdaki üstbilgi dosyalarına başvuruda bulunabilirsiniz:

   - *Stdidcmd.h*: Visual Studio tarafından açığa çıkarılan tüm komutlar için tanımları tanımlar.

   - *Vsshlids.h*: Visual Studio menüleri için komut ilikleri içerir.

2. Paketiniz Visual Studio veya diğer paketler tarafından tanımlanan komutları `UsedCommands` çağırıyorsa, öğeden `Commands` sonra bir öğe ekleyin. Bu öğeyi, paketinizin bir parçası olmayan her komut için bir [UsedCommand](../../extensibility/usedcommand-element.md) öğesi yle doldurun. Öğelerin `guid` `id` ve özniteliklerini, `UsedCommand` çağrılması gereken komutların GUID ve KIMLIK değerlerine ayarlayın.

   Visual Studio komutlarının GUID'lerini ve d'lerini nasıl bulacağı hakkında daha fazla bilgi için [Visual Studio komutlarının GUID'leri ve dislerini](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)görün. Diğer paketlerden komutları aramak için GUID'i ve bu paketler için *.vsct* dosyasında tanımlanan komutun kimliğini kullanın.

### <a name="declare-ui-elements"></a>UI öğelerini bildir
 `Symbols` *.vsct* dosyasının bölümündeki tüm yeni UI öğelerini bildirin.

#### <a name="to-declare-ui-elements"></a>UI öğelerini bildirmek için

1. Öğeye `Symbols` üç [GuidSymbol](../../extensibility/guidsymbol-element.md) öğesi ekleyin. Her `GuidSymbol` öğenin `name` bir özniteliği ve özniteliği `value` vardır. Özniteliği, öğenin `name` amacını yansıtacak şekilde ayarlayın. Öznitelik `value` bir GUID alır. (Araçlar menüsünde bir **Tools** GUID oluşturmak için **GUID Oluştur'u**seçin ve ardından **Kayıt Defteri Biçimi'ni**seçin.)

     İlk `GuidSymbol` öğe paketinizi temsil eder ve genellikle alt öğesi yoktur. İkinci `GuidSymbol` öğe komut kümesini temsil eder ve menülerinizi, gruplarınızı ve komutlarınızı tanımlayan tüm sembolleri içerir. Üçüncü `GuidSymbol` öğe görüntü deponuzu temsil eder ve komutlarınız için tüm simgeler için semboller içerir. Simgeleri kullanan komutlarınız yoksa, üçüncü `GuidSymbol` öğeyi atlayabilirsiniz.

2. Komut `GuidSymbol` kümenizi temsil eden öğeye bir veya daha fazla [IDSymbol](../../extensibility/idsymbol-element.md) öğesi ekleyin. Bunların her biri, UI'ye eklediğiniz bir menü, araç çubuğu, grup veya komutu temsil ediyor.

     Her `IDSymbol` öğe için, `name` ilgili menü, grup veya komuta başvurmak için kullanacağınız ada özniteliğini ayarlayın ve ardından öğeyi `value` komut kimliğini temsil edecek bir hexadecimal sayıya ayarlayın. Aynı `IDSymbol` üst öğeye sahip hiçbir iki öğe aynı değere sahip olamaz.

3. UI öğelerinizden herhangi biri simge gerektiriyorsa, görüntü `GuidSymbol` deponuzu temsil eden öğeye her simge için bir `IDSymbol` öğe ekleyin.

### <a name="put-ui-elements-in-the-ide"></a>IDE'ye UI öğelerini koyma
 [Menüler,](../../extensibility/menus-element.md) [Gruplar](../../extensibility/groups-element.md)ve [Düğmeler](../../extensibility/buttons-element.md) öğeleri, paketinizde tanımlanan tüm menülerin, grupların ve komutların tanımlarını içerir. Bu menüleri, grupları ve komutları IDE'ye, UI öğesi tanımının bir parçası olan [Bir Üst](../../extensibility/parent-element.md) öğeyi kullanarak veya başka bir yerde tanımlanan bir [Komut Yerleştirme](../../extensibility/commandplacement-element.md) öğesi kullanarak koyun.

 Her `Menu` `Group`, `Button` ve öğe `guid` bir öznitelik ve bir `id` öznitelik vardır. Her zaman `guid` komut kümenizi temsil `GuidSymbol` eden öğenin adı yla eşleşecek şekilde özniteliği ayarlayın ve `id` özniteliği, `IDSymbol` `Symbols` menünüzü, grubunuzu veya komutunuzu temsil eden öğenin adına ayarlayın.

#### <a name="to-define-ui-elements"></a>UI öğelerini tanımlamak için

1. Yeni menüler, alt menüler, kısayol menüleri veya araç çubukları tanımlıyorsanız, `Menus` `Commands` öğeye bir öğe ekleyin. Ardından, oluşturulacak her menü için [Menu](../../extensibility/menu-element.md) `Menus` öğeye bir Menü öğesi ekleyin.

    Öğenin `guid` `id` özniteliklerini `Menu` ve özniteliklerini `type` ayarlayın ve özniteliği istediğiniz menü türüne ayarlayın. Ayrıca, üst `priority` gruptaki menünün göreli konumunu oluşturmak için özniteliği de ayarlayabilirsiniz.

   > [!NOTE]
   > Öznitelik `priority` araç çubukları ve bağlam menüleri için geçerli değildir.

2. Visual Studio IDE'deki tüm komutlar, menülerin ve araç çubuklarının doğrudan alt öğeleri olan komut grupları tarafından barındırılmalıdır. IDE'ye yeni menüler veya araç çubukları ekliyorsanız, bunlar yeni komut grupları içermelidir. Komutlarınızı görsel olarak gruplandırmak için varolan menülere ve araç çubuklarına komut grupları da ekleyebilirsiniz.

    Yeni komut grupları eklediğinizde, önce `Groups` bir öğe oluşturmanız ve sonra da her komut grubu için bir [Grup](../../extensibility/group-element.md) öğesi eklemeniz gerekir.

    Her `Group` `guid` öğenin ve `id` özniteliklerini ayarlayın `priority` ve sonra üst menüde grubun göreli konumunu oluşturmak için özniteliği ayarlayın. Daha fazla bilgi için [bkz.](../../extensibility/creating-reusable-groups-of-buttons.md)

3. IDE'ye yeni komutlar ekliyorsanız, `Buttons` `Commands` öğeye bir öğe ekleyin. Ardından, her komut için [Button](../../extensibility/button-element.md) `Buttons` öğeye bir Düğme öğesi ekleyin.

   1. Her `Button` `guid` öğenin özniteliklerini ve `id` özniteliklerini `type` ayarlayın ve özniteliği istediğiniz düğmeye ayarlayın. Özniteliği, ana `priority` gruptaki komutun göreli konumunu oluşturmak için de ayarlayabilirsiniz.

       > [!NOTE]
       > Araç `type="button"` çubuklarındaki standart menü komutları ve düğmeleri için kullanın.

   2. Öğede, `Button` [Bir ButtonText](../../extensibility/buttontext-element.md) öğesi ve [CommandName](../../extensibility/commandname-element.md) öğesi içeren bir [Strings](../../extensibility/strings-element.md) öğesi ekleyin. Öğe, `ButtonText` bir menü öğesi için metin etiketini veya araç çubuğu düğmesi için araç ucunu sağlar. Öğe, `CommandName` komut kuyusu kullanmak için komutun adını sağlar.

   3. Komutunuzda bir simge olacaksa, `Button` öğede bir [Simge](../../extensibility/icon-element.md) öğesi oluşturun `Bitmap` ve simgenin öğesine `guid` `id` özniteliklerini ayarlayın.

       > [!NOTE]
       > Araç çubuğu düğmelerinde simgeler olmalıdır.

   Daha fazla bilgi için [MenuCommands vs. OleMenuCommands'a](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015)bakın.

4. Komutlarınızdan herhangi biri simge gerektiriyorsa, `Commands` öğeye bir [Bitmaps](../../extensibility/bitmaps-element.md) öğesi ekleyin. Ardından, her simge için `Bitmaps` öğeye bir [Bitmap](../../extensibility/bitmap-element.md) öğesi ekleyin. Bu, bit eşlemi kaynağının konumunu belirttiğiniz yerdir. Daha fazla bilgi için bkz: [Menü komutlarına simge ekle.](../../extensibility/adding-icons-to-menu-commands.md)

   Çoğu menüyü, grubu ve komutu doğru bir şekilde yerleştirmek için ebeveynlik yapısına güvenebilirsiniz. Çok büyük komut kümeleri için veya bir menü, grup veya komutun birden çok yerde görünmesi gerektiğinde, komut yerleşimini belirtmenizi öneririz.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE'ye UI öğeleri yerleştirmek için ebeveynlik

1. Tipik ebeveynlik için, `Parent` paketinizde `Menu` `Group`tanımlanan `Command` her , ve öğede bir öğe oluşturun.

    Öğenin `Parent` hedefi menü, grup veya komutu içeren menü veya gruptur.

   1. `guid` Özniteliği komut kümesini tanımlayan `GuidSymbol` öğenin adına ayarlayın. Hedef öğe paketinizin bir parçası değilse, ilgili *.vsct* dosyasında tanımlandığı şekilde bu komut kümesinin guid'ini kullanın.

   2. `id` Hedef menünün veya `id` grubun özniteliğiyle eşleşecek şekilde özniteliği ayarlayın. Visual Studio tarafından ortaya çıkarılan menülerin ve grupların listesi için Visual [Studio menülerinin GUID'leri ve d'leri](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) veya [Visual Studio araç çubuklarının GUI'leri ve d'leri](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)bölümüne bakın.

   IDE'ye yerleştirmeniz gereken çok sayıda UI öğeniz varsa veya birden çok yerde görünmesi gereken öğeler varsa, aşağıdaki adımlarda gösterildiği gibi bunların yerleşimlerini [Komut Yerleşimleri](../../extensibility/commandplacements-element.md) öğesinde tanımlayın.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>IDE'ye UI öğelerini yerleştirmek için komut yerleşimini kullanmak için

1. `Commands` öğesinden sonra `CommandPlacements` öğesini ekleyin.

2. Öğede, `CommandPlacements` her `CommandPlacement` menü, grup veya komut yerine bir öğe ekleyin.

    Her `CommandPlacement` öğe `Parent` veya öğe bir menü, grup veya komutu bir IDE konumuna yerleştirir. UI öğesi yalnızca bir üst öğesi olabilir, ancak birden çok komut yerleşimi olabilir. Birden çok konuma bir UI öğesi `CommandPlacement` yerleştirmek için, her konum için bir öğe ekleyin.

3. Her `CommandPlacement` `guid` öğenin özniteliklerini ve `id` özniteliklerini, tıpkı bir `Parent` öğe için olduğu gibi barındırma menüsüne veya grubuna ayarlayın. Ayrıca, UI `priority` öğesinin göreli konumunu oluşturmak için özniteliği ayarlayabilirsiniz.

   Ebeveynlik ve komut yerleşimine göre yerleşimi karıştırabilirsiniz. Ancak, çok büyük komut kümeleri için yalnızca komut yerleşimi kullanmanızı öneririz.

### <a name="add-specialized-behaviors"></a>Özelleştirilmiş davranışlar ekleme
 Örneğin, menülerin ve komutların davranışını değiştirmek ve görünümlerini ve görünümlerini değiştirmek için [CommandFlag](../../extensibility/command-flag-element.md) öğesini kullanabilirsiniz. Ayrıca, [Bir komutgörünür](../../extensibility/visibilityconstraints-element.md) olduğunda Görünürlük Kısıtlamalar öğesini kullanarak etkileyebilir veya [KeyBindings](../../extensibility/keybindings-element.md) öğesini kullanarak klavye kısayolları ekleyebilirsiniz. Belirli menü ve komut türleri zaten yerleşik özel davranışlar var.

#### <a name="to-add-specialized-behaviors"></a>Özel leştirilmiş davranışlar eklemek için

1. Örneğin, bir çözüm yüklendiğinde, bir UI öğesini yalnızca belirli Ara Birimi bağlamlarında görünür hale getirmek için görünürlük kısıtlamalarını kullanın.

   1. `Commands` öğesinden sonra `VisibilityConstraints` öğesini ekleyin.

   2. Sınırlandıracak her bir Ara-öğretim elemanı için bir [Görünürlük Öğesi](../../extensibility/visibilityitem-element.md) öğesi ekleyin.

   3. Her `VisibilityItem` öğe için, `guid` `id` menü, grup veya komuta ve özdeyişler ayarlayın ve sonra `context` <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> sınıfta tanımlandığı gibi istediğiniz UI bağlamına özniteliği ni ayarlayın.

2. Bir Ara-Öğretim Üyesi öğenin koddaki görünürlüğünü veya kullanılabilirliğini ayarlamak için aşağıdaki komut bayraklarından birini veya birkaçını kullanın:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Daha fazla bilgi için [CommandFlag](../../extensibility/command-flag-element.md) öğesine bakın.

3. Bir öğenin görünümünü değiştirmek veya görünümünü dinamik olarak değiştirmek için aşağıdaki komut bayraklarından birini veya birkaçını kullanın:

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

   Daha fazla bilgi için [CommandFlag](../../extensibility/command-flag-element.md) öğesine bakın.

4. Bir öğenin komutları aldığında nasıl tepki vereceğini değiştirmek için aşağıdaki komut bayraklarından birini veya birkaçını kullanın:

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

   Daha fazla bilgi için [CommandFlag](../../extensibility/command-flag-element.md) öğesine bakın.

5. Menüye veya menüdeki bir öğeye menüye bağlı klavye kısayolu eklemek için, menü `ButtonText` veya menü öğesi öğesine bir amper ve karakter (&) ekleyin. Ampersand'ı izleyen karakter, üst menü açıkken etkin klavye kısayoludur.

6. Bir komuta menüden bağımsız klavye kısayolu eklemek için [KeyBindings](../../extensibility/keybindings-element.md) öğesini kullanın. Daha fazla bilgi için [KeyBinding](../../extensibility/keybinding-element.md) öğesine bakın.

7. Menü metnini yerelleştirmek `LocCanonicalName` için öğeyi kullanın. Daha fazla bilgi için [Strings](../../extensibility/strings-element.md) öğesine bakın.

   Bazı menü ve düğme türleri özel leştirilmiş davranışlar içerir. Aşağıdaki listede bazı özel menü ve düğme türleri açıklanmaktadır. Diğer türler için `types` [Menü,](../../extensibility/menu-element.md) [Düğme](../../extensibility/button-element.md)ve [Combo](../../extensibility/combo-element.md) öğelerindeki öznitelik açıklamalarına bakın.

   - Açılan kutu: Açılan kutu, araç çubuğunda kullanılabilecek açılır listedir. UI'ye açılan kutular eklemek `Commands` için, öğede bir [Kombinasyon](../../extensibility/combos-element.md) öğesi oluşturun. Sonra öğeye `Combos` eklemek `Combo` için her açılan kutu için bir öğe ekleyin. `Combo`öğeler, `Button` öğelerle aynı özelliklere ve `DefaultWidth` çocuklara `idCommandList` sahiptir ve aynı zamanda öznitelikleri ve özellikleri vardır. Öznitelik `DefaultWidth` pikselgenişliği ayarlar ve `idCommandList` öznitelik açılan kutusunu doldurmak için kullanılan bir komut kimliği ne işaret eder.

   - Menü denetleyicisi: Menü denetleyicisi, yanında ok olan bir düğmedir. Oku tıklattığınızda bir liste açılır. UI'ye bir menü denetleyicisi `Menu` eklemek için `type` bir `MenuController` öğe `MenuControllerLatched`oluşturun ve özniteliğini istediğiniz davranışa bağlı olarak ayarlayın. Bir menü denetleyicisini doldurmak için, öğenin `Group` üst öğesi olarak ayarlayın. Menü denetleyicisi, açılan listesinde o grubun tüm alt çocuklarını görüntüler.

## <a name="see-also"></a>Ayrıca bkz.
- [Menüleri ve komutları genişletme](../../extensibility/extending-menus-and-commands.md)
- [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML şema referansı](../../extensibility/vsct-xml-schema-reference.md)
