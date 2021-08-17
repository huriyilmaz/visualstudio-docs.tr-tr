---
title: DSL'de standart menü komutunu değiştirme
description: DSL'niz içinde otomatik olarak tanımlanan bazı standart komutların davranışını nasıl değiştiryebilirsiniz?
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
ms.openlocfilehash: cb575eb52e9a95d2ba548659ec8d265605f5e64d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055464"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dilde Standart Menü Komutunu Değiştirme

DSL'niz içinde otomatik olarak tanımlanan bazı standart komutların davranışını değiştirebilirsiniz. Örneğin, hassas bilgileri **dışlamak** için Kes'i değiştirebilirsiniz. Bunu yapmak için, bir komut kümesi sınıfındaki yöntemleri geçersiz kılar. Bu sınıflar, DslPackage projesinde CommandSet.cs dosyasında tanımlanır ve 'den <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> türetilen.

> [!NOTE]
> Kendi menü komutlarınızı oluşturmak için bkz. [Nasıl kullanılır: Kısayol Menüsüne Komut Ekleme.](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

## <a name="what-commands-can-you-modify"></a>Hangi komutları değiştirebilirsiniz?

### <a name="to-discover-what-commands-you-can-modify"></a>Hangi komutları değiştirebilirsiniz?

1. `DslPackage`Projesinde'i `GeneratedCode\CommandSet.cs` açın. Bu C# dosyası, Çözüm Gezgini bir yan kuruluşu olarak `CommandSet.tt` bulunabilir.

2. Bu dosyada adları " " ile biten sınıfları `CommandSet` bulun, örneğin ve `Language1CommandSet` `Language1ClipboardCommandSet` .

3. Her komut kümesi sınıfında " `override` " yazın ve ardından bir boşluk yazın. IntelliSense geçersiz kılabilirsiniz yöntemlerin listesini gösterir. Her komutun adları " " ve " " " şeklinde başlayan `ProcessOnStatus` bir yöntem çifti `ProcessOnMenu` vardır.

4. Hangi komut kümesi sınıflarının değiştirmek istediğiniz komutu içerdiğini unutmayın.

5. Düzenlemelerinizi kaydetmeden dosyayı kapatın.

    > [!NOTE]
    > Normalde, oluşturulan dosyaları düzenlemeniz gerekir. Dosyalar bir sonraki oluşturmada tüm düzenlemeler kaybedilir.

## <a name="extend-the-appropriate-command-set-class"></a>Uygun komut kümesi sınıfını genişletme

Komut kümesi sınıfının kısmi bildirimini içeren yeni bir dosya oluşturun.

### <a name="to-extend-the-command-set-class"></a>Komut Kümesi sınıfını genişletmek için

1. Bu Çözüm Gezgini DslPackage projesinde GeneratedCode klasörünü açın, sonra CommandSet.tt'nin altına bakın ve oluşturulan CommandSet.cs dosyasını açın. Burada tanımlanan ilk sınıfın ad alanını ve adını not ekleyin. Örneğin, şunları görebilir:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. **DslPackage içinde** Özel Kod adlı bir **klasör oluşturun.** Bu klasörde adlı yeni bir sınıf dosyası `CommandSet.cs` oluşturun.

3. Yeni dosyada, oluşturulan kısmi sınıfla aynı ad alanına ve adına sahip kısmi bir bildirim yazın. Örnek:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Yeni dosyayı oluşturmak için sınıf dosyası şablonunu kullandıysanız, hem ad alanını hem de sınıf adını düzeltmeniz gerekir.

## <a name="override-the-command-methods"></a>Komut yöntemlerini geçersiz kılma

Çoğu komutun iki ilişkili yöntemi vardır: ... gibi bir adı `ProcessOnStatus` olan yöntemi komutun görünür ve etkin olup olmadığını belirler. Kullanıcı diyagrama sağ tıkladığında çağrılır ve hızlı bir şekilde yürütülerek değişiklik yapmaları gerekir. `ProcessOnMenu`... kullanıcı komutuna tıkladığında çağrılır ve komutun işlevini gerçekleştirmesi gerekir. Bu yöntemlerden birini veya her ikisini geçersiz kılmak istiyor olabilir.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Komut bir menüde görüntülendiğinde değiştirmek için

ProcessOnStatus'u Geçersiz Kıl... Yöntem. Bu yöntem, MenuCommand parametresinin Visible ve Enabled özelliklerini ayarlamalı. Genellikle komut buna bakarak. Komutun seçili öğeler için geçerli olup olmadığını belirlemek için CurrentSelection ve ayrıca komutun geçerli durumlarına uygulanıp uygulanamayacaklarını belirlemek için özelliklerine bakabilirsiniz.

Genel bir kılavuz olarak Visible özelliği hangi öğelerin seçilecekleri tarafından belirlenecektir. Komutun menüde siyah mı yoksa gri mi görüntülendiğinden belirleyen Enabled özelliği, seçimin geçerli durumuna bağlı olmalıdır.

Aşağıdaki örnek, kullanıcı birden fazla şekil seçtikten sonra Sil menü öğesini devre dışı bırakıyor.

> [!NOTE]
> Bu yöntem, komutun bir tuş vuruşu ile kullanılabilir olup olmadığını etkilemez. Örneğin, Sil menü öğesinin devre dışı bırakılması komutun Sil anahtarı aracılığıyla çağrılması engellemez.

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

Kaygılanmazken tüm durumlarla ve ayarlarla başa olmak için ilk olarak temel yöntemi çağırmayı iyi bir yöntemdir.

ProcessOnStatus yöntemi, Store'da öğe oluşturma, silme veya güncelleştirme işlemiyle ilgili değildir.

### <a name="to-change-the-behavior-of-the-command"></a>Komutun davranışını değiştirmek için

Override the ProcessOnMenu... Yöntem. Aşağıdaki örnek, Silme anahtarını kullanarak bile kullanıcının aynı anda birden fazla öğeyi silmesini önler.

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

Kodunuz Mağazada öğe veya bağlantı oluşturma, silme veya güncelleştirme gibi değişiklikler yaparsa, bunu bir işlem içinde gerçekleştirebilirsiniz. Daha fazla bilgi için [bkz. Model öğelerini oluşturma ve güncelleştirme.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

### <a name="write-the-code-of-the-methods"></a>Yöntemlerin kodunu yazma

Aşağıdaki parçalar genellikle bu yöntemlerde yararlıdır:

- `this.CurrentSelection`. Kullanıcının sağ tıklamış olduğu şekil her zaman bu şekil ve bağlayıcı listesine eklenir. Kullanıcı diyagramın boş bir parçasına tıklarsa Diyagram listenin tek üyesidir.

- `this.IsDiagramSelected()` - `true` kullanıcı diyagramın boş bir parçasına tıklamışsa.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` - kullanıcı birden çok şekil seçmedi

- `this.SingleSelection` - kullanıcının sağ tıklamış olduğu şekil veya diyagram

- `shape.ModelElement as MyLanguageElement` - bir şekille temsil edilen model öğesi.

Öğeden öğeye nasıl gidilen ve nesne ve bağlantı oluşturma hakkında daha fazla bilgi için bkz. [Program Kodunda Modelde](../modeling/navigating-and-updating-a-model-in-program-code.md)Gezinme ve Güncelleştirme.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.Design.MenuCommand>
- [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Nasıl yapılır: Kısayol Menüsüne Komut Ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML Şeması Başvurusu](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK - Devre Diyagramları örneği. Kapsamlı DSL Özelleştirmesi](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
