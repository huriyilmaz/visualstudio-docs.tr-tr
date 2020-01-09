---
title: Birim Testi
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
ms.openlocfilehash: ffe383d2195feb6689954a8ec858b196bae8c06a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566000"
---
# <a name="unit-test-your-code"></a>Birim testi kod

Birim testleri, geliştiricilere ve test edicilere C#, Visual Basic ve C++ projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir şekilde verin.

Birim testi araçları şunları içerir:

* **Test gezgini**&mdash;birim testlerini çalıştırın ve sonuçlarını **Test Gezgini**'nde görüntüleyin. Bir bağdaştırıcı için olan bir üçüncü taraf çerçeve dahil olmak üzere tüm birim testi çerçevesini kullanabilirsiniz **Test Gezgini**.

* **Yönetilen kod için Microsoft birim test çerçevesi**&mdash;yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sunar.

* **C++ için Microsoft birim test çerçevesi**&mdash;C++ için Microsoft birim test çerçevesi bir parçası olarak yüklü **C++ ile masaüstü geliştirme** iş yükü. Bu, yerel kodu test etmek için bir çerçeve sunar. CTest Google Test ve Boost.Test çerçeveleri de dahildir ve ek test çerçeveleri için üçüncü taraf bağdaştırıcılar bulunmaktadır. Daha fazla bilgi için [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md).

* **Kod kapsamı Araçları**&mdash;Birim Test Gezgini'nde tek komuttan alıştırma testleri ürün kodu miktarını belirleyebilirsiniz.

* **Microsoft Fakes yalıtım çerçevesi**&mdash;sınıfları ve test edilen kodda bağımlılıklar oluşturan üretim ve sistem kodunun yöntemleri yerine Microsoft Fakes yalıtım çerçevesi oluşturabilirsiniz. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

Ayrıca [Intellitest](../test/generate-unit-tests-for-your-code-with-intellitest.md) test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu keşfedin. Koddaki her ifade için bir test girişi oluşturulur o ifadeyi yürütecek. Koddaki her koşullu şube için bir vaka analizi yapılır.

## <a name="key-tasks"></a>Ana görevler

Birim testlerini anlama ve oluşturmayla ilgili yardım almak için aşağıdaki makaleleri kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Hızlı başlangıç ve izlenecek yollar:** Kod örneklerinden Visual Studio 'da birim testi hakkında bilgi edinin.|- [Izlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Hızlı Başlangıç: Test Gezgini ile Test güdümlü geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [nasıl yapılır: C++ uygulamalara birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Test Gezgini ile birim testi:** Test Gezgini'nin daha üretken ve verimli birim testleri oluşturma nasıl yardımcı olabileceğini öğrenin.|- [Birim testi temel bilgileri](../test/unit-test-basics.md)<br />- [Bir birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)<br />- [Üçüncü taraf birim testi çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)|
|**Birim test C++ kodu**|[C/C++ için birim testleri - yazma](../test/writing-unit-tests-for-c-cpp.md)|
|**Birim testlerini yalıtma**|- [Microsoft Fakes ile test edilen kodu Ayır](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Proje kodunuzun ne oranda test edilen belirlemek için kod kapsamı kullanın:** Visual Studio Test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|- [Ne kadar kodun test edildiğini belirlemek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Yük testlerini kullanarak stres ve performans analizi gerçekleştirin:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için yük testleri oluşturmayı öğrenin.|- [hızlı başlangıç: yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md)<br />- [Test (Azure Test planları ve TFS) yükleyin](/azure/devops/test/load-test/index?view=vsts)|
|**Kalite kapıları ayarla:** Kod iade edilene veya birleştirilmeden önce testlerin çalıştırılmasını zorlamak için kalite kapıları oluşturma hakkında bilgi edinin.|- [İade ilkeleri (Azure depoları TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Test seçeneklerini ayarla:** Test seçeneklerini yapılandırma hakkında bilgi edinin, örneğin, test sonuçlarının depolandığı yer.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API başvuru belgeleri

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> öznitelikler, özel durumlar, bildirimler ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting ad alanını açıklar.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> ASP.NET ve web hizmeti birim testleri için destek sağlayan UnitTesting ad alanını genişleten alanını UnitTesting.Web ad alanını ad alanını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesini geliştirme](../test/improve-code-quality.md)
