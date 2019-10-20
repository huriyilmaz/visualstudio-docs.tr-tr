---
title: Birim testi yöntemi saplamaları oluştur
ms.date: 04/01/2019
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3edd4694688011722b9975d299bd09cfb3832a9e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665077"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>Birim Testleri Oluştur komutuyla birim testi yöntemi saplamaları oluşturma

**Birim Testleri Oluştur** komutu birim testi yöntemi saplamaları oluşturur. Bu özellik bir test projesinin, test sınıfının ve içindeki test yönteminin Saplamasının kolay yapılandırılmasını sağlar.

> [!NOTE]
> **Birim Testleri Oluştur** menü komutu yalnızca .NET Framework (.NET Core) hedefleyen yönetilen kod için kullanılabilir.

**Birim Testleri Oluştur** menü komutu genişletilebilir ve MSTest, MSTest v2, NUnit ve xUnit için testler oluşturmak üzere kullanılabilir.

## <a name="get-started"></a>Kullanmaya başlayın

Başlamak için, test etmek istediğiniz projedeki kod düzenleyicisinde bir yöntem, bir tür veya ad alanı seçin, sağ tıklayın ve ardından **Birim Testleri Oluştur**' u seçin. , Testlerin nasıl oluşturulmasını istediğinizi yapılandırabileceğiniz **Birim Testleri Oluştur** iletişim kutusu açılır.

![Birim Testleri Oluştur komutunu kullanma](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>Birim testi nitelikleri ayarla

Bu testleri test Otomasyonu sürecinin bir parçası olarak çalıştırmayı planlıyorsanız, testin başka bir test projesinde oluşturulmasını (yukarıdaki iletişim kutusunda ikinci seçenek) ve birim testi için birim testi nitelikleri ayarlamayı düşünebilirsiniz. Bu, sürekli tümleştirme veya sürekli dağıtım işlem hattının parçası olarak bu belirli testleri daha kolay bir şekilde dahil etmenizi veya dışlamanıza olanak sağlar. Bu nitelikler, aşağıda gösterildiği gibi, birim testine doğrudan meta veriler eklenerek ayarlanır.

![Birim testi nitelikleri ayarlanıyor](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>Üçüncü taraf birim testi çerçeveleri kullanma

NUnit veya xUnit için birim testlerini otomatik olarak oluşturmak için, bu test çerçevesi uzantılarından birini Visual Studio Market adresinden birine yüklersiniz:

* [Test oluşturucuları için NUnit uzantısı](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [test oluşturucuları için xUnit.net uzantısı](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>Bu özelliği ne zaman kullanmalıyım?

Birim testlerini her oluşturmanız gerektiğinde bu özelliği kullanın, ancak özellikle çok fazla test kapsamı ve hiç belge bulunmayan mevcut kodu test ederken. Diğer bir deyişle, sınırlı veya mevcut olmayan kod belirtimi. Kodun gözlemlenen davranışını gösteren [akıllı birim testlerine](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/) benzer bir yaklaşımı etkili bir şekilde uygular.

Ancak, bu özellik, bir geliştirici başlatıldığında bazı kod yazarak ve ardından birim testlerini önyüklemek için kullandığında aynı şekilde geçerlidir. Geliştirici, kodlama akışında, belirli bir kod parçası için hızlı bir şekilde birim testi yöntemi saplaması (uygun bir test sınıfı ve uygun bir test projesiyle birlikte) oluşturmak isteyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- ["Birim testleri oluştur" ile birim testi yöntemi saplamaları oluşturma](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)
- [Birim testi blog gönderileri](https://devblogs.microsoft.com/devops/?s=unit+testing)
