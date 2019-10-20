---
title: 'Nasıl yapılır: Kısayol Menüsüne Komut Ekleme'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7d873a3401e37a18b938cb5785f33eb0bc9b8fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666716"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Nasıl yapılır: Kısayol Menüsüne Komut Ekleme

Kullanıcılarınızın DSL 'nize özgü görevler gerçekleştirebilmesi için, etki alanına özgü dilinize (DSL) menü komutları ekleyebilirsiniz. Kullanıcılar diyagrama sağ tıkladığınızda, komutlar bağlam (kısayol) menüsünde görünür. Yalnızca belirli koşullarda menüde görünmesi için bir komut tanımlayabilirsiniz. Örneğin, komutu yalnızca Kullanıcı belirli türde öğe veya belirli durumlarda öğeler ' i tıklattığında görünür hale getirebilirsiniz.

Özetle, adımlar DslPackage projesinde aşağıdaki gibi gerçekleştirilir:

1. [Commands. vsct içinde komutu bildirin](#VSCT)

2. [Package.tt içinde paket sürüm numarasını güncelleştirin](#version). Komutları her değiştirdiğinizde bunu yapmanız gerekir. vsct

3. Komutu görünür hale getirmek ve komutun ne yapmasını istediğinizi tanımlamak için [CommandSet sınıfına Yöntemler yazın](#CommandSet) .

   Örnekler için [görselleştirme ve modelleme SDK Web sitesine](http://go.microsoft.com/fwlink/?LinkID=185579)bakın.

> [!NOTE]
> Ayrıca, kes, Yapıştır, Tümünü Seç ve CommandSet.cs içindeki yöntemleri geçersiz kılarak Yazdır gibi bazı mevcut komutların davranışını değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>MEF kullanarak bir komut tanımlama

Yönetilen uzantı çerçevesi (MEF), Diyagram menüsünde menü komutlarının tanımlanması için alternatif bir yöntem sağlar. Birincil amacı, bir DSL 'yi sizin veya diğer taraflarca genişletmek üzere etkinleştirmektir. Kullanıcılar yalnızca DSL 'yi yüklemeyi seçebilir veya hem DSL hem de uzantıları yükleyebilir. Ancak MEF, DSL üzerinde MEF 'i etkinleştirmek için ilk çalıştıktan sonra, kısayol menü komutlarının tanımlanmasıyla ilgili işi de azaltır.

Aşağıdaki durumlarda bu konudaki yöntemini kullanın:

1. Menü komutlarını sağ tıklama kısayol menüsü dışındaki menülerde tanımlamak istiyorsunuz.

2. Menüde belirli komut gruplandırmaları tanımlamak istiyorsunuz.

3. Başkalarının DSL 'yi kendi komutlarıyla genişletmelerini sağlamak istemezsiniz.

4. Yalnızca bir komut tanımlamak istiyorsunuz.

   Aksi takdirde, komutları tanımlamak için MEF metodunu kullanmayı düşünün. Daha fazla bilgi için bkz. [mef kullanarak DSL 'Nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="VSCT"></a>Commands. vsct içinde komutu bildirin
 Menü komutları Dslpackage\commandsve vsct' içinde bildirilmiştir. Bu tanımlar menü öğelerinin etiketlerini ve menülerde nerede göründüğünü belirtir.

 Commands. vsct olan dosya, *Visual STUDIO SDK install Path*\VisualStudioIntegration\Common\Inc. dizininde bulunan çeşitli. h dosyalarından tanımları içeri aktarır. Ayrıca DSL tanımınızdan oluşturulan GeneratedVsct. vsct öğesini de içerir.

 . Vsct dosyaları hakkında daha fazla bilgi için bkz. [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Komutu eklemek için

1. **Çözüm Gezgini**, **DslPackage** projesi altında Commands. vsct öğesini açın.

2. @No__t_0 öğesinde bir veya daha fazla düğme ve grup tanımlayın. *Düğme* , menüdeki bir öğedir. Bir *Grup* , menüdeki bir bölümdür. Bu öğeleri tanımlamak için aşağıdaki öğeleri ekleyin:

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
    > Her düğme veya grup bir GUID ve bir tamsayı KIMLIĞI ile tanımlanır. Aynı GUID ile birkaç grup ve düğme oluşturabilirsiniz. Ancak, farklı kimliklere sahip olmaları gerekir. GUID adları ve KIMLIK adları, `<Symbols>` düğümündeki gerçek GUID 'lere ve sayısal kimliklere çevrilir.

3. Yalnızca etki alanına özgü dilinizin bağlamında yüklenebilmesi için komut için görünürlük kısıtlaması ekleyin. Daha fazla bilgi için bkz. [Visibilitykısıtlamalar öğesi](../extensibility/visibilityconstraints-element.md).

     Bunu yapmak için, `Commands` öğesinden sonra `CommandTable` öğesine aşağıdaki öğeleri ekleyin.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. GUID 'ler ve kimlikler için kullandığınız adları tanımlayın. Bunu yapmak için, `Commands` öğesinden sonra `CommandTable` öğesinde bir `Symbols` öğesi ekleyin.

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

5. @No__t_0, gruplarınızı ve menü öğelerinizi tanımlayan bir GUID ile değiştirin. Yeni bir GUID almak için, **Araçlar** menüsünde **GUID oluştur** aracını kullanın.

    > [!NOTE]
    > Daha fazla grup veya menü öğesi eklerseniz, aynı GUID 'yi kullanabilirsiniz. Ancak, `IDSymbols` için yeni değerler kullanmanız gerekir.

6. Bu yordamdan kopyaladığınız kodda, aşağıdaki dizelerin her oluşumunu kendi dizelerinizle değiştirin:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="version"></a>Package.tt 'de paket sürümünü güncelleştirme
 Bir komut eklediğinizde veya değiştirdiğinizde, etki alanına özgü dilin yeni sürümünü bırakmadan önce paket sınıfına uygulanan <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> `version` parametresini güncelleştirin.

 Paket sınıfı oluşturulmuş bir dosyada tanımlandığından, Package.cs dosyasını oluşturan metin şablonu dosyasında özniteliğini güncelleştirin.

### <a name="to-update-the-packagett-file"></a>Package.tt dosyasını güncelleştirmek için

1. **Çözüm Gezgini**, **DslPackage** projesinde, **GeneratedCode** klasöründe, Package.tt dosyasını açın.

2. @No__t_0 özniteliğini bulun.

3. İkinci parametre olan özniteliğin `version` parametresini artırın. İsterseniz, size amacını hatırlatmak için parametre adını açıkça yazabilirsiniz. Örneğin:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="CommandSet"></a>Komutun davranışını tanımlama

DSL 'niz zaten DslPackage\GeneratedCode\CommandSet.cs. içinde belirtilen kısmi bir sınıfta uygulanan bazı komutlara sahiptir Yeni komutlar eklemek için, aynı sınıfın kısmi bildirimini içeren yeni bir dosya oluşturarak bu sınıfı genişletmeniz gerekir. Sınıfın adı genellikle `CommandSet` *> \<YourDslName* . Sınıfın adını doğrulayarak ve içeriğini inceleyerek başlamak yararlı olur.

Komut kümesi sınıfı <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> türetilir.

### <a name="extend-the-commandset-class"></a>CommandSet sınıfını genişletme

1. Çözüm Gezgini, DslPackage projesinde, GeneratedCode klasörünü açın ve ardından CommandSet.tt ' ın altında, oluşturulan dosya CommandSet.cs ' nı açın. Ad alanını ve burada tanımlanan ilk sınıfın adını unutmayın. Örneğin, şu şekilde karşılaşabilirsiniz:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. **DslPackage**' de, **özel kod**adlı bir klasör oluşturun. Bu klasörde, `CommandSet.cs` adlı yeni bir sınıf dosyası oluşturun.

3. Yeni dosyada, oluşturulan kısmi sınıfla aynı ad alanına ve ada sahip kısmi bir bildirim yazın. Örneğin:

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

Ad alanını ve sınıf adını oluşturulan CommandSet.cs eşleşecek şekilde ayarlayın:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Komutun sağ tıklama (bağlam) menüsünde görünür olacağını ve komutu gerçekleştirmeye yönelik diğerini belirlemek için iki yöntem tanımlamanız gerekir. Bu Yöntemler geçersiz kılınmaz; Bunun yerine, bunları bir komut listesine kaydedersiniz.

### <a name="define-when-the-command-will-be-visible"></a>Komutun ne zaman görünür olacağını tanımlayın
 Her komut için, komutun menüde görünüp görünmeyeceğini ve etkinleştirilip etkinleştirilmeyeceğini veya büyümeyeceğini belirleyen bir `OnStatus...` yöntemi tanımlayın. Aşağıdaki örnekte gösterildiği gibi `MenuCommand` `Visible` ve `Enabled` özelliklerini ayarlayın. Bu yöntem, kullanıcının Diyagramı sağ tıkladığı her seferinde kısayol menüsünü oluşturmak için çağrılır, bu nedenle hızlı bir şekilde çalışır.

 Bu örnekte, komut yalnızca Kullanıcı belirli bir şekil türünü seçtiğinde görünür ve yalnızca seçili öğelerden en az biri belirli bir durumda olduğunda etkindir. Örnek, DSL şablonu sınıf diyagramı ' na dayalıdır ve ClassShape ve ModelClass, DSL içinde tanımlanan türlerdir:

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

Aşağıdaki parçalar OnStatus yöntemlerinde sıklıkla faydalıdır:

- `this.CurrentSelection`. Kullanıcının sağ tıklamış olduğu şekil bu listeye her zaman dahildir. Kullanıcı diyagramın boş bir kısmına tıkladığında diyagram, listenin tek üyesidir.

- Kullanıcı diyagramın boş bir bölümüne tıklandığı `true`  -  `this.IsDiagramSelected()`.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`-Kullanıcı birden çok nesne seçmedi

- `this.SingleSelection`-kullanıcıya sağ tıklamış olan şekil veya diyagram

- `shape.ModelElement as MyLanguageElement`-bir şekil tarafından temsil edilen model öğesi.

Genel bir kılavuz olarak, `Visible` özelliğinin seçili öğelere bağlı olmasını ve `Enabled` özelliğinin seçili öğelerin durumuna bağlı olmasını sağlayın.

OnStatus yöntemi deponun durumunu değiştirmemelidir.

### <a name="define-what-the-command-does"></a>Komutun ne yaptığını tanımlayın
 Her komut için, Kullanıcı menü komutuna tıkladığında gerekli eylemi gerçekleştiren bir `OnMenu...` yöntemi tanımlayın.

 Model öğelerinde değişiklik yaparsanız, bunu bir işlem içinde yapmanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 Bu örnekte, `ClassShape`, `ModelClass` ve `Comment`, DSL şablonunda tanımlanan ve bu tür bir DSL şablonundan türetilen türlerdir.

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

 Bir nesneden nesne ve bağlantı oluşturma hakkında daha fazla bilgi için, bkz. [nasıl yapılır: bir standart menü komutunu değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Komutu Kaydet
 C# CommandSet. vsct 'ın semboller bölümünde yaptığınız GUID ve kimlik değerlerinin bildirimlerinde yineleyin:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 **Commands. vsct**IÇINE eklediğiniz GUID değerini kullanın.

> [!NOTE]
> VSCT dosyasının semboller bölümünü değiştirirseniz bu bildirimleri eşleşecek şekilde de değiştirmeniz gerekir. Ayrıca, Package.tt içindeki sürüm numarasını da artırmanız gerekir

 Menü komutlarınızı bu komut kümesinin bir parçası olarak kaydedin. Diyagram başlatıldığında `GetMenuCommands()` bir kez çağrılır:

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
 DSL 'yi Visual Studio 'nun deneysel bir örneğinde derleyin ve çalıştırın. Komutun, belirttiğiniz durumlarda kısayol menüsünde görünmesi gerekir.

### <a name="to-exercise-the-command"></a>Komutu uygulamak için

1. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür**' e tıklayın.

2. Çözümü yeniden derlemek için **F5** tuşuna basın ve deneysel derlemede alana özgü dilde hata ayıklamaya başlayın.

3. Deneysel derlemede, örnek bir diyagram açın.

4. Komutun doğru şekilde etkinleştirildiğini veya devre dışı bırakıldığını ve seçili öğeye bağlı olarak uygun şekilde görüntülendiğini veya gizlendiğini doğrulamak için diyagramdaki çeşitli öğelere sağ tıklayın.

## <a name="troubleshoot"></a>Sorun giderme

**Komut menüde görünmüyor:**

- Bu komut, DSL paketini yükleyene kadar yalnızca Visual Studio 'daki hata ayıklama örneklerinde görünür. Daha fazla bilgi için bkz. [etki alanına özgü dil çözümlerini dağıtma](msi-and-vsix-deployment-of-a-dsl.md).

- Deneysel örneklerinizin bu DSL için doğru dosya adı uzantısına sahip olduğundan emin olun. Dosya adı uzantısını denetlemek için, Visual Studio 'nun ana örneğinde DslDefinition. dsl dosyasını açın. Ardından DSL Gezgini ' nde düzenleyici düğümüne sağ tıklayın ve ardından Özellikler ' e tıklayın. Özellikler penceresi FileExtension özelliğini inceleyin.

- [Paket sürüm numarasını artırdınız](#version)mı?

- OnStatus yönteminizin başlangıcında bir kesme noktası ayarlayın. Diyagramın herhangi bir kısmına sağ tıkladığınızda bu, kesmesi gerekir.

**OnStatus yöntemi çağrılmadı**:

- CommandSet kodunuzda GUID 'lerin ve kimliklerin Commands. vsct 'ın semboller bölümünde olanlarla eşleştiğinden emin olun.

- Commands. vsct içinde, her üst düğümdeki GUID ve KIMLIğIN doğru üst grubu tanımladığınızdan emin olun.

- Bir Visual Studio komut isteminde devenv/rootsuffix exp/setupyazın. Sonra Visual Studio 'nun hata ayıklama örneğini yeniden başlatın.

- Komutun doğrulanması için OnStatus metodunu adım adım yapın. Görünür ve komut. Etkin özelliği true olarak ayarlandı.

**Yanlış menü metni görünüyor veya komut yanlış yerde görünüyor**:

- GUID ve ID birleşiminin bu komuta özgü olduğundan emin olun.

- Paketin önceki sürümlerini kaldırdığınızdan emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Nasıl Yapılır: Standart Menü Komutunu Değiştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Etki Alanına Özgü Dil Çözümlerini Dağıtma](msi-and-vsix-deployment-of-a-dsl.md)
- [Örnek kod: devre şemaları](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]