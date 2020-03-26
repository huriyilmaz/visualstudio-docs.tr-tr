---
title: Test araçları
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 0517d03db180ce76940723ca935be258d0cf1818
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256237"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Visual Studio'da test araçlarına ilk bakış

Visual Studio test araçları, sizin ve ekibinizin yüksek kod mükemmelliği standartları geliştirmenize ve sürdürmenize yardımcı olabilir.

> [!NOTE]
> Birim testi Visual Studio'nun tüm sürümlerinde mevcuttur. Canlı Birim Testi, IntelliTest ve Kodlu UI Testi gibi diğer test araçları yalnızca Visual Studio Enterprise sürümünde kullanılabilir. Sürümler hakkında daha fazla bilgi [için](https://visualstudio.microsoft.com/vs/compare/)bkz.

## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** penceresi, geliştiricilerin birim testleri oluşturmasına, yönetmesine ve çalıştırmesine yardımcı olur. Microsoft birim test çerçevesini veya birkaç üçüncü taraf ve açık kaynak çerçevelerinden birini kullanabilirsiniz.

::: moniker range="vs-2017"
![Görsel Stüdyo Test Explorer](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Görsel Stüdyo Test Explorer 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Birim testiile başlayın](unit-test-your-code.md)
* [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Test Gezgini Hakkında SSS](test-explorer-faq.md)
* [Üçüncü taraf birim testi çerçevelerini yükleme](install-third-party-unit-test-frameworks.md)

Visual Studio da genişletilebilir ve NUnit ve xUnit.net gibi üçüncü taraf birim test adaptörleri için kapıyı açar. Buna ek olarak, kod klon lama özelliği, yaygın hata düzeltmeleri veya yeniden düzenleme için aday olabilecek anlamsal olarak benzer kod bloklarını belirlemenize yardımcı olarak yüksek kaliteli yazılım lar sunarak el ele gider.

![Üçüncü taraf test tümleştirmesi](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Canlı Birim Testi](../test/live-unit-testing.md) arka planda birim testlerini otomatik olarak çalıştırıyor ve Visual Studio kod düzenleyicisinde kod kapsamını ve test sonuçlarını grafik olarak görüntüler.

## <a name="intellitest"></a>IntelliTest

IntelliTest, yönetilen kodunuz için birim testleri ve test verilerini otomatik olarak oluşturur. IntelliTest kapsama alanını geliştirir ve yeni veya varolan kodlar için birim testleri oluşturma ve sürdürme çabasını önemli ölçüde azaltır.

![IntelliTest iş başında](media/devtest-intellitest.png)

* [Intellitest ile kodunuz için birim testleri oluşturma](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – Hepsini yönetmek için bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [IntelliTest başvuru kılavuzu](intellitest-manual/index.md)

## <a name="code-coverage"></a>Kod kapsamı

[Kod kapsamı,](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) projenizin kodunun gerçekte birim testleri gibi kodlanmış testler tarafından test edildiğini belirler. Hatalara karşı etkili bir şekilde korunmak için, testlerinizin kodunuzu büyük ölçüde kullanması veya "kapsaması" gerekir.

Kod kapsamı çözümlemesi hem yönetilen hem de yönetilmeyen (yerel) koda uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

* [Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Visual Studio (Lab) ile birim testi, kod kapsamı ve kod klon analizi](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Kod kapsamı analizini özelleştirme](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes,](../test/isolating-code-under-test-with-microsoft-fakes.md) uygulamanın diğer bölümlerini saplama veya şimlerle değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Kodlu Kullanıcı Arabirimi ve Selenyum ile kullanıcı arabirimi testi

Kodlanmış Kullanıcı Arabirimi testleri, uygulamanızın kullanıcı arabiriminin işlevselliğini ve davranışını doğrulamak için tam otomatik testler oluşturmanın bir yolunu sağlar. XAML tabanlı UWP uygulamaları, tarayıcı uygulamaları ve SharePoint uygulamaları da dahil olmak üzere çeşitli teknolojilerde UI testini otomatikleştirebilirler.

Whether you choose best-of-breed Coded UI Tests or generic browser-based UI testing with Selenium, Visual Studio provides all the tools you need.

![Kodlu UI ile ui testi](media/devtest-codeduitest.png)

* [Kodunuzu test etmek için UI otomasyonunu kullanma](use-ui-automation-to-test-your-code.md)
* [Kodlanmış bir UI testi oluşturmaya, düzenlemeye ve korumaya başlayın](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [UWP uygulamalarını kodlanmış UI testleriyle test edin](test-uwp-app-with-coded-ui-test.md)
* [Visual Studio Enterprise (Lab) ile kodlanmış ui testlerine giriş](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Yük test etme

[Yük testi,](../test/quickstart-create-a-load-test-project.md) birim testleri ve web performans testleri çalıştırarak bir sunucu uygulamasındaki yükü simüle eder.

## <a name="related-scenarios"></a>İlgili senaryolar

* [Araştırmacı & manuel test (Azure Test Planları)](/azure/devops/test/index?view=vsts)
* [Yük testi (Azure Test Planları)](/azure/devops/test/load-test/index?view=vsts)
* [Sürekli test (Azure Test Planları)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)
* [Kod analiz araçları](../code-quality/code-analysis-for-managed-code-overview.md)
