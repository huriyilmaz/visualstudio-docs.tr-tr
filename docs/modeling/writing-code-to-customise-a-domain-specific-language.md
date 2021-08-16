---
title: Bir Etki Alanına Özgü Dili Özelleştirme
description: Etki alanına özgü bir dilde (DSL) modele erişmek, değiştirmek veya model oluşturmak için özel kod kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d2cf06916c4dd149aa948c71d5f72eff307fcd45ea45227e91f89528e00a3fd9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398027"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Alana Özgü Dil Özelleştirmek için Kod yazma

Bu bölümde, etki alanına özgü bir dilde modele erişmek, değiştirmek veya oluşturmak için özel kodu nasıl kullanabileceğiniz açıktır.

DSL ile çalışan kod yazabilirsiniz çeşitli bağlamlar vardır:

- **Özel komutlar.** Kullanıcıların diyagrama sağ tıklayarak çağıran ve modeli değiştiren bir komut oluşturabilirsiniz. Daha fazla bilgi için, [bkz. How to: Add a Command to the Shortcut Menu](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Doğrulama.** Modelin doğru durumda olduğunu doğrular kodu yazabilirsiniz. Daha fazla bilgi için, [bkz. Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

- **Varsayılan davranışı geçersiz kılma.** DslDefinition.dsl'den oluşturulan kodun birçok yönlerini değiştirebilirsiniz. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)

- **Metin Dönüştürme.** Modele erişen ve bir metin dosyası oluşturan kod içeren metin şablonları (örneğin, program kodu oluşturmak için) yazabilirsiniz. Daha fazla bilgi için [bkz. Domain-Specific Dilinden Kod Oluşturma.](../modeling/generating-code-from-a-domain-specific-language.md)

- **Diğer Visual Studio uzantıları.** Modelleri okumak ve değiştirmek için ayrı VSIX uzantıları yazabilirsiniz. Daha fazla bilgi için, [bkz. How to: Open a Model from File in Program Code](../modeling/how-to-open-a-model-from-file-in-program-code.md)

DslDefinition.dsl içinde tanımladığınız sınıfların örnekleri, Bellek Içinde Depo  (IMS) veya Depolama adlı bir veri yapısında *tutulur.* DSL'de tanımladığınız sınıflar her zaman oluşturucu için bağımsız değişken olarak bir Store alır. Örneğin, DSL'niz Örnek adlı bir sınıf tanımlarsa:

`Example element = new Example (theStore);`

Nesneleri Depoda tutmak (sıradan nesneler gibi değil) çeşitli avantajlar sağlar.

- **İşlemler**. Bir dizi ilgili değişikliği bir işlemde grup haline dönüştüresiniz:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Değişiklikler sırasında bir özel durum oluşursa, son Commit() işlemi gerçekleştirilmazsa, Depo önceki durumuna sıfırlanır. Bu, hataların modeli tutarsız bir durumda bırakmamanıza yardımcı olur. Daha fazla bilgi için [bkz. Program Kodunda Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

- **İkili ilişkiler.** İki sınıf arasında bir ilişki tanımlarsanız, her iki uçta da örneklerin diğer sona gitmek için bir özelliği vardır. İki uç her zaman eşitlenir. Örneğin, Parents ve Children adlı rollerle bir üst öğe ilişkisi tanımlarsanız şunları yazabilir:

     `John.Children.Add(Mary)`

     Aşağıdaki ifadelerin her ikisi de doğrudur:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Ayrıca şunları yazarak da aynı etkiyi elde etmek için:

     `Mary.Parents.Add(John)`

     Daha fazla bilgi için [bkz. Program Kodunda Modelde Gezinme ve Güncelleştirme.](../modeling/navigating-and-updating-a-model-in-program-code.md)

- **Kurallar ve Olaylar.** Belirtilen değişiklikler her yapıldı mı, bu kuralları tanımlayabilirsiniz. Kurallar, örneğin diyagramda yer alan şekilleri mevcut model öğeleriyle güncel tutmak için kullanılır. Daha fazla bilgi için [bkz. Değişiklikleri Yanıt verme ve Yayma.](../modeling/responding-to-and-propagating-changes.md)

- **Seri hale getirme**. Depo, içerdiği nesneleri bir dosyaya seri hale getirmenin standart bir yolunu sağlar. Seri hale getirme ve seriden seriden serileştirme için kuralları özelleştirebilirsiniz. Daha fazla bilgi için, [bkz. Dosya Depolama ve XML Serileştirme özelleştirme.](../modeling/customizing-file-storage-and-xml-serialization.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)