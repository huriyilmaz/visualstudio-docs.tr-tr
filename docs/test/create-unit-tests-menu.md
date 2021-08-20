---
title: Birim testi yöntemi saplamaları oluşturma
description: Bir test projesinin, test sınıfının ve test yöntemi saplamanın kolayca yapılandırmasını sağlayan Birim Testleri Oluştur komutunu kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/19/2021
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 35eb729b08e969ded00bb2f6eb428ccdfece1032
ms.sourcegitcommit: e6aeefef5b659a56e6e433d155bfd269c46bceb0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2021
ms.locfileid: "122603586"
---
# <a name="create-unit-test-method-stubs-from-code"></a>Koddan birim testi yöntemi saplamaları oluşturma

Birim **Testleri Oluştur komutu** birim testi yöntemi saplamaları oluşturur. Bu özellik, test projesinin, test sınıfının ve test yöntemi saplamanın kolayca yapılandırmasını sağlar.

::: moniker range="vs-2017"
> [!NOTE]
> Birim **Testleri Oluştur menü** komutu yalnızca .NET Core veya .NET Framework'yi .NET Framework C# kodu için .NET Standard.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> Birim **Testleri Oluştur menü** komutu yalnızca C# kodu için kullanılabilir. Bu yöntemi .NET Core veya .NET Standard kullanmak için Visual Studio 2019 gerekir.
::: moniker-end

Birim **Testleri Oluştur menü** komutu genişletilebilir ve MSTest, MSTest V2, NUnit ve xUnit için testler oluşturmak için kullanılabilir.

## <a name="get-started"></a>başlarken

Çalışmaya başlamanız için test etmek istediğiniz projede kod düzenleyicisinde bir yöntem, tür veya ad alanı seçin, sağ tıklayın ve Birim Testleri **Oluştur'u seçin.** Birim **Testleri Oluştur** iletişim kutusu açılır ve burada testlerin nasıl oluşturulacaklarını yapılandırabilirsiniz.

![Birim testleri oluştur komutunu kullanma](media/createunittestcommand.png)

NUnit veya xUnit için test çerçevesi seçeneklerini görmüyorsanız bkz. Üçüncü taraf [birim test çerçevelerini kullanma.](#use-third-party-unit-test-frameworks)

## <a name="set-unit-test-traits"></a>Birim testi niteliklerini ayarlama

Bu testleri test otomasyonu işleminin bir parçası olarak çalıştırmayı planlıyorsanız, testin başka bir test projesinde (yukarıdaki iletişim kutusundaki ikinci seçenek) oluşturulmuş ve birim testi için birim testi niteliklerini ayarlamayı düşünebilirsiniz. Bu, bu belirli testleri sürekli tümleştirme veya sürekli dağıtım işlem hattının bir parçası olarak dahil etmek veya dışlamak için daha kolay bir şekilde olanak sağlar. Nitelikler, aşağıda gösterildiği gibi doğrudan birim testinde meta veriler eklenmiştir.

![Birim testi niteliklerini ayarlama](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Üçüncü taraf birim testi çerçevelerini kullanma

NUnit veya xUnit için birim testlerini otomatik olarak oluşturmak için Market'te şu test çerçevesi uzantılarından Visual Studio yükleyin:

* [Test oluşturucuları için NUnit uzantısı](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371)
* [xUnit.net oluşturucular için bir uzantı](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator)

## <a name="when-should-i-use-this-feature"></a>Bu özelliği ne zaman kullan gerekir?

Birim testleri oluşturmanız gereken her durumda, ancak özellikle çok az test kapsamına sahip veya hiç belgesi olan mevcut kodu test ediyorsanız bu özelliği kullanın. Başka bir deyişle, sınırlı veya mevcut olmayan kod belirtimi vardır. Kodun gözlemlenen davranışını ifade [etmek için Akıllı](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) birim testlerinde olduğu gibi etkili bir yaklaşım benimser.

Ancak, bir geliştirici bazı kodlar yazarak başladığında ve ardından birim testlerini önyüklemek için bunu kullandığında bu özellik de aynı şekilde geçerlidir. Kod akışı içinde geliştirici, belirli bir kod parçası için hızla bir birim testi yöntemi saplama (uygun bir test sınıfı ve uygun bir test projesi ile) oluşturmak istiyor olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- ["Birim Testleri Oluştur" ile birim testi yöntemi saplamaları oluşturma](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Birim testi blog gönderileri](https://devblogs.microsoft.com/devops/?s=unit+testing)
