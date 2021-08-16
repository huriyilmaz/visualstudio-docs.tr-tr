---
title: Yük Testi Çalıştırma Ayarına Bağlam Parametreleri Ekleme
description: Bir dizeyi parametreleştirmeniz için bir yük testi çalıştırma ayarında Yük Testi Düzenleyicisi parametreleri oluşturma hakkında bilgi.
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
ms.openlocfilehash: b128d2b12447b1547237060ab6e18f899bc60eef6ab489ccd1f7f57a78f33b94
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121299831"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>Nasıl olur: Yük testi çalıştırma ayarına bağlam parametreleri ekleme

Yük testini New Yük Testi Sihirbazı kullanarak **oluşturdukktan** sonra, Yük Testi Düzenleyicisi  özelliklerini test Yük Testi Düzenleyicisi hedeflerinizi karşılayacak şekilde değiştirmek için kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Çalıştırma ayarları özelliklerinin ve açıklamalarının tam listesi için [bkz. Test çalıştırması ayarları özelliklerini yükleme.](../test/load-test-run-settings-properties.md)

Yük testi çalıştırması ayarında kullanmak üzere bağlam parametrelerini oluşturmak için Yük Testi Düzenleyicisi. Bağlam parametreleri, bir dizeyi parametreleştirmeye izin verir.

Yük testinde zaten bir bağlam parametresi kullanılarak parametreli web sunucusu URL'si kullanan bir web performans testi olduğunu varsayalım. Yük testi çalıştırma ayarına, web performans testinde kullanılanla aynı ad değerini kullanan bir bağlam parametresi eklemek için kullanabilirsiniz. Bu, yük testini çalıştırarak web performans testini farklı bir sunucuyla eşler. Örneğin, yük testinde URL'de web sunucusunun adı olarak WebServer1 adlı bir bağlam parametresi kullanan bir web performans testi varsa. Daha sonra yük testi çalıştırma ayarında WebServer1 olarak da adlandırılmış bir bağlam parametresi belirtirseniz yük testi, yük testi çalıştırma ayarında atadığı bağlam parametresini kullanır. Netleştirmek için, yük testinde web performans testi yük testinde bağlam parametresiyle aynı bağlam parametresi adını kullanıyorsa, yük testinde bağlam parametresi web performans testinde kullanılan bağlam parametresini geçersiz kılar.

> [!WARNING]
> Bir çalıştırma ayarında bağlam parametrelerini kullanırken web performans testinin bağlam parametresini irdeden geçersiz kılmama konusunda dikkatli olun. Bunu kasıtlı olarak yapmadıkça aynı bağlam parametresi adlarını kullanmaktan kaçının.

Webserver1 bağlam parametresinin değerini uygulamasına atarsanız, yük testi boyunca kullanabilir ve böylece değeri istediğiniz zaman kolayca farklı bir `http://CorporateStagingWebServer` `WebServer1` web sunucusuna değiştirebilirsiniz.

Ayrıca, farklı yük testi çalıştırma ayarlarında aynı adı kullanarak bir bağlam parametresine farklı değerler ataarak, yük testini farklı ortamlar kullanarak çalıştırabilirsiniz:

- Kurumsal Hazırlama Web Sunucusu çalıştırma ayarı: adlı bağlam parametresi `WebServer1=http://CorporateStagingWebServer`

- Kurumsal Üretim Web Sunucusu çalıştırma ayarı: Adlı Bağlam parametresi `WebServer1=http://CorporateProductionWebServer`

  **Komut Satırı'dan Çalıştırma Ayarını Değiştirme**

  Bağlam parametresi stratejisini kullanmak için komut satırına göre farklı çalıştırma ayarları kullanmak için aşağıdaki komutları kullanın:

  **Test.UseRunSetting= CorporateStagingWebServer'ı ayarlama**

  -and-

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>Bir çalıştırma ayarına bağlam parametresi eklemek için

1. Yük testi açın.

2. Çalışma alanı **Ayarlar** yük testi ağacında Çalıştır klasörünü Yük Testi Düzenleyicisi.

3. Bağlam parametresi eklemek istediğiniz belirli bir çalıştırma ayarına sağ tıklayın ve Bağlam Parametresi **Ekle'yi seçin.**

     Yük testi ağacının Run **Ayarlar** context **Parameters** klasörüne yeni bir bağlam parametresi eklenir.

     -veya-

     Çalıştırma ayarı zaten bir Bağlam Parametreleri **klasörü içeriyorsa,** buna sağ tıklar ve Bağlam Parametresi **Ekle'yi seçebilirsiniz.**

4. Özellikler **penceresinde** Ad değerini uygun **şekilde** değiştirin (örneğin, WebServer1). Özellikler **penceresinde,** **Değer'i** kullanmak istediğiniz parametreyle değiştirin (örneğin, `http://CorporateStagingWebServer` ).

5. (İsteğe bağlı) 3 ile 5 arasında adımları tekrarlayın ve **Value** özelliği için farklı bir dize kullanın (örneğin, `http://CorporateProductionWebServer` ).

6. Etkin olmak istediğiniz çalıştırma ayarlarını seçin. Çalıştırma ayarlarında kısayol menüsünü açın ve Etkin Olarak **Ayarla'yı seçin.**

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md)
