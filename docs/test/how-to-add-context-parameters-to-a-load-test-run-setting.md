---
title: Yük Testi Çalıştırma Ayarına Bağlam Parametreleri Ekleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 05efbba005a9455af3b9d2e8755b580a8af30d0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584484"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Nasıl kullanılır: Yük testi çalıştırma ayarına bağlam parametreleri ekleme

**Yeni Yük Testi Sihirbazı'nı**kullanarak yük testinizi oluşturduktan sonra, test gereksinimlerinizi ve hedeflerinize ulaşmak için senaryo özelliklerini değiştirmek için Yük Testi Düzenleyicisi'ni kullanabilirsiniz. **Load Test Editor**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi [için, Yükle testi çalıştırma ayarları özelliklerine](../test/load-test-run-settings-properties.md)bakın.

Yük Testi Düzenleyicisi'ni kullanarak yük testi çalıştırma ayarında kullanılacak bağlam parametreleri oluşturabilirsiniz. Bağlam parametreleri bir dize parametrenize izin sağlar.

Yük testinizin bağlam parametresi kullanarak zaten parametrelendirilmiş bir web sunucusu URL'si kullanan bir web performans testi içerdiğini varsayalım. Web performans testinde kullanılan ad değeriyle aynı ad değerini kullanan bir yük testi çalışması ayarına bağlam parametresi ekleyebilirsiniz. Bu, yük testini çalıştırdığınızda web performans testini farklı bir sunucuyla eşler. Örneğin, yük testiniz, URL'deki web sunucusunun adı için WebServer1 adlı bağlam parametresi kullanan bir web performans testi içeriyorsa. Daha sonra yük testi çalıştırma ayarnızda WebServer1 olarak da adlandırılan bir bağlam parametresi belirtirseniz, yük testi yük testi çalıştırma ayarında atadığınız bağlam parametresini kullanır. Açıklığa kavuşturmak için, yük testindeki web performans testi, yük testinde bağlam parametresi olarak aynı bağlam parametresi adını kullanıyorsa, yük testindeki bağlam parametresi web performans testinde kullanılan bağlam parametresini geçersiz kılar.

> [!WARNING]
> Çalışma ortamında bağlam parametrelerini kullandığınızda, web performans testinin bağlam parametresini istemeden geçersiz kılmamaya dikkat edin. Bunu kasıtlı olarak yapmazsanız aynı bağlam parametre adlarını kullanmaktan kaçının.

Webserver1 bağlam parametresinin değerini `http://CorporateStagingWebServer`yüklerseniz, yükleme testi `WebServer1` boyunca kullanabilirsiniz ve bu nedenle değeri istediğiniz zaman kolayca farklı bir web sunucusuna değiştirebilirsiniz.

Ayrıca, farklı yük testi çalıştırma ayarlarında aynı adı kullanarak bağlam parametresine farklı değerler atayarak, farklı ortamlar kullanarak yük testini çalıştırabilirsiniz:

- Kurumsal Evreleme Web Server çalıştırma ayarı: Adlı bağlam parametresi`WebServer1=http://CorporateStagingWebServer`

- Kurumsal Üretim Web Sunucusu çalıştırma ayarı: Bağlam parametresi adlı`WebServer1=http://CorporateProductionWebServer`

  **Komut Satırından Çalıştırma Ayarını Değiştirme**

  Bağlam parametre stratejisinden yararlanmak için komut satırından farklı çalışma ayarlarını kullanmak istiyorsanız, aşağıdaki komutları kullanın:

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  -ve-

  **mstest /testkonteyneri:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Çalışma ayarına bağlam parametresi eklemek için

1. Bir yük testi açın.

2. Yük Testi Düzenleyicisi'ndeki yük testi ağacındaki **Çalıştır Ayarları** klasörünü genişletin.

3. Bağlam parametresi eklemek istediğiniz belirli çalıştırma ayarını sağ tıklatın ve ardından **Bağlam Parametresi Ekle'yi**seçin.

     Yük testi ağacındaki **Çalıştır Ayarları** klasöründeki **Bağlam Parametreleri** klasörüne yeni bir bağlam parametresi eklenir.

     -veya-

     Çalıştırma ayarı zaten bir **Bağlam Parametreleri** klasörü içeriyorsa, sağ tıklayıp **Bağlam Parametresi Ekle'yi**seçebilirsiniz.

4. **Özellikler** penceresinde, **Ad** değerini uygun olarak değiştirin (örneğin, WebServer1). **Özellikler** penceresinde, **Değeri** kullanmak istediğiniz parametreyle değiştirin (örneğin, `http://CorporateStagingWebServer`).

5. (İsteğe bağlı) 3'ten 5'e kadar olan **Value** adımları yineleyin ve `http://CorporateProductionWebServer`Değer özelliği için farklı bir dize kullanın (örneğin, ).

6. Etkin olmak istediğiniz çalışma ayarlarını seçin. Çalıştırma ayarlarındaki kısayol menüsünü açın ve **Etkin Olarak Ayarla'yı**seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
