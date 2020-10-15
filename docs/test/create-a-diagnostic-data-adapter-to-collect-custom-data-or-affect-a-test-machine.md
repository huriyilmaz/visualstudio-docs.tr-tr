---
title: Test için tanılama veri bağdaştırıcısı oluşturma
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 65d311ec522e5ba5b5c92193a8af3e53a9e9eb35
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099329"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Özel veri toplamak veya bir test makinesini etkilemek için bir tanılama veri bağdaştırıcısı oluşturma

Bir testi çalıştırdığınızda veri toplamak için kendi tanılama veri bağdaştırıcınızı oluşturmak veya testinizin bir parçası olarak test makinesini etkilemek isteyebilirsiniz. Örneğin, test kapsamındaki uygulamanız tarafından oluşturulan günlük dosyalarını toplamak ve bunları test sonuçlarınıza eklemek isteyebilirsiniz veya bilgisayarınızda sınırlı disk alanı kalmadığında testlerinizi çalıştırmak isteyebilirsiniz. Visual Studio Enterprise içinde sunulan API 'Leri kullanarak, test çalıştırinizdeki belirli noktalarda görevler gerçekleştirmek için kod yazabilirsiniz. Örneğin, bir test çalıştırması başlatıldığında, her bir test çalıştırılmadan önce ve sonra ve test çalıştırması tamamlandığında görevleri gerçekleştirebilirsiniz.

::: moniker range="vs-2017"
Bir yapılandırma ayarları dosyası kullanarak özel tanılama veri bağdaştırıcınıza varsayılan giriş sağlayabilirsiniz. Örneğin, toplamak istediğiniz dosyanın konumu ve test sonuçlarınıza eklemek veya sistemde ne kadar disk alanı açmak istediğinize ilişkin bilgiler sağlayabilirsiniz. Bu veriler, oluşturduğunuz her test ayarı için yapılandırılabilir. Microsoft Test Yöneticisi ile birlikte sunulan varsayılan düzenleyici kullanılarak görüntülenebilir ve düzenlenebilir veya bir düzenleyici olarak kullanmak için kendi Kullanıcı denetiminizi oluşturabilirsiniz. Düzenleyicinizdeki bağdaştırıcı yapılandırmasında yapılan tüm değişiklikler, test ayarlarınızla birlikte depolanır.
::: moniker-end

::: moniker range=">=vs-2019"
Bir yapılandırma ayarları dosyası kullanarak özel tanılama veri bağdaştırıcınıza varsayılan giriş sağlayabilirsiniz. Örneğin, toplamak istediğiniz dosyanın konumu ve test sonuçlarınıza eklemek veya sistemde ne kadar disk alanı açmak istediğinize ilişkin bilgiler sağlayabilirsiniz. Bu veriler, oluşturduğunuz her test ayarı için yapılandırılabilir. Bir düzenleyici olarak kullanmak için kendi Kullanıcı denetiminizi oluşturabilirsiniz. Düzenleyicinizdeki bağdaştırıcı yapılandırmasında yapılan tüm değişiklikler, test ayarlarınızla birlikte depolanır.
::: moniker-end

Testlerinizi Visual Studio 'dan çalıştırıyorsanız, bu test ayarlarını etkin olacak şekilde ayarlamanız gerekir. Test ayarları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Görevler

Tanılama veri bağdaştırıcıları oluşturmanıza yardımcı olması için aşağıdaki konuları kullanın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Tanılama veri bağdaştırıcısı oluşturma:** Bir sınıf kitaplığı oluşturarak bir tanılama veri bağdaştırıcısı oluşturun ve ardından, istediğiniz bilgileri toplamak veya testlerinizi çalıştırmak için kullandığınız bir test sistemini etkilemek için tanılama veri bağdaştırıcısı API 'Lerini kullanın.|-   [Nasıl yapılır: tanılama veri bağdaştırıcısı oluşturma](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Testler çalıştırıldığında kullanılacak özel bir tanılama veri bağdaştırıcısı seçme:** Testlerinizi çalıştırdığınızda bağdaştırıcının kullanılması için, test ayarlarınız için hangi tanılama veri bağdaştırıcısının kullanılacağını seçebilirsiniz.|-   [Test sırasında tanılama verilerini topla (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)<br />-   [Tanılama verilerini el ile testlerde topla (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)|

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)