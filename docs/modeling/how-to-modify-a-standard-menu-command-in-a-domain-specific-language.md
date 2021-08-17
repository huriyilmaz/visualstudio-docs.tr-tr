---
title: DSL 'de standart menü komutunu değiştirme
description: DSL 'niz içinde otomatik olarak tanımlanan bazı standart komutlardan oluşan davranışı nasıl değiştirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 744c52dc23a7f144a42c371abc7faab520c58226f488a04540bd590c8965c2d2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121428958"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dilde Standart Menü Komutunu Değiştirme

DSL 'niz içinde otomatik olarak tanımlanan bazı standart komutlardan oluşan davranışı değiştirebilirsiniz. Örneğin, hassas bilgileri dışladığı için **kesmeyi** değiştirebilirsiniz. Bunu yapmak için, komut kümesi sınıfındaki yöntemleri geçersiz kılabilirsiniz. Bu sınıflar, DslPackage projesindeki CommandSet. cs dosyasında tanımlanır ve öğesinden türetilir <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

> [!NOTE]
> Kendi Menü komutlarınızı oluşturmak isterseniz, bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>Hangi komutlara değişiklik yapabilirsiniz?

### <a name="to-discover-what-commands-you-can-modify"></a>Değiştirebileceğiniz komutları öğrenmek için

1. `DslPackage`Projesinde öğesini açın `GeneratedCode\CommandSet.cs` . Bu C# dosyası, ' ın bir yan kuruluşu olarak Çözüm Gezgini bulunabilir `CommandSet.tt` .

2. Adları "" ile biten bu dosyadaki sınıfları bulur `CommandSet` , örneğin `Language1CommandSet` ve `Language1ClipboardCommandSet` .

3. Her komut kümesi sınıfında, "" yazın ve `override` ardından bir boşluk girin. IntelliSense, geçersiz kılabileceğiniz yöntemlerin bir listesini gösterir. Her komutun adı " `ProcessOnStatus` " ve "" olan bir çift yöntemi vardır `ProcessOnMenu` .

4. Komut kümesi sınıflarından hangilerinin değiştirmek istediğiniz komutu içerdiğini göz önünde görürsünüz.

5. Düzenlemelerinizi kaydetmeden dosyayı kapatın.

    > [!NOTE]
    > Normalde, oluşturulan dosyaları düzenlememelisiniz. Dosyaların bir sonraki oluşturulışında tüm düzenlemeler kaybedilir.

## <a name="extend-the-appropriate-command-set-class"></a>Uygun komut kümesi sınıfını Genişlet

Komut kümesi sınıfının kısmi bildirimini içeren yeni bir dosya oluşturun.

### <a name="to-extend-the-command-set-class"></a>Komut kümesi sınıfını genişletmek için

1. Çözüm Gezgini, DslPackage projesinde, GeneratedCode klasörünü açın ve ardından CommandSet.tt ' ın altında yazıp oluşturulan CommandSet. cs dosyasını açın. Ad alanını ve burada tanımlanan ilk sınıfın adını unutmayın. Örneğin, şu şekilde karşılaşabilirsiniz:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. **DslPackage**' de, **özel kod** adlı bir klasör oluşturun. Bu klasörde adlı yeni bir sınıf dosyası oluşturun `CommandSet.cs` .

3. Yeni dosyada, oluşturulan kısmi sınıfla aynı ad alanına ve ada sahip kısmi bir bildirim yazın. Örnek:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Yeni dosyayı oluşturmak için sınıf dosya şablonunu kullandıysanız, hem ad alanını hem de sınıf adını düzeltmeniz gerekir.

## <a name="override-the-command-methods"></a>Komut yöntemlerini geçersiz kılın

Çoğu komutun iki ilişkili yöntemi vardır:... gibi bir ada sahip Yöntem `ProcessOnStatus` komutun görünür ve etkin olup olmayacağını belirler. Kullanıcı diyagrama sağ tıkladığında çağrılır ve hızlı bir şekilde yürütülecektir ve hiçbir değişiklik yapmamalıdır. `ProcessOnMenu`... Kullanıcı komuta tıkladığında çağrılır ve komutun işlevini gerçekleştirmesi gerekir. Bu yöntemlerin birini ya da her ikisini de geçersiz kılmak isteyebilirsiniz.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Komutun bir menüde göründüğü zaman değiştirmek için

ProcessOnStatus öğesini geçersiz kıl... yöntemidir. Bu yöntem, parametrenin MenuCommand öğesinin Visible ve Enabled özelliklerini ayarlamanız gerekir. Genellikle komut buna bakar. Geçerli seçim komutun seçili öğelere uygulanıp uygulanmadığını belirleme ve ayrıca, komutun geçerli durumunda uygulanıp uygulanamayacağını tespit etmek için özelliklerine de bakabilirler.

Genel bir kılavuz olarak Visible özelliği, öğelerin seçilmesinin belirlenmesi gerekir. Komutun menüdeki siyah veya gri görünüp görünmeyeceğini belirleyen Enabled özelliği, seçimin geçerli durumuna bağlıdır.

Aşağıdaki örnek, Kullanıcı birden fazla şekil seçtiği zaman sil menü öğesini devre dışı bırakır.

> [!NOTE]
> Bu yöntem, komutun bir tuş vuruşu aracılığıyla kullanılabilir olup olmadığını etkilemez. Örneğin, sil menü öğesini devre dışı bırakmak komutun silme anahtarı aracılığıyla çağrılmasını engellemez.

```csharp
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

İlk olarak temel yöntemi çağırmak, ilgilenmekte olduğunuz tüm durum ve ayarlarla başa çıkmak için iyi bir uygulamadır.

ProcessOnStatus yöntemi depodaki öğeleri oluşturmamalıdır, silmemelidir veya güncelleştirmemelidir.

### <a name="to-change-the-behavior-of-the-command"></a>Komutun davranışını değiştirmek için

ProcessOnMenu 'yi geçersiz kıl... yöntemidir. Aşağıdaki örnek, silme anahtarını kullanarak kullanıcının aynı anda birden fazla öğeyi silmesini engeller.

```csharp
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

Kodunuz depoda değişiklik yapıyorsa (örneğin, öğeleri veya bağlantıları oluşturma, silme veya güncelleştirme), bunu bir işlemin içinde yapmanız gerekir. Daha fazla bilgi için bkz. [model öğeleri oluşturma ve güncelleştirme](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="write-the-code-of-the-methods"></a>Yöntemlerin kodunu yazma

Aşağıdaki parçalar genellikle bu yöntemler içinde yararlı olur:

- `this.CurrentSelection`. Kullanıcının sağ tıklamış olduğu şekil, bu şekil ve bağlayıcılar listesine her zaman dahildir. Kullanıcı diyagramın boş bir kısmına tıkladığında diyagram, listenin tek üyesidir.

- `this.IsDiagramSelected()` - `true` Kullanıcı diyagramın boş bir kısmına tıklamıştır.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` -Kullanıcı birden çok şekil seçmedi

- `this.SingleSelection` -kullanıcıya sağ tıklamış olan şekil veya diyagram

- `shape.ModelElement as MyLanguageElement` -bir şekil tarafından temsil edilen model öğesi.

Öğesinden öğeye nasıl gidebileceğiniz ve nesnelerin ve bağlantıların nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.Design.MenuCommand>
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Nasıl yapılır: Kısayol Menüsüne Komut Ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK-devre şemaları örneği. Kapsamlı DSL özelleştirmesi](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
