---
title: Test araçları
description: Test araçlarının Visual Studio ve takımınıza yüksek kod mükemmelliği standartları geliştirmenize ve sürdürmenize nasıl yardımcı olduğunu öğrenin.
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
ms.openlocfilehash: 7cfb71071efab7e119c04d32f3362e00add4bdc2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148525"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Visual Studio'daki test araçlarına ilk bakış

Visual Studio test araçları, sizin ve takımınızın kod mükemmelliğinde yüksek standartlar geliştirmenize ve bu standartları sürdürmenize yardımcı olabilir.

> [!NOTE]
> Birim testi, uygulamanın tüm sürümlerinde Visual Studio. Live Unit Testing ve IntelliTest gibi diğer test araçları yalnızca Visual Studio Enterprise kullanılabilir. Sürümler hakkında daha fazla bilgi için [bkz. IDE'Visual Studio karşılaştırma.](https://visualstudio.microsoft.com/vs/compare/)

## <a name="test-explorer"></a>Test Gezgini

Test **Gezgini penceresi geliştiricilerin** birim testleri oluşturmasına, yönetmeye ve çalıştırmasına yardımcı olur. Microsoft birim testi çerçevesini veya birkaç üçüncü taraf ve açık kaynak çerçeveden birini kullanabilirsiniz.

::: moniker range="vs-2017"
![Visual Studio Test Gezgini](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range=">=vs-2019"
![Visual Studio Test Gezgini 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Birim testini kullanmaya başlama](unit-test-your-code.md)
* [Test Gezgini ile birim testleri çalıştırma](run-unit-tests-with-test-explorer.md)
* [Test Gezgini Hakkında SSS](test-explorer-faq.md)
* [Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme](install-third-party-unit-test-frameworks.md)

Visual Studio da genişletilebilir ve NUnit ve xUnit.net gibi üçüncü taraf birim test bağdaştırıcıları için xUnit.net. Ayrıca kod kopyalama özelliği, yaygın hata düzeltmeleri veya yeniden düzenleme için adaylar olarak semantantik olarak benzer kod bloklarını tanımlamanıza yardımcı olarak yüksek kaliteli yazılım sunma konusunda da el ile ilerler.

![Üçüncü taraf test tümleştirmesi](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

[Live Unit Testing,](../test/live-unit-testing.md) birim testlerini arka planda otomatik olarak çalıştırır ve kod kapsamı ile test sonuçlarını grafiksel olarak kod düzenleyicisinde Visual Studio görüntüler.

> [!NOTE]
> Canlı birim testi yalnızca Enterprise sürümüyle kullanılabilir ve yalnızca .NET kodu için de kullanılabilir.

## <a name="intellitest"></a>IntelliTest

IntelliTest yönetilen kodunuz için birim testleri ve test verilerini otomatik olarak üretir. IntelliTest kapsamı iyiler ve yeni veya mevcut kod için birim testleri oluşturma ve sürdürme çabasını önemli ölçüde azaltır.

![IntelliTest iş içinde](media/devtest-intellitest.png)

> [!NOTE]
> IntelliTest yalnızca Enterprise kullanılabilir. Bu, kaynak grubu hedef alan C# .NET Framework. .NET Core ve .NET Standard şu anda desteklenmiyor.

* [Intellitest ile kodunuz için birim testleri oluşturma](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest – Hepsini kurala göre bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [IntelliTest başvuru kılavuzu](intellitest-manual/index.md)

## <a name="code-coverage"></a>Kod kapsamı

[Kod kapsamı,](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) projenizin kodunun gerçekte birim testleri gibi kodlu testler tarafından test edilen oranını belirler. Hatalara karşı etkili bir şekilde koruma için testlerinizi uygulamalı veya kodunuzun büyük bir oranını "kapsıyor" olması gerekir.

> [!NOTE]
> Kod kapsamı yalnızca Enterprise kullanılabilir.

Kod kapsamı analizi hem yönetilen hem de yönetilemeyen (yerel) koda uygulanabilir.

Test yöntemlerini Test Gezgini'ni kullanarak çalıştırdığınızda kod kapsamı bir seçenektir. Sonuçlar tablosu, her derleme sınıfı ve yöntemi içinde çalışan kod yüzdesini gösterir. Ayrıca, kaynak düzenleyici hangi kodun test edildiğini gösterir.

* [Kod kapsamını kullanarak ne kadar kodun test edildiğini belirleme](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Visual Studio ile birim testi, kod kapsamı ve kod Visual Studio analizi (Laboratuvar)](https://azuredevopslabs.com/labs/devopsserver/liveunittesting)
* [Kod kapsamı analizini özelleştirme](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes,](../test/isolating-code-under-test-with-microsoft-fakes.md) uygulamanın diğer bölümlerini saplamalar veya dolgularla değiştirerek test etmekte olduğunu kodu yalıtmanıza yardımcı olur.

> [!NOTE]
> Microsoft Fakes sürümde Enterprise ve yalnızca .NET kodu için de kullanılabilir.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Kodlanmış KULLANıCı Arabirimi ve Selenium ile kullanıcı arabirimi testi

Kodlanmış UI testleri, uygulama kullanıcı arabiriminizin işlevselliğini ve davranışını doğrulamak için tam otomatik testler oluşturmanın bir yolunu sağlar. XAML tabanlı UWP uygulamaları, tarayıcı uygulamaları ve kullanıcı arabirimi uygulamaları gibi çeşitli teknolojilerde kullanıcı arabirimi testini SharePoint olabilir.

> [!NOTE]
> Kodlanmış kullanıcı arabirimi kullanım dışı bir özelliktir.

Selenium ile en iyi tür Kodlanmış UI Testlerini veya genel tarayıcı tabanlı UI testlerini tercih Visual Studio ihtiyacınız olan tüm araçları sağlar.

![Kodlanmış kullanıcı arabirimi ile kullanıcı arabirimi testi](media/devtest-codeduitest.png)

* [Kodunuzu test etmek için UI otomasyonunu kullanma](use-ui-automation-to-test-your-code.md)
* [Kullanmaya başlayın kullanıcı arabirimi testi oluşturma, düzenleme ve bakımını sağlama](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Kodlanmış UI testleriyle UWP uygulamalarını test edin](test-uwp-app-with-coded-ui-test.md)
* [Visual Studio Enterprise (Lab) ile kodlanmış UI testlerini giriş](https://azuredevopslabs.com/labs/tfs/codedui)

## <a name="related-scenarios"></a>İlgili senaryolar

* [Keşif & el ile test (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Yük test etme (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Sürekli test (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Kod analizi araçları](../code-quality/code-analysis-for-managed-code-overview.md)
