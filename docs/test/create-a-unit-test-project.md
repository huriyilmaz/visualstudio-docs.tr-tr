---
title: Birim testi projesi oluşturma
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 313083090c94c94f4e196e87f3bf6cf6df36e118
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565259"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri genellikle test altındaki kodun yapısını yansıttır. Örneğin, üründeki her kod projesi için bir birim test projesi oluşturulur. Test projesi üretim koduyla aynı çözümde olabilir veya ayrı bir çözümde olabilir. Bir çözümde birden çok birim test projesi olabilir.

> [!NOTE]
> Yerel kod ve test proje yapısı için birim testlerinin konumu, bu makalede açıklanan yapıdan farklı olabilir. Daha fazla bilgi için [C/C++ için yazı birimi testlerine](writing-unit-tests-for-c-cpp.md)bakın.

## <a name="to-create-a-unit-test-project"></a>Birim test projesi oluşturmak için

1. **Dosya** menüsünde **Yeni** > **Proje'yi**seçin veya **Ctrl**+**Shift**+**N**tuşuna basın.

::: moniker range="vs-2017"

2. Yeni **Proje** iletişim kutusunda, **Yüklü** düğümgenişletmek, test projeniz için kullanmak istediğiniz dili seçin ve sonra **Test'i**seçin.

3. MSTest **Test Project** veya **NUnit Test Project**gibi kullanmak istediğiniz test çerçevesi için proje şablonu seçin. Projeyi adlandırın ve **ardından Tamam'ı**seçin.

   ![Visual Studio 2017'de test proje şablonları](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **bir proje oluştur** sayfasında, **birim testini** arama kutusuna yazın. Örneğin **MSTest Test Project** veya **NUnit Test Project**gibi kullanmak istediğiniz test çerçevesi için proje şablonu seçin ve ardından **İleri'yi**seçin.

   ![Visual Studio 2019'da test proje şablonları](media/vs-2019/test-project-templates.png)

3. Yeni **proje sayfanızı Yapılandır'da, projeniz** için bir ad girin ve ardından **Oluştur'u**seçin.

::: moniker-end

4. Birim test projenizde, test altındaki koda bir başvuru ekleyin. Aynı çözümdeki bir kod projesine başvuru eklemek için:

   1. **Çözüm Gezgini'nde**test projesini seçin.

   2. **Proje** menüsünde **Referans Ekle'yi**seçin.

   3. **Başvuru Yöneticisi'nde,** **Projeler**altında **Çözüm** düğümünü seçin. Sınamak istediğiniz kod projesini seçin ve ardından **Tamam'ı**seçin.

   Sınamak istediğiniz kod başka bir konumdaysa, başvuru ekleme hakkında bilgi almak için [projede başvuruları yönetme'ye](../ide/managing-references-in-a-project.md) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki bölümlerden birine bakın:

**Yazma ünitesi testleri**

- [Birim kodunuzu test edin](../test/unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Çalışma ünitesi testleri**

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
