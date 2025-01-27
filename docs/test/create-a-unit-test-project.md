---
title: Birim testi projesi oluşturma
description: Birim testi projesi oluşturma hakkında bilgi. Test projesi, üretim koduyla aynı çözümde veya ayrı bir çözümde olabilir.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.date: 01/13/2022
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 71f0a341c3ddd544fbf795755db4e3e52b380816
ms.sourcegitcommit: f81a8f381bcdbac96d112f815737ba1df55d97a3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137667414"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma

Birim testleri genellikle test altındaki kodun yapısını yansıtabilir. Örneğin, üründe her kod projesi için bir birim testi projesi oluşturulur. Test projesi, üretim koduyla aynı çözümde veya ayrı bir çözümde olabilir. Bir çözümde birden çok birim testi projesine sahip olabilirsiniz.

> [!NOTE]
> Yerel kod için birim testlerinin konumu ve test projesi yapısı, bu makalede açıklanan yapıdan farklı olabilir. Daha fazla bilgi için [bkz. C/C++ için birim testleri yazma.](writing-unit-tests-for-c-cpp.md)

## <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için

1. Dosya menüsünde **Yeni** **sayfa'Project**  >  seçin **veya** **Ctrl Shift** N + **tuşlarına** + **basın.**

::: moniker range="vs-2017"

2. Yeni **Project** iletişim kutusunda Yüklü düğümünü  genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından Test'i **seçin.**

3. Kullanmak istediğiniz test çerçevesinin proje şablonunu seçin, örneğin **MSTest Test** Project **veya NUnit Test** Project. Projeye bir ad ve ardından Tamam'ı **seçin.**

   ![Visual Studio 2017'de proje şablonlarını test etmek](media/test-project-templates.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Yeni **proje oluştur sayfasında** arama kutusuna **birim testi** yazın. Kullanmak istediğiniz test çerçevesinin proje şablonunu **(örneğin, MSTest Test** Project veya **NUnit Test Project)** seçin ve ardından Sonraki 'yi **seçin.**

   ![Visual Studio 2019'da proje şablonlarını test etmek](media/vs-2019/test-project-templates.png)

3. Yeni **projenizi yapılandır sayfasında** projeniz için bir ad girin ve Oluştur'a **tıklayın.**

::: moniker-end

4. Birim testi projenize, test altındaki koda bir başvuru ekleyin. Aynı çözümdeki bir kod projesine başvuru eklemek için:

   1. içinde test projesini **Çözüm Gezgini.**

   2. Yeni **Project** **Ekle'yi seçin.**

   3. Başvuru **Yöneticisi'nde** Projeler altında **Çözüm** düğümünü **seçin.** Test etmek istediğiniz kod projesini ve ardından Tamam'ı **seçin.**

   Test etmek istediğiniz kod başka bir konumda ise, başvuru ekleme hakkında [bilgi](../ide/managing-references-in-a-project.md) için bkz. Projedeki başvuruları yönetme.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki bölümlerden birini görme:

**Birim testleri yazma**

- [Kodunuzu birim testi](../test/unit-test-your-code.md)

- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

- [Birim testlerinde MSTest çerçevesini kullanma](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**Birim testleri çalıştırma**

- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)