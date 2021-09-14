---
title: Birim testi projesi oluşturma
description: Birim testi projesi oluşturmayı öğrenin. Test projesi üretim koduyla aynı çözümde olabilir veya ayrı bir çözümde olabilir.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d7b5629cc50a2a9d08d00daabd2b4579e628a6cb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628172"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri genellikle test altındaki kodun yapısını yansıtır. Örneğin, üründeki her kod projesi için bir birim testi projesi oluşturulur. Test projesi üretim koduyla aynı çözümde olabilir veya ayrı bir çözümde olabilir. Bir çözümde birden çok birim testi projesine sahip olabilirsiniz.

> [!NOTE]
> Yerel kod ve test projesi yapısına yönelik birim testlerinin konumu, bu makalede açıklanan yapıdan farklı olabilir. Daha fazla bilgi için bkz. [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md).

## <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için

1. **dosya** menüsünde, **yeni**  >  **Project**' yi seçin veya **Ctrl** + **shıft** + **N** tuşuna basın.

::: moniker range="vs-2017"

2. **yeni Project** iletişim kutusunda, **yüklü** düğümünü genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından **test**' i seçin.

3. kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest test Project** veya **nunit test Project**. Projeyi adlandırın ve ardından **Tamam**' ı seçin.

   ![Visual Studio 2017 ' de Test projesi şablonları](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Yeni proje oluştur** sayfasında, arama kutusuna **birim testi** yazın. kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest test Project** veya **nunit test Project** ve ardından **ileri**' yi seçin.

   ![Visual Studio 2019 ' de Test projesi şablonları](media/vs-2019/test-project-templates.png)

3. **Yeni projenizi yapılandırın** sayfasında, projeniz için bir ad girin ve ardından **Oluştur**' u seçin.

::: moniker-end

4. Birim testi projenizde, test altındaki koda bir başvuru ekleyin. Aynı çözümde bir kod projesine bir başvuru eklemek için:

   1. **Çözüm Gezgini**' de test projesi seçin.

   2. **Project** menüsünde **başvuru ekle**' yi seçin.

   3. **Başvuru Yöneticisi**' nde **Projeler** altındaki **çözüm** düğümünü seçin. Test etmek istediğiniz kod projesini seçin ve ardından **Tamam**' ı seçin.

   Test etmek istediğiniz kod başka bir konumdaysa, başvuru ekleme hakkında bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md) .

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki bölümlerden birine bakın:

**Birim testlerini yazma**

- [Kodunuzun birim testi](../test/unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Birim testlerini çalıştırma**

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
