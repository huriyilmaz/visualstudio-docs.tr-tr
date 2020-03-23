---
title: Birim test yöntemi koçanları oluşturma
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3eb001d2022bb57981f21fd99c051c54aeb08301
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75844313"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Birim Testleri Oluştur komutu ile birim test yöntemi koçanları oluşturma

**Birim Testleri Oluştur** komutu birim test yöntemi koçanları oluşturur. Bu özellik, bir test projesinin, test sınıfının ve içindeki test yönteminin kolay yapılandırmasını sağlar.

::: moniker range="vs-2017"
> [!NOTE]
> **Birim Testleri Oluştur** menüsü komutu yalnızca .NET Framework'ü hedefleyen (ancak .NET Core'u hedeflemeyan) yönetilen kod için kullanılabilir.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> **Birim Testleri Oluştur** menüsü komutu yalnızca yönetilen kod için kullanılabilir.
::: moniker-end

**Birim Testleri Oluştur** menüsü genişletilebilir ve MSTest, MSTest V2, NUnit ve xUnit için testler oluşturmak için kullanılabilir.

## <a name="get-started"></a>Kullanmaya başlayın

Başlamak için, test etmek istediğiniz projedeki kod düzenleyicisinde bir yöntem, tür veya ad alanı seçin, sağ tıklatın ve ardından **Birim Testleri Oluştur'u**seçin. **Birim Testleri Oluştur** iletişim kutusu, testlerin nasıl oluşturulmasını istediğinizi yapılandırabileceğiniz bir şekilde açılır.

![Birim testleri oluştur komutunu kullanma](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Birim test özelliklerini ayarlama

Bu testleri test otomasyon sürecinin bir parçası olarak çalıştırmayı planlıyorsanız, testin başka bir test projesinde (yukarıdaki iletişim kutusundaki ikinci seçenek) oluşturulmasını ve birim testi için birim test özelliklerini ayarlamayı düşünebilirsiniz. Bu, sürekli tümleştirme veya sürekli dağıtım ardışık bir parçası olarak bu özel testleri daha kolay eklemenize veya hariç tutmanıza olanak tanır. Özellikler, aşağıda gösterildiği gibi, birim testine doğrudan meta veri eklenerek ayarlanır.

![Birim test özelliklerini ayarlama](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Üçüncü taraf birim test çerçevelerini kullanma

NUnit veya xUnit için birim testleri otomatik olarak oluşturmak için Visual Studio Marketplace'ten şu test çerçevesi uzantılarından birini yükleyin:

* [Test jeneratörleri için NUnit uzantısı](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [Test jeneratörleri için xUnit.net uzantısı](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Bu özelliği ne zaman kullanmalıyım?

Birim testleri oluşturmanız gerektiğinde, ancak özellikle çok az test kapsamı olan veya belgelemeolmayan varolan kodu sınarken bu özelliği kullanın. Başka bir deyişle, sınırlı veya var olmayan kod belirtimi vardır. Kodun gözlenen davranışını karakterize eden [Akıllı birim testlerine](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) benzer bir yaklaşımı etkili bir şekilde uygular.

Ancak, bu özellik, bir geliştirici bazı kod yazarak başlar ve daha sonra bootstrap birim testleri için kullanır eşit olarak geçerlidir. Kodlama akışı içinde, geliştirici hızlı bir şekilde belirli bir kod parçası için bir birim test yöntemi saplama (uygun bir test sınıfı ve uygun bir test projesi ile) oluşturmak isteyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- ["Birim Testleri Oluştur" ile birim test yöntemi koçanları oluşturma](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Birim test blog gönderileri](https://devblogs.microsoft.com/devops/?s=unit+testing)
