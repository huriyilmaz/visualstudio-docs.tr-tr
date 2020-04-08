---
title: Test için Tanılama Veri Bağdaştırıcısı Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2eadce12890e483f1b1c7aafccb61d9a6ee28e3a
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880305"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Özel veri toplamak veya bir test makinesini etkilemek için tanılama veri bağdaştırıcısı oluşturun

Bir test çalıştırdığınızda veri toplamak için kendi tanılama veri bağdaştırıcınızı oluşturmak veya testinizin bir parçası olarak test makinesini etkilemek isteyebilirsiniz. Örneğin, uygulamanız tarafından oluşturulan günlük dosyalarını test altında toplamak ve bunları test sonuçlarınıza eklemek veya bilgisayarınızda sınırlı disk alanı kaldığında testlerinizi çalıştırmak isteyebilirsiniz. Visual Studio Enterprise'da sağlanan API'leri kullanarak, test çalışmanızdaki belirli noktalarda görevleri gerçekleştirmek için kod yazabilirsiniz. Örneğin, bir test çalışması başladığında, her test çalıştırıldığından önce ve sonra ve test çalışması bittiğinde görevleri gerçekleştirebilirsiniz.

::: moniker range="vs-2017"
Yapılandırma ayarları dosyasını kullanarak özel tanılama veri bağdaştırıcınıza varsayılan giriş sağlayabilirsiniz. Örneğin, toplamak ve test sonuçlarınıza eklemek istediğiniz dosyanın konumu veya sistemde ne kadar disk alanı kalmak istediğiniz hakkında bilgi sağlayabilirsiniz. Bu veriler oluşturduğunuz her test ayarları için yapılandırılabilir. Microsoft Test Manager ile sağlanan varsayılan düzenleyici kullanılarak görüntülenebilir ve düzenlenebilir veya düzenleyici olarak kullanmak üzere kendi kullanıcı denetiminizi oluşturabilirsiniz. Düzenleyicinizdeki bağdaştırıcı yapılandırmasında yapılan tüm değişiklikler test ayarlarınızla birlikte depolanır.
::: moniker-end

::: moniker range=">=vs-2019"
Yapılandırma ayarları dosyasını kullanarak özel tanılama veri bağdaştırıcınıza varsayılan giriş sağlayabilirsiniz. Örneğin, toplamak ve test sonuçlarınıza eklemek istediğiniz dosyanın konumu veya sistemde ne kadar disk alanı kalmak istediğiniz hakkında bilgi sağlayabilirsiniz. Bu veriler oluşturduğunuz her test ayarları için yapılandırılabilir. Editör olarak kullanmak için kendi kullanıcı denetiminizi oluşturabilirsiniz. Düzenleyicinizdeki bağdaştırıcı yapılandırmasında yapılan tüm değişiklikler test ayarlarınızla birlikte depolanır.
::: moniker-end

Testlerinizi Visual Studio'dan çalıştırıyorsanız, bu test ayarlarını etkin olacak şekilde ayarlamanız gerekir. Test ayarları hakkında daha fazla bilgi için [bkz.](../test/collect-diagnostic-information-using-test-settings.md)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Görevler

Tanılama Veri Bağdaştırıcıları oluşturmanıza yardımcı olmak için aşağıdaki konuları kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Tanılama Veri Bağdaştırıcısı Oluşturma:** Bir sınıf kitaplığı oluşturarak bir tanılama veri bağdaştırıcısı oluşturursunuz ve ardından testlerinizi çalıştırmak için kullandığınız bir test sistemini istediğiniz bilgileri toplamak veya etkilemek için tanılama veri bağdaştırıcısı API'lerini kullanırsınız.|-   [Nasıl kullanılır: Tanılama veri bağdaştırıcısı oluşturma](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Testler Çalıştırıldığında Kullanılacak Özel Tanılama Veri Bağdaştırıcısı Seçme:** Test ayarlarınız için hangi tanılama veri bağdaştırıcısını kullanacağınızı seçebilirsiniz, böylece testlerinizi çalıştırdığınızda bağdaştırıcı kullanılır.|-   [Test ederken tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [El ile yapılan testlerde tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
