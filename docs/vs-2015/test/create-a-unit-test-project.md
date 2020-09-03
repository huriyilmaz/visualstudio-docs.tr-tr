---
title: Birim testi projesi oluştur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfc85b0616fdf8f30732f2409a1a15040967dbb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660647"
---
# <a name="create-a-unit-test-project"></a>Birim testi projesi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birim testleri genellikle test altındaki kodun yapısını yansıtır. Örneğin, üründeki her kod projesi için bir birim testi projesi oluşturulur. Test projesi üretim koduyla aynı çözümde olabilir veya ayrı bir çözümde olabilir. Bir çözümde birden çok birim testi projesine sahip olabilirsiniz.

> [!NOTE]
> Yerel kod ve test projesi yapısına yönelik birim testlerinin konumu, bu konuda açıklanan yapıdan farklı olabilir. Daha fazla bilgi için bkz. [var olan C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md).

## <a name="to-create-a-unit-test-project"></a>Birim testi projesi oluşturmak için:

1. **Dosya** menüsünde **Yeni** ' yi ve ardından **Proje** (klavye CTRL + SHIFT + N) öğesini seçin.

2. Yeni proje iletişim kutusunda, **yüklü** düğümünü genişletin, test projeniz için kullanmak istediğiniz dili seçin ve ardından **Test**' i seçin.

3. Microsoft birim testi çerçevelerinden birini kullanmak için proje şablonları listesinden **birim testi projesi** ' ni seçin. Aksi takdirde, kullanmak istediğiniz birim testi çerçevesinin proje şablonunu seçin. Örneğimizin hesaplar projesini test etmek için, proje AccountsTests adlı projeyi adlandırın.

4. Birim testi projenizde, test altındaki koda bir başvuru ekleyin.  Aynı çözümde bir kod projesine başvurunun nasıl oluşturulduğu aşağıda verilmiştir:

    1. Çözüm Gezgini içinde projeyi seçin.

    2. **Proje** menüsünde, **Başvuru Ekle...** öğesini seçin.

    3. Başvuru Yöneticisi iletişim kutusunda, **çözüm** düğümünü açın ve **Projeler**' i seçin. Kod projesi adını denetleyin ve iletişim kutusunu kapatın.

5. Test etmek istediğiniz kod başka bir konumdaysa, başvuru ekleme hakkında bilgi için bkz. [bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md) .

## <a name="next-steps"></a>Sonraki adımlar
 **Birim testlerini yazma**

 Aşağıdaki bölümlerden birine bakın:

- [Yönetilen Kod için Microsoft Birim Testi Çerçevesi ile .NET Framework için Birim Testleri Yazma](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [C++ için Microsoft Birim Testi Çerçevesi ile C/C++ için Birim Testleri Yazma](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

  **Birim testlerini çalıştırma**

  [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)
