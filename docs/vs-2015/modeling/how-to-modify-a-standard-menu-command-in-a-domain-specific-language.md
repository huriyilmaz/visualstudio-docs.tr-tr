---
title: 'Nasıl yapılır: etki alanına özgü bir dilde standart menü komutunu değiştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 989367d395abb56e4f57c4aa2694b5f4ef17fb6e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300873"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Nasıl yapılır: Etki Alanına Özgü bir Dilde Standart Menü Komutunu Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 'niz içinde otomatik olarak tanımlanan bazı standart komutlardan oluşan davranışı değiştirebilirsiniz. Örneğin, hassas bilgileri dışladığı için **kesmeyi** değiştirebilirsiniz. Bunu yapmak için, komut kümesi sınıfındaki yöntemleri geçersiz kılabilirsiniz. Bu sınıflar, DslPackage projesindeki CommandSet.cs dosyasında tanımlanır ve <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>türetilir.

 Özet ' te, bir komutu değiştirmek için:

1. [Değiştirebileceğiniz komutları öğrenin](#what).

2. [Uygun komut kümesi sınıfının kısmi bildirimini oluşturun](#extend).

3. Komut için [ProcessOnStatus ve ProcessOnMenu yöntemlerini geçersiz kılın](#override) .

   Bu konuda bu yordam açıklanmaktadır.

> [!NOTE]
> Kendi Menü komutlarınızı oluşturmak isterseniz, bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what"></a>Hangi komutlara değişiklik yapabilirsiniz?

#### <a name="to-discover-what-commands-you-can-modify"></a>Değiştirebileceğiniz komutları öğrenmek için

1. `DslPackage` projesinde, `GeneratedCode\CommandSet.cs`açın. Bu C# dosya, `CommandSet.tt`bir yan kuruluşu olarak Çözüm Gezgini bulunabilir.

2. Bu dosyada adları "`CommandSet`" ile biten, örneğin `Language1CommandSet` ve `Language1ClipboardCommandSet`olan sınıfları bulun.

3. Her komut kümesi sınıfında, "`override`" yazın ve ardından bir boşluk girin. IntelliSense, geçersiz kılabileceğiniz yöntemlerin bir listesini gösterir. Her komutun adları "`ProcessOnStatus`" ve "`ProcessOnMenu`" başlayan bir çift yöntemi vardır.

4. Komut kümesi sınıflarından hangilerinin değiştirmek istediğiniz komutu içerdiğini göz önünde görürsünüz.

5. Düzenlemelerinizi kaydetmeden dosyayı kapatın.

    > [!NOTE]
    > Normalde, oluşturulan dosyaları düzenlememelisiniz. Dosyaların bir sonraki oluşturulışında tüm düzenlemeler kaybedilir.

## <a name="extend"></a>Uygun komut kümesi sınıfını Genişlet
 Komut kümesi sınıfının kısmi bildirimini içeren yeni bir dosya oluşturun.

#### <a name="to-extend-the-command-set-class"></a>Komut kümesi sınıfını genişletmek için

1. Çözüm Gezgini, DslPackage projesinde, GeneratedCode klasörünü açın ve ardından CommandSet.tt ' ın altında, oluşturulan dosya CommandSet.cs ' nı açın. Ad alanını ve burada tanımlanan ilk sınıfın adını unutmayın. Örneğin, şu şekilde karşılaşabilirsiniz:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. **DslPackage**' de, **özel kod**adlı bir klasör oluşturun. Bu klasörde, `CommandSet.cs`adlı yeni bir sınıf dosyası oluşturun.

3. Yeni dosyada, oluşturulan kısmi sınıfla aynı ad alanına ve ada sahip kısmi bir bildirim yazın. Örneğin:

    ```
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Göz önünde** Yeni dosyayı oluşturmak için sınıf dosya şablonunu kullandıysanız, hem ad alanını hem de sınıf adını düzeltmeniz gerekir.

## <a name="override"></a>Komut yöntemlerini geçersiz kılın
 Çoğu komutun iki ilişkili yöntemi vardır: `ProcessOnStatus`gibi bir ada sahip yöntem... komutun görünür ve etkin olup olmayacağını belirler. Kullanıcı diyagrama sağ tıkladığında çağrılır ve hızlı bir şekilde yürütülecektir ve hiçbir değişiklik yapmamalıdır. `ProcessOnMenu`... Kullanıcı komuta tıkladığında çağrılır ve komutun işlevini gerçekleştirmesi gerekir. Bu yöntemlerin birini ya da her ikisini de geçersiz kılmak isteyebilirsiniz.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Komutun bir menüde göründüğü zaman değiştirmek için
 ProcessOnStatus öğesini geçersiz kıl... yöntemidir. Bu yöntem, parametrenin MenuCommand öğesinin Visible ve Enabled özelliklerini ayarlamanız gerekir. Genellikle komut buna bakar. Geçerli seçim komutun seçili öğelere uygulanıp uygulanmadığını belirleme ve ayrıca, komutun geçerli durumunda uygulanıp uygulanamayacağını tespit etmek için özelliklerine de bakabilirler.

 Genel bir kılavuz olarak Visible özelliği, öğelerin seçilmesinin belirlenmesi gerekir. Komutun menüdeki siyah veya gri görünüp görünmeyeceğini belirleyen Enabled özelliği, seçimin geçerli durumuna bağlıdır.

 Aşağıdaki örnek, Kullanıcı birden fazla şekil seçtiği zaman sil menü öğesini devre dışı bırakır.

> [!NOTE]
> Bu yöntem, komutun bir tuş vuruşu aracılığıyla kullanılabilir olup olmadığını etkilemez. Örneğin, sil menü öğesini devre dışı bırakmak komutun silme anahtarı aracılığıyla çağrılmasını engellemez.

```
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

```
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

### <a name="writing-the-code-of-the-methods"></a>Yöntemlerin kodunu yazma
 Aşağıdaki parçalar genellikle bu yöntemler içinde yararlı olur:

- `this.CurrentSelection`. Kullanıcının sağ tıklamış olduğu şekil, bu şekil ve bağlayıcılar listesine her zaman dahildir. Kullanıcı diyagramın boş bir kısmına tıkladığında diyagram, listenin tek üyesidir.

- Kullanıcı diyagramın boş bir bölümüne tıklandığı `true`  - `this.IsDiagramSelected()`.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`-Kullanıcı birden çok şekil seçmedi

- `this.SingleSelection`-kullanıcıya sağ tıklamış olan şekil veya diyagram

- `shape.ModelElement as MyLanguageElement`-bir şekil tarafından temsil edilen model öğesi.

  Öğesinden öğeye nasıl gidebileceğiniz ve nesnelerin ve bağlantıların nasıl oluşturulacağı hakkında daha fazla bilgi için bkz. [Program kodundaki bir modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [bir etki alanına özgü dil özelleştirmek Için kod yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md) <xref:System.ComponentModel.Design.MenuCommand> [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md) [Izlenecek yol: seçili bağlantılardan bilgileri alma](../misc/walkthrough-getting-information-from-a-selected-link.md) [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md) [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML şema başvurusu](../extensibility/vsct-xml-schema-reference.md)
