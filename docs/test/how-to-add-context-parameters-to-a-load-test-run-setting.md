---
title: Yük testi çalışma ayarına bağlam parametreleri ekleme
description: Bir dizeyi parametreetmenize olanak sağlayan Yük Testi Düzenleyicisi kullanarak yük testi çalıştırma ayarında kullanmak için bağlam parametreleri oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 3a843f6991f77886c6b5b5b0fb3943b720790698
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026695"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Nasıl yapılır: yük testi çalışma ayarına bağlam parametreleri ekleme

**Yeni Yük Testi Sihirbazı** kullanarak yük testinizi oluşturduktan sonra, test ihtiyaçlarını ve hedeflerinizi karşılamak üzere senaryolar özelliklerini değiştirmek için **Yük Testi Düzenleyicisi** kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Çalışma ayarları özelliklerinin tam listesi ve açıklamaları için bkz. [Yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).

Yük Testi Düzenleyicisi kullanarak yük testi çalıştırma ayarında kullanmak için bağlam parametreleri oluşturabilirsiniz. Bağlam parametreleri bir dizeyi parametreleştirietmenize olanak tanır.

Yük testiniz bir bağlam parametresi kullanarak zaten parametreli bir Web sunucusu URL 'SI kullanan bir Web performans testi içerdiğini varsayalım. Web performans testinde kullanılan ile aynı ad değerini kullanan bir yük testi çalıştırma ayarına bağlam parametresi ekleyebilirsiniz. Bu işlem, yük testini çalıştırdığınızda Web performans testini farklı bir sunucuya eşler. Örneğin, yük testiniz URL 'deki Web sunucusunun adı için WebServer1 adlı bir bağlam parametresi kullanan bir Web performans testi içeriyorsa. Daha sonra, WebServer1 adlı yük testi çalışma ayarınız içinde bir bağlam parametresi belirtirseniz, yük testi yük testi çalıştırma ayarında atadığınız bağlam parametresini kullanır. Netleştirmek için, yük testinde Web performans testi, yük testinde bir bağlam parametresi olarak aynı bağlam parametresi adını kullanıyorsa, yük testindeki bağlam parametresi, Web performans testinde kullanılan bağlam parametresini geçersiz kılar.

> [!WARNING]
> Bir çalışma ayarında bağlam parametreleri kullandığınızda bir Web performans testinin bağlam parametresini istenmeden geçersiz kılmamaya dikkat edin. Bunu bilerek yapmadığınız takdirde aynı bağlam parametresi adlarını kullanmaktan kaçının.

WebServer1 context parametresinin değerini sürümüne atarsanız `http://CorporateStagingWebServer` , daha sonra `WebServer1` Yük testi boyunca kullanabilirsiniz ve bu sayede değeri dilediğiniz zaman farklı bir Web sunucusuna kolayca değiştirebilirsiniz.

Ayrıca, farklı yük testi çalışma ayarlarında aynı adı kullanarak bir bağlam parametresine farklı değerler atayarak, farklı ortamları kullanarak yük testini çalıştırabilirsiniz:

- Kurumsal hazırlama Web sunucusu çalıştırma ayarı: adlı bağlam parametresi `WebServer1=http://CorporateStagingWebServer`

- Kurumsal üretim Web sunucusu çalıştırma ayarı: adlı bağlam parametresi `WebServer1=http://CorporateProductionWebServer`

  **Çalıştırma ayarını komut satırından değiştirme**

  Bağlam parametresi stratejisinden faydalanmak için komut satırından farklı çalışma ayarları kullanmak istiyorsanız aşağıdaki komutları kullanın:

  **Test. UseRunSetting = CorporateStagingWebServer ayarla**

  '

  **MSTest/testcontainer: LoadTest1. LoadTest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Bir çalıştırma ayarına bağlam parametresi eklemek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi yük testi ağacındaki **Run Ayarlar** klasörünü genişletin.

3. Bağlam parametresi eklemek istediğiniz özel çalıştırma ayarına sağ tıklayın ve sonra **Bağlam parametresi Ekle**' yi seçin.

     yük testi ağacındaki **Run Ayarlar** klasöründeki **bağlam parametreleri** klasörüne yeni bir bağlam parametresi eklenir.

     -veya-

     Çalıştırma ayarı zaten bir **Bağlam parametreleri** klasörü içeriyorsa, sağ tıklayıp **Bağlam parametresi Ekle**' yi seçebilirsiniz.

4. **Özellikler** penceresinde, **ad** için değeri uygun şekilde değiştirin (örneğin, WebServer1). **Özellikler** penceresinde, **değerini** kullanmak istediğiniz parametreye değiştirin (örneğin, `http://CorporateStagingWebServer` ).

5. Seçim 3 ile 5 arasındaki adımları yineleyin ve **değer** özelliği için farklı bir dize kullanın (örneğin, `http://CorporateProductionWebServer` ).

6. Hangi çalıştırma ayarlarının etkin olmasını istediğinizi seçin. Çalıştır ayarları ' nın kısayol menüsünü açın ve **etkin olarak ayarla**' yı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandır](../test/configure-load-test-run-settings.md)
