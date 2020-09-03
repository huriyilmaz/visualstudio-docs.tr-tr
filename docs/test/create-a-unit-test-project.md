---
title: Birim testi projesi oluşturma
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ffa19fb9dc49d6286ef3f54c51d89043445f18ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288721"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri genellikle test altındaki kodun yapısını yansıtır. Örneğin, üründeki her kod projesi için bir birim testi projesi oluşturulur. Test projesi üretim koduyla aynı çözümde olabilir veya ayrı bir çözümde olabilir. Bir çözümde birden çok birim testi projesine sahip olabilirsiniz.

> [!NOTE]
> Yerel kod ve test projesi yapısına yönelik birim testlerinin konumu, bu makalede açıklanan yapıdan farklı olabilir. Daha fazla bilgi için bkz. [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için

1. **Dosya** menüsünde **Yeni**  >  **Proje**' yi seçin veya **CTRL** + **SHIFT** + **N**tuşuna basın.

::: moniker range="vs-2017"

2. **Yeni proje** iletişim kutusunda, **yüklü** düğümünü genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından **Test**' i seçin.

3. Kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest test projesi** veya **NUnit test projesi**. Projeyi adlandırın ve ardından **Tamam**' ı seçin.

   ![Visual Studio 2017 ' de test projesi şablonları](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni proje oluştur** sayfasında, arama kutusuna **birim testi** yazın. Kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest test projesi** veya **NUnit test projesi**ve sonra **İleri**' yi seçin.

   ![Visual Studio 2019 ' de test projesi şablonları](media/vs-2019/test-project-templates.png)

3. **Yeni projenizi yapılandırın** sayfasında, projeniz için bir ad girin ve ardından **Oluştur**' u seçin.

::: moniker-end

4. Birim testi projenizde, test altındaki koda bir başvuru ekleyin. Aynı çözümde bir kod projesine bir başvuru eklemek için:

   1. **Çözüm Gezgini**' de test projesi seçin.

   2. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.

   3. **Başvuru Yöneticisi**' nde **Projeler**altındaki **çözüm** düğümünü seçin. Test etmek istediğiniz kod projesini seçin ve ardından **Tamam**' ı seçin.

   Test etmek istediğiniz kod başka bir konumdaysa, başvuru ekleme hakkında bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md) .

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki bölümlerden birine bakın:

**Birim testlerini yazma**

- [Kodunuzun birim testi](../test/unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Birim testlerini çalıştırma**

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
