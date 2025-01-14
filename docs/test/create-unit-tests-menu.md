---
title: Birim testi yöntemi saplamaları oluşturma
description: Bir test projesinin, test sınıfının ve test yöntemi saplamanın kolayca yapılandırmasını sağlayan Birim Testleri Oluştur komutunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/01/2021
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: a0252a0a2bc7ee84a8f32a75ab5c0a0b1da992aa
ms.sourcegitcommit: 5178819f49bb92995bca5c90c90e5fc5a1e04681
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2021
ms.locfileid: "134938262"
---
# <a name="create-unit-test-method-stubs-from-code"></a>Koddan birim testi yöntemi saplamaları oluşturma

Birim **Testleri Oluştur komutu** birim testi yöntemi saplamaları oluşturur. Bu özellik bir test projesinin, test sınıfının ve test yöntemi saplamanın kolayca yapılandırmasını sağlar.

::: moniker range="vs-2017"
> [!NOTE]
> Birim **Testleri Oluştur menü** komutu yalnızca .NET Framework 'i (.NET Core veya .NET Standard) hedef alan C# kodu için kullanılabilir.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Birim **Testleri Oluştur menü** komutu yalnızca C# kodu için kullanılabilir. Bu yöntemi .NET Core veya .NET Standard kullanmak için Visual Studio 2019 veya sonrası gerekir.
::: moniker-end

Birim **Testleri Oluştur menü** komutu genişletilebilir ve MSTest, MSTest V2, NUnit ve xUnit için testler oluşturmak için kullanılabilir.

## <a name="get-started"></a>başlarken

Çalışmaya başlamanız için test etmek istediğiniz projede kod düzenleyicisinde bir yöntem, tür veya ad alanı seçin, sağ tıklayın ve Birim Testleri **Oluştur'u seçin.** Birim **Testleri Oluştur** iletişim kutusu açılır ve burada testlerin nasıl oluşturulacaklarını yapılandırabilirsiniz.

::: moniker range="<=vs-2019"
![Birim testleri oluştur komutunu kullanma](media/createunittestcommand.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Birim testleri oluştur komutunu ve menü iletişim kutusunu kullanma](media/vs-2022/create-unit-test-command-menu-dialog.png)
::: moniker-end

NUnit veya xUnit için test çerçevesi seçeneklerini görmüyorsanız bkz. Üçüncü taraf [birim test çerçevelerini kullanma.](#use-third-party-unit-test-frameworks)

## <a name="set-unit-test-traits"></a>Birim testi niteliklerini ayarlama

Bu testleri test otomasyonu işleminin bir parçası olarak çalıştırmayı planlıyorsanız, testin başka bir test projesinde (yukarıdaki iletişim kutusunda ikinci seçenek) oluşturulmuş ve birim testi için birim testi niteliklerini ayarlamayı düşünebilirsiniz. Bu, bu belirli testleri sürekli tümleştirme veya sürekli dağıtım işlem hattının bir parçası olarak dahil etmek veya dışlamak için daha kolay bir şekilde olanak sağlar. Nitelikler, aşağıda gösterildiği gibi doğrudan birim testinde meta veriler eklenmiştir.

::: moniker range="<=vs-2019"
![Birim testi niteliklerini ayarlama](media/createunittest.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Birim testi oluşturma niteliklerini kullanma](media/vs-2022/create-unit-test-traits.png)
::: moniker-end

## <a name="use-third-party-unit-test-frameworks"></a>Üçüncü taraf birim testi çerçevelerini kullanma

NUnit veya xUnit için birim testlerini otomatik olarak oluşturmak için Market'te şu test çerçevesi uzantılarından Visual Studio yükleyin:

* [Test oluşturucuları için NUnit uzantısı](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371)
* [xUnit.net oluşturucular için bir uzantı](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator)

## <a name="when-should-i-use-this-feature"></a>Bu özelliği ne zaman kullan gerekir?

Birim testleri oluşturmanız gereken her durumda, ancak özellikle çok az test kapsamına sahip veya hiç belgesi olan mevcut kodu test ediyorsanız bu özelliği kullanın. Başka bir deyişle, sınırlı veya mevcut olmayan kod belirtimi vardır. Kodun gözlemlenen davranışını ifade etmek için [IntelliTest'e](generate-unit-tests-for-your-code-with-intellitest.md) benzer bir yaklaşım benimser.

Ancak, bir geliştirici bazı kodlar yazarak başladığında ve ardından birim testlerini önyüklemek için bunu kullandığında bu özellik de aynı şekilde geçerlidir. Kod akışı içinde geliştirici, belirli bir kod parçası için hızla bir birim testi yöntemi saplama (uygun bir test sınıfı ve uygun bir test projesi ile) oluşturmak istiyor olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [IntelliTest’i kullanmaya başlama](generate-unit-tests-for-your-code-with-intellitest.md)
- [Birim testi blog gönderileri](https://devblogs.microsoft.com/search?query=unit+testing)
