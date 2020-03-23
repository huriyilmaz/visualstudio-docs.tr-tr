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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566000"
---
# <a name="unit-test-your-code"></a>Birim kodunuzu test edin

Birim testleri, geliştiricilere ve test edenlere C#, Visual Basic ve C++ projelerindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar.

Birim testi araçları şunları içerir:

* **Test Explorer**&mdash;Çalıştır birim testleri ve **Test Explorer**sonuçlarını bakın. **Test Gezgini**için bağdaştırıcısı olan üçüncü taraf çerçevesi de dahil olmak üzere herhangi bir birim test çerçevesi kullanabilirsiniz.

* **Yönetilen kod**&mdash;için Microsoft birim test çerçevesi Yönetilen kod için Microsoft birim test çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sağlar.

* **C++**&mdash;için Microsoft birim test çerçevesi C++ için Microsoft birim test çerçevesi, C++ iş **yüküne sahip Masaüstü geliştirmenin** bir parçası olarak yüklenir. Yerel kodu sınandırıda bir çerçeve sağlar. Google Test, Boost.Test ve CTest çerçeveleri de dahildir ve ek test çerçeveleri için üçüncü taraf bağdaştırıcılar kullanılabilir. Daha fazla bilgi için [C/C++ için birim testleri yaz'a](../test/writing-unit-tests-for-c-cpp.md)bakın.

* **Kod kapsama araçları**&mdash;Ünitenizin test ettiği ürün kodu miktarını Test Gezgini'ndeki tek bir komuttan belirleyebilirsiniz.

* **Microsoft Fakes yalıtım çerçevesi**&mdash;Microsoft Fakes yalıtım çerçevesi, test altındaki kodda bağımlılıklar oluşturan üretim ve sistem kodu için yedek sınıflar ve yöntemler oluşturabilir. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

Test verileri ve birim testleri paketi oluşturmak için .NET kodunuzu keşfetmek için [IntelliTest'i](../test/generate-unit-tests-for-your-code-with-intellitest.md) de kullanabilirsiniz. Koddaki her deyim için, bu deyimi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir servis talebi çözümlemesi gerçekleştirilir.

## <a name="key-tasks"></a>Ana görevler

Birim testlerini anlama ve oluşturma konusunda yardımcı olmak için aşağıdaki makaleleri kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Hızlı başlatmalar ve geçişler:** Visual Studio'daki birim testleri hakkında kod örneklerinden bilgi edinin.|- [Walkthrough: Yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Quickstart: Test Gezgini ile test odaklı geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Nasıl kullanılır: C++ uygulamalarına birim testleri ekleme](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Test Explorer ile birim testi:** Test Gezgini'nin daha üretken ve verimli birim testleri oluşturmaya nasıl yardımcı olabileceğini öğrenin.|- [Birim test temelleri](../test/unit-test-basics.md)<br />- [Birim test projesi oluşturma](../test/create-a-unit-test-project.md)<br />- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)<br />- [Üçüncü taraf birim test çerçevelerini yükleme](../test/install-third-party-unit-test-frameworks.md)|
|**Birim testi C++ kodu**|- [C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp.md)|
|**Yalıtım ünitesi testleri**|- [Microsoft Fakes ile testi naltında kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Projenizin kodunun ne oranda sınantının test edilebilmiş olduğunu belirlemek için kod kapsamını kullanın:** Visual Studio test araçlarının kod kapsamı özelliği hakkında bilgi edinin.|- [Ne kadar kodun test edildiğini belirlemek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Yük testleri kullanarak stres ve performans analizi yapın:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için yük testleri nasıl oluşturup oluşturacağımız hakkında bilgi edinin.|- [Quickstart: Yük testi projesi oluşturma](../test/quickstart-create-a-load-test-project.md)<br />- [Yük testi (Azure Test Planları ve TFS)](/azure/devops/test/load-test/index?view=vsts)|
|**Kalite kapılarını ayarlayın:** Kod iade edilmeden veya birleştirilmeden önce testlerin çalıştırılmasını zorlamak için kalite kapıları nasıl oluşturulacağı nızı öğrenin.|- [İade ilkeleri (Azure Repos TFVC)](/azure/devops/repos/tfvc/add-check-policies?view=vsts)|
|**Test seçeneklerini ayarlayın:** Test sonuçlarının depolandığı test seçeneklerini nasıl yapılandıracağınızı öğrenin.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API başvuru belgeleri

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>öznitelikleri, özel durumları, ileri gelenleri ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting ad alanını açıklar.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>ASP.NET ve web hizmeti birimi testleri için destek sağlayarak UnitTesting ad alanını genişleten UnitTesting.Web ad alanını açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesini artırma](../test/improve-code-quality.md)
