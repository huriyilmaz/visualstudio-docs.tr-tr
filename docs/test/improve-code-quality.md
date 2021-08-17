---
title: Test araçları
description: Visual Studio test araçlarının, sizin ve ekibinizin yüksek standartlara sahip kod mükemmelliği geliştirme ve bt konusunda nasıl yardımcı olabileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 344418a1943f9225d5422923b044d04aa6ac4e955060fe2aefa10c27ee2dcfbe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121227212"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Visual Studio 'de test araçlarına ilk bakış

Visual Studio test araçları, sizin ve takımınızın kod mükemmelliğinde yüksek standartlar geliştirmenize ve bu standartları sürdürmenize yardımcı olabilir.

> [!NOTE]
> Birim testi tüm Visual Studio sürümlerinde kullanılabilir. Live Unit Testing ve ıntellitest gibi diğer test araçları yalnızca Visual Studio Enterprise sürümünde kullanılabilir. sürümler hakkında daha fazla bilgi için bkz. [Compare Visual Studio ıdes](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** penceresi, geliştiricilerin birim testlerini oluşturmalarına, yönetmesine ve çalıştırmasına yardımcı olur. Microsoft birim testi çerçevesini veya çeşitli üçüncü taraf ve açık kaynak çerçevelerinden birini kullanabilirsiniz.

::: moniker range="vs-2017"
![Visual Studio Test Gezgini](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range=">=vs-2019"
![Visual Studio Test Gezgini 16,2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Birim testini kullanmaya başlama](unit-test-your-code.md)
* [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Test Gezgini Hakkında SSS](test-explorer-faq.md)
* [Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme](install-third-party-unit-test-frameworks.md)

Visual Studio ayrıca genişletilebilir ve nunit ve xUnit.net gibi üçüncü taraf birim testi bağdaştırıcılarının kapısını açar. Ayrıca, kod kopyalama özelliği, yaygın hata düzeltmeleri veya yeniden düzenleme için aday olabilecek anlamsal benzer kod bloklarını tanımlamanızı sağlayarak yüksek kaliteli yazılım sunmaya yardımcı olur.

![Üçüncü taraf test tümleştirmesi](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing](../test/live-unit-testing.md) arka planda birim testlerini otomatik olarak çalıştırır ve kod kapsamını ve test sonuçlarını grafik olarak Visual Studio kod düzenleyicisinde görüntüler.

> [!NOTE]
> canlı birim testi yalnızca Enterprise sürümünde kullanılabilir ve yalnızca .net kodu için desteklenir.

## <a name="intellitest"></a>IntelliTest

IntelliTest, yönetilen kodunuz için birim testlerini ve test verilerini otomatik olarak oluşturur. IntelliTest kapsamı geliştirir ve yeni veya mevcut kod için birim testleri oluşturma ve sürdürme çabaları önemli ölçüde azaltır.

![IntelliTest eylemde](media/devtest-intellitest.png)

> [!NOTE]
> ıntellitest yalnızca Enterprise sürümünde kullanılabilir. .NET Framework hedefleyen C# kodu için desteklenir. .NET Core ve .NET Standard Şu anda desteklenmiyor.

* [Intellitest ile kodunuz için birim testleri oluşturma](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – tümünü kurala göre bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [IntelliTest başvurusu el ile](intellitest-manual/index.md)

## <a name="code-coverage"></a>Kod kapsamı

[Kod kapsamı](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) , proje kodunuzun birim testleri gibi kodlanmış testler tarafından ne oranda test edildiğini belirler. Hatalara karşı etkili bir şekilde koruma sağlamak için, testleriniz kodunuzun büyük bir oranını "ele almalıdır" veya "kapsamalıdır".

> [!NOTE]
> kod kapsamı yalnızca Enterprise sürümünde kullanılabilir.

Kod kapsamı analizi, hem yönetilen hem de yönetilmeyen (yerel) koda uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

* [Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [birim testi, kod kapsamı ve Visual Studio (Lab) ile kod kopyası analizi](https://azuredevopslabs.com/labs/devopsserver/liveunittesting)
* [Kod kapsamı analizini özelleştirme](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) , uygulamanın diğer bölümlerini saplamalar veya parçalar ile değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur.

> [!NOTE]
> Microsoft Fakes yalnızca Enterprise edition 'da kullanılabilir ve yalnızca .net kodu için desteklenir.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Kodlanmış UI ve Selenium ile Kullanıcı Arabirimi testi

Kodlanmış UI testleri, uygulamanızın kullanıcı arabiriminin işlevselliğini ve davranışını doğrulamak için tam otomatikleştirilmiş testlerin oluşturulması için bir yol sağlar. XAML tabanlı UWP uygulamaları, tarayıcı uygulamaları ve SharePoint uygulamalar dahil olmak üzere çeşitli teknolojiler genelinde uı testini otomatikleştirebilirler.

> [!NOTE]
> Kodlanmış UI kullanım dışı olan bir özelliktir.

selenium ile en iyi kodlanmış uı testlerini veya genel tarayıcı tabanlı kullanıcı arabirimi testini tercih etmeksizin, Visual Studio ihtiyacınız olan tüm araçları sağlar.

![Kodlanmış UI ile UI testi](media/devtest-codeduitest.png)

* [Kodunuzu test etmek için UI Otomasyonunu kullanma](use-ui-automation-to-test-your-code.md)
* [Kodlanmış UI testi oluşturmaya, düzenlemesine ve sürdürme ile çalışmaya başlama](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Kodlanmış UI Testleriyle UWP uygulamalarını test etme](test-uwp-app-with-coded-ui-test.md)
* [Visual Studio Enterprise (Lab) ile kodlanmış uı testlerine giriş](https://azuredevopslabs.com/labs/tfs/codedui)

## <a name="related-scenarios"></a>İlgili senaryolar

* [Araştırmacı & el ile test (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Yük test etme (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Sürekli test (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Kod analizi araçları](../code-quality/code-analysis-for-managed-code-overview.md)
