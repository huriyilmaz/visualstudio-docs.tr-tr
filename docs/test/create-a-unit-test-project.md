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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565259"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri, test altındaki kod yapısına genellikle yansıtır. Örneğin, her kod projesini ürün için birim testi projesi oluşturulması. Ayrı bir çözümde de olabilir veya üretim kodu aynı çözümde test projesini olabilir. Test projeleri bir çözümde birden çok birim olabilir.

> [!NOTE]
> Yerel kod ve test projesi yapısına yönelik birim testlerinin konumu, bu makalede açıklanan yapıdan farklı olabilir. Daha fazla bilgi için [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için

1. **Dosya** menüsünde **Yeni** > **Proje**' yi seçin veya **CTRL**+**SHIFT**+**N**tuşlarına basın.

::: moniker range="vs-2017"

2. İçinde **yeni proje** iletişim kutusunda **yüklü** düğümü, test projeniz için kullanın ve ardından istediğiniz dili seçin **Test**.

3. Kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest test projesi** veya **NUnit test projesi**. Projeyi adlandırın ve ardından **Tamam**' ı seçin.

   ![Visual Studio 2017 ' de test projesi şablonları](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni proje oluştur** sayfasında, arama kutusuna **birim testi** yazın. Kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest test projesi** veya **NUnit test projesi**ve sonra **İleri**' yi seçin.

   ![Visual Studio 2019 ' de test projesi şablonları](media/vs-2019/test-project-templates.png)

3. **Yeni projenizi yapılandırın** sayfasında, projeniz için bir ad girin ve ardından **Oluştur**' u seçin.

::: moniker-end

4. Birim test projenizde, test edilen kod bir başvuru ekleyin. Aynı çözümde bir kod projesine bir başvuru eklemek için:

   1. **Çözüm Gezgini**' de test projesi seçin.

   2. Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.

   3. **Başvuru Yöneticisi**' nde **Projeler**altındaki **çözüm** düğümünü seçin. Test etmek istediğiniz kod projesini seçin ve ardından **Tamam**' ı seçin.

   Test etmek istediğiniz kod başka bir konumdaysa, başvuru ekleme hakkında bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md) .

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki bölümlerden birine bakın:

**Birim testleri yazma**

- [Birim testi kod](../test/unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [MSTest framework birim testleri kullanın](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Birim testlerini çalıştırma**

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
