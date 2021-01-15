---
title: Birim test araçları & görevleri
description: Geliştiricilere ve test edicilere kodunuzda mantık hataları aramak için hızlı bir yol sağlamak üzere kullanabileceğiniz birim testi araçları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dc82d72d7c0a333fc28146746a473ed359857490
ms.sourcegitcommit: 993fca11dc373a10150751bc2a045a9701a9db2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98240289"
---
# <a name="unit-test-tools-and-tasks"></a>Birim testi araçları ve görevleri

Birim testleri, geliştiricilere ve test edicilere C#, Visual Basic ve C++ projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar.

Birim testi araçları şunları içerir:

* **Test Gezgini** &mdash; Birim testlerini çalıştırın ve sonuçlarını **Test Gezgini**'nde görüntüleyin. **Test Gezgini** için bir bağdaştırıcıya sahip olan, üçüncü taraf bir çerçeve dahil olmak üzere herhangi bir birim testi çerçevesini kullanabilirsiniz.

* **Yönetilen kod** &mdash; için Microsoft birim testi çerçevesi Yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sağlar.

* C++ için Microsoft **birim testi çerçevesi** &mdash; C++ için Microsoft birim testi çerçevesi, C++ iş yüküyle **Masaüstü geliştirmenin** bir parçası olarak yüklenir. Yerel kodu test etmek için bir çerçeve sağlar. Google Test, Boost. test ve CTest çerçeveleri de dahil edilmiştir ve üçüncü taraf bağdaştırıcılar ek test çerçeveleri için kullanılabilir. Daha fazla bilgi için bkz. [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

* **Kod kapsamı araçları** &mdash; Test Gezgini 'nde, birim testlerinizin çalıştıracağı ürün kodu miktarını bir komuttan belirleyebilirsiniz.

* **Microsoft Fakes yalıtım çerçevesi** &mdash; Microsoft Fakes yalıtım çerçevesi, test edilen kodda bağımlılıklar oluşturan üretim ve sistem .NET kodu için alternatif sınıflar ve Yöntemler oluşturabilir. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

.NET için, kodunuzu araştırmak ve test verileri ve birim testleri paketi oluşturmak için [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) ' i de kullanabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir olay Analizi gerçekleştirilir.

## <a name="key-tasks"></a>Ana görevler

Birim testlerini anlama ve oluşturmayla ilgili yardım almak için aşağıdaki makaleleri kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Hızlı başlangıç ve izlenecek yollar:** Kod örneklerinden Visual Studio 'da birim testi hakkında bilgi edinin.|- [İzlenecek yol: .NET kodu için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [İzlenecek yol: Test Gezgini ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Nasıl yapılır: C++ uygulamalarına birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Test Gezgini Ile birim testi:** Test Gezgini 'nin daha üretken ve verimli birim testleri oluşturmaya nasıl yardımcı olabileceğini öğrenin.|- [Birim testi temelleri](../test/unit-test-basics.md)<br />- [Birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)<br />- [Üçüncü taraf birim testi çerçeveleri 'ni yükler](../test/install-third-party-unit-test-frameworks.md)|
|**Birim testi C++ kodu**|- [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)|
|**Projenizin kodunun ne oranda test edildiğini belirlemek için kod kapsamını kullanın:** Visual Studio test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|- [Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanın](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Birim testlerini yalıtma**|- [Microsoft Fakes ile test edilen .NET kodunu yalıtın](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Yük testlerini kullanarak stres ve performans analizi gerçekleştirin:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için yük testleri oluşturmayı öğrenin (kullanım dışı).|- [Hızlı başlangıç: yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md)<br />- [Yük testi (Azure Test Plans ve TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Kalite kapıları ayarla:** Kod iade edilene veya birleştirilmeden önce testlerin çalıştırılmasını zorlamak için kalite kapıları oluşturma hakkında bilgi edinin.|- [İade ilkeleri (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Test seçeneklerini ayarla:** Test seçeneklerini yapılandırma hakkında bilgi edinin, örneğin, test sonuçlarının depolandığı yer.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API başvuru belgeleri

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> öznitelikleri, özel durumları, onayları ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting Ad alanını açıklar.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> ASP.NET ve Web hizmeti birim testleri için destek sağlayarak UnitTesting Ad alanını genişleten UnitTesting. Web ad alanını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesini geliştirme](../test/improve-code-quality.md)