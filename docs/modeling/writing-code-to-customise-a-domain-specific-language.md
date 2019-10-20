---
title: Bir Etki Alanına Özgü Dili Özelleştirme
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c8a65b19baeb3a03c8ada039bce354140aecbf6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666877"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>Alana Özgü Dil Özelleştirmek için Kod yazma

Bu bölümde, etki alanına özgü bir dilde bir modele erişmek, değiştirmek veya model oluşturmak için özel kodun nasıl kullanılacağı gösterilmektedir.

DSL ile birlikte çalışarak kod yazabileceğiniz birkaç bağlam vardır:

- **Özel komutlar.** Kullanıcıların diyagram üzerinde sağ tıklayıp, modeli değiştirebilecek bir komut oluşturabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

- **Doğrulamasına.** Modelin doğru durumda olduğunu doğrulayan bir kod yazabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü bir dilde doğrulama](../modeling/validation-in-a-domain-specific-language.md).

- **Varsayılan davranışı geçersiz kılma.** DslDefinition. dsl 'den oluşturulan kodun birçok özelliğini değiştirebilirsiniz. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).

- **Metin dönüştürme.** Bir modele erişen ve bir metin dosyası (örneğin, program kodu oluşturmak için) oluşturan kod içeren metin şablonları yazabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü dilden kod oluşturma](../modeling/generating-code-from-a-domain-specific-language.md).

- **Diğer Visual Studio uzantıları.** Modelleri okuyan ve değiştiren ayrı VSıX uzantıları yazabilirsiniz. Daha fazla bilgi için bkz [. nasıl yapılır: program kodunda dosyadan model açma](../modeling/how-to-open-a-model-from-file-in-program-code.md)

DslDefinition. dsl içinde tanımladığınız sınıfların örnekleri, *bellek Içi depo* (IMS) veya *Mağaza*adlı bir veri yapısında tutulur. Bir DSL 'de tanımladığınız sınıflar her zaman oluşturucuya bağımsız değişken olarak bir depo alır. Örneğin, DSL 'niz örnek adlı bir sınıf tanımlıyorsa:

`Example element = new Example (theStore);`

nesnelerin depoda tutulması (yalnızca sıradan nesneler yerine) birçok avantaj sağlar.

- **İşlemler**. Bir dizi ilişkili değişikliği bir işlem halinde gruplandırabilirsiniz:

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     Değişiklikler sırasında bir özel durum oluşursa, son COMMIT () gerçekleştirilmemesi için mağaza önceki durumuna sıfırlanır. Bu, hataların modeli tutarsız bir durumda bırakmadığından emin olmanıza yardımcı olur. Daha fazla bilgi için bkz. [program kodunda modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **İkili ilişkiler**. İki sınıf arasında bir ilişki tanımlarsanız, her iki uçta da örnek, diğer uca giden bir özelliğe sahiptir. İki bitiş her zaman eşitlenir. Örneğin, üst ve alt öğe adlı rollerle bir Parenthood ilişkisi tanımlarsanız şunu yazabilirsiniz:

     `John.Children.Add(Mary)`

     Aşağıdaki ifadelerden her ikisi de doğrudur:

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     Yazarak aynı etkiyi de elde edebilirsiniz:

     `Mary.Parents.Add(John)`

     Daha fazla bilgi için bkz. [program kodunda modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

- **Kurallar ve olaylar**. Belirtilen değişiklikler yapıldığında başlatılan kuralları tanımlayabilirsiniz. Kurallar, örneğin diyagramdaki şekilleri mevcut model öğeleriyle güncel tutmak için kullanılır. Daha fazla bilgi için bkz. [değişiklikleri yanıtlama ve yayma](../modeling/responding-to-and-propagating-changes.md).

- **Serileştirme**. Mağaza, içerdiği nesneleri bir dosyaya seri hale getirmek için standart bir yol sağlar. Serileştirme ve seri durumdan çıkarma kurallarını özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Dosya depolamayı ve XML Serileştirmeyi özelleştirme](../modeling/customizing-file-storage-and-xml-serialization.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)