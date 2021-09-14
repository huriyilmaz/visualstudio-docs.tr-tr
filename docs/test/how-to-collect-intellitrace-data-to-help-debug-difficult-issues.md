---
title: IntelliTrace verileri
description: IntelliTrace için tanılama veri bağdaştırıcısını yapılandırmayı ve bu bağdaştırıcıda belirli tanılama izleme bilgilerini toplamayı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: f25c0b0e2ab80ac61b0256d1b4af2e95c02b2382
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628154"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Nasıl kullanılır: Zor sorunlarda hata ayıklamaya yardımcı olmak için IntelliTrace verileri toplama

IntelliTrace için tanılama veri bağdaştırıcısını yapılandırarak belirli tanılama izleme bilgilerini Visual Studio. Testler bu bağdaştırıcıyı kullanabilir, test, uygulama için büyük miktarda tanılama olayları toplayabilir ve sonrasında bir geliştirici bu olayları, kodu izleyip bir hatanın nedenini bulmak üzere kullanabilir. IntelliTrace için tanılama veri bağdaştırıcısı, el ile veya otomatikleştirilmiş testler için kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace yalnızca yönetilen kod kullanılarak yazılan bir uygulamada çalışır. İstemci olarak tarayıcı kullanan bir web uygulamasını test ediyorsanız, izleme için yönetilen kod mevcut olduğundan, test ayarlarınıza istemci için IntelliTrace'i etkinleştirmeniz gerekir. Bu durumda, bir ortam ayarlamak ve web sunucunuzda IntelliTrace verilerini uzaktan toplamak istiyor olabilirsiniz.

IntelliTrace verileri.iTrace uzantısına sahip bir *dosyada depolanır.* Testlerinizi çalıştırarak bir test adımı başarısız olduğunda hata oluşturabilirsiniz. Tanılama bilgilerini içeren IntelliTrace dosyası bu hataya otomatik olarak eklenir.

> [!NOTE]
> IntelliTrace için tanılama veri bağdaştırıcısı, bir test başarılı olduğunda IntelliTrace dosyası oluşturmaz. Bir dosyayı yalnızca başarısız bir test çalışmasına veya hata gönderdiğinizde kaydeder.

IntelliTrace dosyasında toplanan veriler, kodundaki bir hatayı yeniden oluşturmak ve tanılamak için gereken zamanı azaltarak hata ayıklama üretkenliğini artırır. Buna ek olarak, IntelliTrace dosyasını kendi bilgisayarlarında yerel oturumlarınızı çoğaltacak başka bir bireyle paylaşabilirsiniz, çünkü bir hatanın yeniden tekrarlanamaz olma olasılığını azaltır.

> [!NOTE]
> Test ayarlarınıza IntelliTrace'i etkinleştirirsiniz, kod kapsamı verilerini toplama çalışmaz.

> [!WARNING]
> IntelliTrace için tanılama veri bağdaştırıcısı, test çalıştırması için testler yüklendikten sonra gerçekleştirilecek yönetilen bir işlemi izlemeyle çalışır. İzlemek istediğiniz işlem zaten başlatıldı ise, işlem zaten çalışıyor olduğundan IntelliTrace dosyası toplanmaz. Bunu yapmak için testler yüklenmeden önce sürecin durdurul olduğundan emin olun. Ardından testler yüklendikten veya ilk test başlatıldıktan sonra işlemi başlat.

::: moniker range="vs-2017"
Aşağıdaki yordam, toplamak istediğiniz IntelliTrace verilerini yapılandırmayı açıklar. Bu adımlar hem Microsoft Test Yöneticisi'daki yapılandırma düzenleyicisi hem de Ayarlar iletişim kutusunda Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki yordam, toplamak istediğiniz IntelliTrace verilerini yapılandırmayı açıklar. Bu adımlar, Ayarlar test Visual Studio.
::: moniker-end

> [!NOTE]
> IntelliTrace verilerini toplamak için kullanılan test aracısı kullanıcı hesabının yöneticiler grubunun bir üyesi olması gerekir. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace tanılama veri bağdaştırıcısı ile veri toplayan verileri yapılandırma

::: moniker range="vs-2017"
Bu yordamda yer alan adımları gerçekleştirmeden önce test ayarlarınızı Microsoft Test Yöneticisi veya Visual Studio ve Tanılama **sayfasını seçmeniz** gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
Bu yordamda yer alan adımları gerçekleştirmeden önce test ayarlarınızı Visual Studio ve Tanılama **sayfasını seçmeniz** gerekir.
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace tanılama veri bağdaştırıcısı ile toplayan verileri yapılandırmak için

1. IntelliTrace verilerini toplamak için kullanmak istediğiniz rolü seçin.

2. **IntelliTrace'i seçin.**

3. Bir web istemcisi rolü veya ASP.NET web uygulaması için IntelliTrace ekliyorsanız, **IntelliTrace** ve Test Etkisi için ASP.NET Proxy'yi de seçmeniz gerekir.

     Bu ara sunucu, IntelliTrace ve Test Etkisi tanılama veri bağdaştırıcıları için istemciden web sunucusuna yapılan http çağrıları hakkında bilgi toplamaya olanak sağlar.

    > [!WARNING]
    > IntelliTrace verilerini toplamak istediğiniz Internet Information Server'da (IIS) uygulama havuzu için kullanılan kimlik için özel bir hesap kullanmaya karar veriyorsanız, kullanılan özel hesap için IIS makinesi üzerinde yerel kullanıcı profilini oluşturmanız gerekir. Iis makinesine bir kez yerel olarak oturum açmak veya özel hesap kimlik bilgilerini kullanarak aşağıdaki komut satırı çalıştırarak özel hesap için yerel profili oluşturabilirsiniz:
    >
    > **runas /user:domain\name /profile cmd.exe**

4. Varsayılan  **IntelliTrace ayarlarını değiştirmek için IntelliTrace** için Yapılandır'ı seçin.

     Toplanacak verileri yapılandırma iletişim kutusu görüntülenir.

    > [!WARNING]
    > IntelliTrace verilerini toplamayı etkinleştirirsanız kod kapsamı verilerini toplama çalışmaz.

5. Genel **sekmesini** seçin. Testte performansı en az etkileyen önemli tanılama olaylarını kaydetmek için **IntelliTrace** olaylarını seçin.

     -veya-

     Tanılama olaylarını ve çağrı bilgilerini gösteren yöntem düzeyinde izlemeyi kaydetmek için **IntelliTrace** olaylarını ve çağrı bilgilerini seçin. Testlerinizi çalıştırarak bu izleme düzeyinin performans üzerinde etkisi olabilir.

6. Internet Information Services üzerinde ASP.NET uygulamanıza veri toplamak için, Internet Information Services üzerinde **çalışan ASP.NET** uygulamalardan veri Internet Information Services. Web sunucusu rolünde test aracınızı ayarlayın ve yapılandırabilirsiniz. Bkz. [Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

7. Modüller **sekmesini** seçin. Aşağıdakiler **dışında tüm modüllerden veri** topla'ya tıklayın ve modül listesine eklemek için **Ekle'yi** ve bir modülü kaldırmak için **Kaldır'ı** kullanın. Bu seçenek, belirttiğiniz modüller dışında sistemde çalışan tüm modülleri dahil edersiniz.

     -veya-

     Yalnızca **aşağıdaki modüllerden veri toplayın'ı seçin ve** modül listesine eklemek için **Ekle'yi,** bir modülü kaldırmak için **Kaldır'ı** kullanın. Bu seçenek tam olarak istediğiniz modülleri belirtmenize olanak sağlar.

    > [!NOTE]
    > Mümkünse, izlemek istediğiniz belirli işlemleri seçin. Bu, en iyi performans için önerilir.

8. İşlemler **sekmesini** seçin. Aşağıdakiler **dışında tüm işlemlerden veri** topla'ya tıklayın ve ekle'yi kullanarak işlem listesine ekleyin ve **Kaldır'ı** kullanarak bir işlemi kaldırın.  Bu seçenek, belirttiğiniz işlemler dışında sistemde çalışan tüm işlemleri dahil etmek için kullanılabilir.

     -veya-

     Yalnızca **belirtilen işlemlerden veri topla'ya tıklayın** ve **ekle'yi** kullanarak işlem listesine ekleyin ve **Kaldır'ı** seçerek bir işlemi kaldırın. Bu seçenek, tam olarak istediğiniz işlemleri belirtmenize olanak sağlar.

9. (İsteğe bağlı) **IntelliTrace Olayları sekmesini** seçin. Tanılama olaylarını toplayan dahil etmek veya hariç tutmak istediğiniz her IntelliTrace olay kategorisini seçin veya silin.

10. (İsteğe bağlı) Her IntelliTrace olay kategorisini genişletin ve IntelliTrace olaylarını dahil etmek veya hariç tutmak istediğiniz belirli olayları seçin veya silin.

11. (İsteğe bağlı) Gelişmiş **sekmesini** seçin. Ardından, Kayıt için **maksimum disk** alanı miktarı'nın yanındaki oku seçin ve IntelliTrace dosyasının kullanılası için etkinleştirmek istediğiniz maksimum boyutu seçin.

    > [!NOTE]
    > Kaydın boyutunu artırdısanız, bu kaydı test sonuçlarınızla birlikte kaydederken bir zaman out sorunu oluşabilir.

12. Microsoft Test Yöneticisi 2017'de Visual Studio kullanıyorsanız Kaydet'i **seçin.** Uygulama kullanıyorsanız Visual Studio'yi **seçin.** IntelliTrace ayarları artık yapılandırıldı ve test ayarlarınız için kaydedildi.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını  sıfırlamak için, Visual Studio  için varsayılan yapılandırmaya sıfırla veya Microsoft Test Yöneticisi.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını sıfırlamak için Bu tanılama veri **bağdaştırıcısında varsayılan yapılandırmaya** sıfırla'Visual Studio.
    ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test sırasında tanılama verilerini toplama (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)
- [Tanılama verilerini el ile yapılan testlerde toplama (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
