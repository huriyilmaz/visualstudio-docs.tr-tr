---
title: 'Nasıl yapabilirsiniz: Kısayol menüsüne komut ekleme'
description: Kullanıcılarının DSL'nize özgü görevleri gerçekleştirene kadar etki alanına özgü dilinize (DSL) menü komutlarını nasıl ekleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: db4e032f755337067ba208c0a8a6267c155ba4847b8259e7f5f7cd70822b9509
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231632"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Nasıl yapabilirsiniz: Kısayol menüsüne komut ekleme

Kullanıcılarının DSL'nize özgü görevleri gerçekleştirene kadar etki alanına özgü dilinize (DSL) menü komutları ekleyebilirsiniz. Komutlar, kullanıcılar diyagrama sağ tıklansa bağlam (kısayol) menüsünde görünür. Bir komutu yalnızca belirli durumlarda menüde görünür olacak şekilde tanımlayabilirsiniz. Örneğin, komutu yalnızca kullanıcı belirli öğe türlerine veya belirli eyaletlerde öğelere tıkladığında görünür hale ekleyebilirsiniz.

Özetle, dslpackage projesinde adımlar aşağıdaki gibi gerçekleştirilir:

1. [Komutu Commands.vsct içinde bildir](#VSCT)

2. [içinde paket sürüm numarasını Package.tt.](#version) Commands.vsct'i her değiştiriyorken bunu yapmak zorundasınız

3. [Komutu görünür yapmak ve komutun](#CommandSet) ne yapmak istediğini tanımlamak için CommandSet sınıfında yöntemler yazın.

> [!NOTE]
> Ayrıca, CommandSet.cs'de yöntemleri geçersiz karak Kes, Yapıştır, Hepsini Seç ve Yazdır gibi bazı mevcut komutların davranışını değiştirebilirsiniz. Daha fazla bilgi için, [bkz. How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>MEF kullanarak Komut Tanımlama

Yönetilen Uzantı Çerçevesi (MEF), diyagram menüsünde menü komutlarını tanımlamak için alternatif bir yöntem sağlar. Bunun birincil amacı, DSL'nin sizin veya diğer tarafların uzatılabilir olmasıdır. Kullanıcılar yalnızca DSL'yi yükleyebilir veya hem DSL'yi hem de uzantıları yükleyebilir. Ancak MEF, DSL üzerinde MEF'yi etkinleştirmek için ilk çalışmadan sonra kısayol menüsü komutlarını tanımlama çalışmalarını da azaltır.

Aşağıdakiler için bu konudaki yöntemini kullanın:

1. Menü komutlarını sağ tıklama kısayol menüsü dışında menülerde tanımlamak istiyorsunuz.

2. Menüde belirli komut gruplamalarını tanımlamak istediğiniz.

3. Başkalarının DSL'yi kendi komutlarıyla genişletmesini sağlamak istemiyorsunuz.

4. Yalnızca bir komut tanımlamak istediğiniz.

   Aksi takdirde, komutları tanımlamak için MEF yöntemini kullanmayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. MEF kullanarak DSL'nizi genişletme.](../modeling/extend-your-dsl-by-using-mef.md)

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Command.Vsct içinde Komutu Bildir
 Menü komutları DslPackage\Commands.vsct içinde bildirildi. Bu tanımlar, menü öğelerinin etiketlerini ve menülerde nerede görüneceklerini belirtir.

 Düzenley istediğiniz Commands.vsct dosyası, Visual Studio *SDK* yükleme yolu \VisualStudioIntegration\Common\Inc dizininde bulunan birkaç .h dosyasından tanımları içeri aktarır. Ayrıca DSL tanımından oluşturulan GeneratedVsct.vsct'i de içerir.

 .vsct dosyaları hakkında daha fazla bilgi için [bkz. Visual Studio Tablosu () . Vsct) Dosyaları.](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

### <a name="to-add-the-command"></a>Komutu eklemek için

1. Bu **Çözüm Gezgini** **DslPackage projesinin** altında Commands.vsct'i açın.

2. `Commands`öğesinde, bir veya daha fazla düğme ve bir grup tanımlayın. *Düğme,* menüde yer alan bir öğedir. *Grup,* menüde yer alan bir bölümdir. Bu öğeleri tanımlamak için aşağıdaki öğeleri ekleyin:

    ```xml
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Her düğme veya grup bir GUID ve tamsayı kimliği ile tanımlanır. Aynı GUID'ye sahip birkaç grup ve düğme oluşturabilirsiniz. Ancak farklı kimliklere sahip olması gerekir. GUID adları ve kimlik adları, düğümdeki gerçek GUID'lere ve sayısal kimliklere `<Symbols>` çevrilir.

3. Komutun yalnızca etki alanına özgü diliniz bağlamında yüklensin diye bir görünürlük kısıtlaması ekleyin. Daha fazla bilgi için [bkz. VisibilityConstraints Öğesi.](../extensibility/visibilityconstraints-element.md)

     Bunu yapmak için öğesinde öğesi sonra `CommandTable` aşağıdaki öğeleri `Commands` ekleyin.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. GUID'ler ve kimlikler için kullanılan adları tanımlayın. Bunu yapmak için `Symbols` öğesinde öğesi sonra `CommandTable` bir öğesi `Commands` ekleyin.

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. öğesini, `{000...000}` gruplarınızı ve menü öğelerinizi tanımlayan bir GUID ile değiştirin. Yeni bir GUID elde etmek için **Araçlar menüsündeki GUID** oluştur **aracını** kullanın.

    > [!NOTE]
    > Daha fazla grup veya menü öğesi eklerken aynı GUID'yi kullanabilirsiniz. Ancak, için yeni değerler kullan `IDSymbols` gerekir.

6. Bu yordamdan kopyalanan kodda, aşağıdaki dizelerin her oluşumunu kendi dizeleriyle değiştirin:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Package.tt'de Paket Sürümünü güncelleştirme
 Bir komut ekler veya değiştirirken, etki alanına özgü dilinizin yeni sürümünü serbest bırakmadan önce paket sınıfına uygulanan `version` <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> parametresini güncelleştirin.

 Paket sınıfı oluşturulan bir dosyada tanımlandığı için Package.cs dosyasını oluşturan metin şablonu dosyasında özniteliğini güncelleştirin.

### <a name="to-update-the-packagett-file"></a>Package.tt güncelleştirmek için

1. Bu **Çözüm Gezgini** **DslPackage** projesinde **GeneratedCode** klasöründeki Package.tt açın.

2. özniteliğini `ProvideMenuResource` bulun.

3. özniteliğinin `version` ikinci parametre olan parametresini artırır. 5000000000000000000000000000000000000000000000000000000000 Örnek:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Komutun Davranışını Tanımlama

DSL'niz, DslPackage\GeneratedCode\CommandSet.cs içinde bildirilen kısmi bir sınıfta uygulanan bazı komutları zaten içerir. Yeni komutlar eklemek için, aynı sınıfın kısmi bildirimini içeren yeni bir dosya oluşturarak bu sınıfı genişletmelisiniz. Sınıfın adı genellikle *\<YourDslName>* `CommandSet` olur. Başlangıç olarak sınıfın adını doğrular ve içeriğini incelersiniz.

Komut kümesi sınıfı, sınıfından <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> türetildi.

### <a name="extend-the-commandset-class"></a>CommandSet sınıfını genişletme

1. Bu Çözüm Gezgini DslPackage projesinde GeneratedCode klasörünü açın, sonra CommandSet.tt'nin altına bakın ve oluşturulan CommandSet.cs dosyasını açın. Burada tanımlanan ilk sınıfın ad alanını ve adını not ekleyin. Örneğin, şunları görebilir:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. **DslPackage içinde,** Özel Kod adlı bir **klasör oluşturun.** Bu klasörde adlı yeni bir sınıf dosyası `CommandSet.cs` oluşturun.

3. Yeni dosyada, oluşturulan kısmi sınıfla aynı ad alanına ve adına sahip kısmi bir bildirim yazın. Örnek:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     > [!NOTE]
     > Yeni dosyayı oluşturmak için sınıf şablonunu kullandıysanız, hem ad alanını hem de sınıf adını düzeltmeniz gerekir.

Komut kümesi kodunuzun genellikle aşağıdaki ad alanlarını içeri aktarması gerekir:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Ad alanını ve sınıf adını, oluşturulan CommandSet.cs'de bulunan ad alanlarıyla eş olacak şekilde ayarlayın:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Komutun sağ tıklama (bağlam) menüsünde ne zaman görünür olacağını belirlemek için biri de komutu gerçekleştirmek için diğeri olmak üzere iki yöntem tanımlamanız gerekir. Bu yöntemler geçersiz kılma değildir; bunun yerine, bunları bir komut listesine kaydedebilirsiniz.

### <a name="define-when-the-command-will-be-visible"></a>Komutun ne zaman görünür olacağını tanımlama
 Her komut için, komutun menüde görünip görünmeyeceklerini ve etkinleştirilip etkinleştirilmeyeceklerini veya gri olacağını `OnStatus...` belirleyen bir yöntem tanımlayın. Aşağıdaki `Visible` örnekte `Enabled` gösterildiği gibi ve `MenuCommand` özelliklerini ayarlayın. Kullanıcı diyagrama her sağ tıkladığında kısayol menüsünü oluşturmak için bu yöntem çağrılır, bu nedenle hızlı çalışması gerekir.

 Bu örnekte, komut yalnızca kullanıcı belirli bir şekil türünü seçtikten sonra görünür ve yalnızca seçili öğelerden en az biri belirli bir durumda olduğunda etkinleştirilir. Örnek, Sınıf Diyagramı DSL şablonunu temel alan bir şablondur ve ClassShape ve ModelClass, DSL'de tanımlanan türlerdir:

```csharp
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

Aşağıdaki parçalar, OnStatus yöntemlerinde sıklıkla yararlıdır:

- `this.CurrentSelection`. Kullanıcının sağ tıklama şekli her zaman bu listeye eklenir. Kullanıcı diyagramın boş bir parçasına tıklarsa Diyagram listenin tek üyesidir.

- `this.IsDiagramSelected()` - `true` kullanıcı diyagramın boş bir parçasına tıklamışsa.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - kullanıcı birden çok nesne seçmedi

- `this.SingleSelection` - kullanıcının sağ tıklamış olduğu şekil veya diyagram

- `shape.ModelElement as MyLanguageElement` - bir şekille temsil edilen model öğesi.

Genel bir kılavuz olarak, özelliğin nelerin seçili olduğuna bağlı olarak ve özelliğinin seçili öğelerin durumuna bağımlı hale geldi `Visible` `Enabled` niz.

OnStatus yöntemi, Mağazanın durumunu değiştirmez.

### <a name="define-what-the-command-does"></a>Komutun ne yaptığını tanımlama
 Her komut için, kullanıcı `OnMenu...` menü komutuna tıkladığında gerekli eylemi gerçekleştiren bir yöntem tanımlayın.

 Model öğelerinde değişiklik yaptıysanız, bunu bir işlem içinde yapabilirsiniz. Daha fazla bilgi için, [bkz. How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 Bu örnekte , ve , Sınıf Diyagramı DSL şablonundan türetilen DSL içinde `ClassShape` tanımlanan `ModelClass` `Comment` türlerdir.

```csharp
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Modelde nesneden nesneye nasıl gidilen ve nesne ve bağlantı oluşturma hakkında daha fazla bilgi için, [bkz. How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Komutu kaydetme
 C# ' de, CommandSet. vsct 'ın semboller bölümünde yaptığınız GUID ve KIMLIK değerlerinin bildirimlerini yineleyin:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 **Commands. vsct** IÇINE eklediğiniz GUID değerini kullanın.

> [!NOTE]
> VSCT dosyasının semboller bölümünü değiştirirseniz bu bildirimleri eşleşecek şekilde de değiştirmeniz gerekir. Ayrıca, Package.tt içindeki sürüm numarasını da artırmanız gerekir

 Menü komutlarınızı bu komut kümesinin bir parçası olarak kaydedin. `GetMenuCommands()` Diyagram başlatıldığında bir kez çağrılır:

```csharp
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Komutu test etme
 Visual Studio deneysel bir örnekte DSL oluşturun ve çalıştırın. Komutun, belirttiğiniz durumlarda kısayol menüsünde görünmesi gerekir.

### <a name="to-exercise-the-command"></a>Komutu uygulamak için

1. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür**' e tıklayın.

2. Çözümü yeniden derlemek için **F5** tuşuna basın ve deneysel derlemede alana özgü dilde hata ayıklamaya başlayın.

3. Deneysel derlemede, örnek bir diyagram açın.

4. Komutun doğru şekilde etkinleştirildiğini veya devre dışı bırakıldığını ve seçili öğeye bağlı olarak uygun şekilde görüntülendiğini veya gizlendiğini doğrulamak için diyagramdaki çeşitli öğelere sağ tıklayın.

## <a name="troubleshoot"></a>Sorun giderme

**Komut menüde görünmüyor:**

- bu komut, DSL paketini yükleyene kadar yalnızca Visual Studio hata ayıklama örneklerinde görünür. Daha fazla bilgi için bkz. [Domain-Specific dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

- Deneysel örneklerinizin bu DSL için doğru dosya adı uzantısına sahip olduğundan emin olun. Dosya adı uzantısını denetlemek için Visual Studio ana örneğinde DslDefinition. dsl dosyasını açın. Ardından DSL Gezgini ' nde düzenleyici düğümüne sağ tıklayın ve ardından Özellikler ' e tıklayın. Özellikler penceresi FileExtension özelliğini inceleyin.

- [Paket sürüm numarasını artırdınız](#version)mı?

- OnStatus yönteminizin başlangıcında bir kesme noktası ayarlayın. Diyagramın herhangi bir kısmına sağ tıkladığınızda bu, kesmesi gerekir.

**OnStatus yöntemi çağrılmadı**:

- CommandSet kodunuzda GUID 'lerin ve kimliklerin Commands. vsct 'ın semboller bölümünde olanlarla eşleştiğinden emin olun.

- Commands. vsct içinde, her üst düğümdeki GUID ve KIMLIğIN doğru üst grubu tanımladığınızdan emin olun.

- Visual Studio komut isteminde devenv/rootsuffix exp/setupyazın. Sonra Visual Studio hata ayıklama örneğini yeniden başlatın.

- Komutun doğrulanması için OnStatus metodunu adım adım yapın. Görünür ve komut. Etkin özelliği true olarak ayarlandı.

**Yanlış menü metni görünüyor veya komut yanlış yerde görünüyor**:

- GUID ve ID birleşiminin bu komuta özgü olduğundan emin olun.

- Paketin önceki sürümlerini kaldırdığınızdan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki alanına özgü dili özelleştirmek için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md)
- [Örnek kod: devre şemaları](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
