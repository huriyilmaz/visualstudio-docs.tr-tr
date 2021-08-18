---
title: Birim test araçları & görevleri
description: Geliştiricilere ve test edicilere kodunuzda mantık hataları aramak için hızlı bir yol sağlamak üzere kullanabileceğiniz birim testi araçları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 08/10/2021
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bd506fe8c47050e936854c51f6e3c225210bcdff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100406"
---
# <a name="unit-test-tools-and-tasks"></a>Birim testi araçları ve görevleri

birim testleri, geliştiricilere ve test edicilere C#, Visual Basic ve C++ projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar.

Birim testi araçları şunları içerir:

* **Test Gezgini** &mdash; Birim testlerini çalıştırın ve sonuçlarını **Test Gezgini**'nde görüntüleyin. **Test Gezgini** için bir bağdaştırıcıya sahip olan, üçüncü taraf bir çerçeve dahil olmak üzere herhangi bir birim testi çerçevesini kullanabilirsiniz.

* **Yönetilen kod** &mdash; için Microsoft birim testi çerçevesi yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .net kodunu test etmek için bir çerçeve sağlar.

* **Microsoft yerel birim test çerçevesi** &mdash; C++ için Microsoft Native Unit Test Framework, C++ iş yüküyle **Masaüstü geliştirmenin** bir parçası olarak yüklenir. Yerel kodu test etmek için bir çerçeve sağlar. Google Test, Boost. test ve CTest çerçeveleri de dahil edilmiştir ve üçüncü taraf bağdaştırıcılar ek test çerçeveleri için kullanılabilir. Daha fazla bilgi için bkz. [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

* **Kod kapsamı araçları** &mdash; Test Gezgini 'nde, birim testlerinizin çalıştıracağı ürün kodu miktarını bir komuttan belirleyebilirsiniz.

* **Microsoft Fakes yalıtım çerçevesi** &mdash; Microsoft Fakes yalıtım çerçevesi, test edilen kodda bağımlılıklar oluşturan üretim ve sistem .net kodu için alternatif sınıflar ve yöntemler oluşturabilir. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

.NET için, kodunuzu araştırmak ve test verileri ve birim testleri paketi oluşturmak için [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) ' i de kullanabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir olay Analizi gerçekleştirilir.

## <a name="key-tasks"></a>Ana görevler

Birim testlerini anlama ve oluşturmayla ilgili yardım almak için aşağıdaki makaleleri kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Öğreticiler:** kod örneklerinden Visual Studio birim testi hakkında bilgi edinin.|- [Birim testini kullanmaya başlama](getting-started-with-unit-testing.md)<br />- [Test Gezgini ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)|
|**Test Gezgini Ile birim testi:** Test Gezgini 'nin daha üretken ve verimli birim testleri oluşturmaya nasıl yardımcı olabileceğini öğrenin.|- [Birim testi temelleri](../test/unit-test-basics.md)<br />- [Birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)<br />- [Üçüncü taraf birim testi çerçeveleri 'ni yükler](../test/install-third-party-unit-test-frameworks.md)|
|**Birim testi .NET kodu**|- [.NET kodu için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)|
|**Birim testi C++ kodu**|- [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)<br />- [Nasıl yapılır: C++ uygulamalarına birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Projenizin kodunun ne oranda test edildiğini belirlemek için kod kapsamını kullanın:** Visual Studio test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|- [Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Birim testlerini yalıtma**|- [Test kapsamındaki .NET kodunu Microsoft Fakes ayır](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Yük testlerini kullanarak stres ve performans analizi gerçekleştirin:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için yük testleri oluşturmayı öğrenin (kullanım dışı).|- [Hızlı başlangıç: yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md)<br />- [yük testi (Azure Test Plans ve TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Kalite kapıları ayarla:** Kod iade edilene veya birleştirilmeden önce testlerin çalıştırılmasını zorlamak için kalite kapıları oluşturma hakkında bilgi edinin.|- [iade ilkeleri (Azure Repos tfvc)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Test seçeneklerini ayarla:** Test seçeneklerini yapılandırma hakkında bilgi edinin, örneğin, test sonuçlarının depolandığı yer.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API başvuru belgeleri

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> öznitelikleri, özel durumları, onayları ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting Ad alanını açıklar.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>ASP.NET ve Web hizmeti birim testleri için destek sağlayarak unittesting ad alanını genişleten unittesting. Web ad alanını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesini geliştirme](../test/improve-code-quality.md)