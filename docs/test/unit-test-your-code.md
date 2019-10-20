---
title: Birim Testi
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: fd6d6dca2680dcfcaa42912333b080c428ba78d2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659855"
---
# <a name="unit-test-your-code"></a>Kodunuzun birim testi

Birim testleri C#, geliştiricilere ve test edicilere, Visual Basic ve C++ projelerdeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar.

Birim testi araçları şunları içerir:

* **Test gezgini &mdash;Run birim** testlerini ve sonuçlarını **Test Gezgini**'nde görün. **Test Gezgini**için bir bağdaştırıcıya sahip olan, üçüncü taraf bir çerçeve dahil olmak üzere herhangi bir birim testi çerçevesini kullanabilirsiniz.

* **Yönetilen kod Için Microsoft** birim testi çerçevesi &mdash;The yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sağlar.

* İçin C++ Microsoft birim testi çerçevesi &mdash;The **için C++ Microsoft birim testi çerçevesi** , iş yüküyle  **C++ masaüstü geliştirmenin** bir parçası olarak yüklenir. Yerel kodu test etmek için bir çerçeve sağlar. Google Test, Boost. test ve CTest çerçeveleri de dahil edilmiştir ve üçüncü taraf bağdaştırıcılar ek test çerçeveleri için kullanılabilir. Daha fazla bilgi için bkz. [C/C++Için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

* **Kod kapsamı araçları** &mdash;You, birim testlerinizin test Gezgini 'nde bir komuttan çalışacağını ürün kodu miktarını belirleyebilir.

* Microsoft Fakes yalıtım çerçevesi &mdash;The Microsoft Fakes **yalıtım çerçevesi,** test edilen kodda bağımlılıklar oluşturan üretim ve sistem kodu için alternatif sınıflar ve Yöntemler oluşturabilir. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

Ayrıca, test verileri ve birim testleri paketi oluşturmak üzere .NET kodunuzu araştırmak için [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) ' i de kullanabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir olay Analizi gerçekleştirilir.

## <a name="key-tasks"></a>Ana görevler

Birim testlerini anlama ve oluşturmayla ilgili yardım almak için aşağıdaki makaleleri kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Hızlı başlangıç ve izlenecek yollar:** Kod örneklerinden Visual Studio 'da birim testi hakkında bilgi edinin.|- [Izlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [hızlı başlangıç: Test Gezgini Ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [nasıl yapılır: C++ uygulamalara birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Test Gezgini Ile birim testi:** Test Gezgini 'nin daha üretken ve verimli birim testleri oluşturmaya nasıl yardımcı olabileceğini öğrenin.|- [birim testi temelleri](../test/unit-test-basics.md)<br />- [birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />[Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md) - <br />[üçüncü taraf birim testi](../test/install-third-party-unit-test-frameworks.md) çerçevelerini -  yüklemesi|
|**Birim test C++ kodu**|[C/C++ için birim testleri -  yazma](../test/writing-unit-tests-for-c-cpp.md)|
|**Birim testlerini yalıtma**|[Microsoft Fakes ile test edilen kodu yalıtmak](../test/isolating-code-under-test-with-microsoft-fakes.md) - |
|**Projenizin kodunun ne oranda test edildiğini belirlemek için kod kapsamını kullanın:** Visual Studio test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|- [kodun ne kadar test edildiğini öğrenmek için kod kapsamını kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Yük testlerini kullanarak stres ve performans analizi gerçekleştirin:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için yük testleri oluşturmayı öğrenin.|- [hızlı başlangıç: yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md)<br />[Yük testi -  (Azure test Plans ve TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Kalite kapıları ayarla:** Kod iade edilene veya birleştirilmeden önce testlerin çalıştırılmasını zorlamak için kalite kapıları oluşturma hakkında bilgi edinin.|- [iade ilkeleri (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Test seçeneklerini ayarla:** Test seçeneklerini yapılandırma hakkında bilgi edinin, örneğin, test sonuçlarının depolandığı yer.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API başvuru belgeleri

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>, öznitelikleri, özel durumları, onayları ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting Ad alanını açıklar.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>, ASP.NET ve Web hizmeti birim testleri için destek sağlayarak UnitTesting Ad alanını genişleten UnitTesting. Web ad alanını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesini geliştirme](../test/improve-code-quality.md)
