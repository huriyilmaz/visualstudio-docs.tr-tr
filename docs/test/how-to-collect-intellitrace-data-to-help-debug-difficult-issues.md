---
title: IntelliTrace verileri
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
manager: jillfra
ms.openlocfilehash: d0983967d42c6daa89b9a690b93fb97872e98603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288266"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Nasıl yapılır: hata ayıklama zor sorunlarını gidermek için IntelliTrace verilerini toplama

Visual Studio 'da belirli tanılama izleme bilgilerini toplamak üzere IntelliTrace için tanılama veri bağdaştırıcısını yapılandırabilirsiniz. Testler bu bağdaştırıcıyı kullanabilir, test, uygulama için büyük miktarda tanılama olayları toplayabilir ve sonrasında bir geliştirici bu olayları, kodu izleyip bir hatanın nedenini bulmak üzere kullanabilir. IntelliTrace için tanılama veri bağdaştırıcısı, el ile veya otomatikleştirilmiş testler için kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace yalnızca yönetilen kod kullanılarak yazılmış bir uygulama üzerinde çalışıyor. İstemci olarak tarayıcı kullanan bir Web uygulamasını test ediyorsanız, izleme için kullanılabilir yönetilen kod olmadığından test ayarlarınızda istemci için IntelliTrace 'i etkinleştirmemelisiniz. Bu durumda, bir ortam ayarlamak ve IntelliTrace verilerini Web sunucunuzda Uzaktan toplamak isteyebilirsiniz.

IntelliTrace verileri *. iTrace*uzantısına sahip bir dosyada depolanır. Testinizi çalıştırdığınızda bir test adımı başarısız olursa, bir hata oluşturabilirsiniz. Tanılama bilgilerini içeren IntelliTrace dosyası otomatik olarak bu hataya eklenir.

> [!NOTE]
> IntelliTrace için tanılama veri bağdaştırıcısı, test geçişi başarılı olduğunda bir IntelliTrace dosyası oluşturmaz. Dosyayı yalnızca başarısız bir test çalışmasında veya bir hata gönderdiğinizde kaydeder.

IntelliTrace dosyasında toplanan veriler, kodunuzda bir hata yeniden üretmek ve tanılamak için gereken süreyi azaltarak hata ayıklama verimliliğini artırır. Ayrıca, IntelliTrace dosyasını bilgisayarında yerel oturumunuzu çoğaltabilen başka bir kişi ile paylaşabileceğiniz bir hatanın yeniden denenebilme olasılığını azaltır.

> [!NOTE]
> Test ayarlarınızda IntelliTrace 'i etkinleştirirseniz, kod kapsamı verilerinin toplanması işe alınacaktır.

> [!WARNING]
> IntelliTrace için tanılama veri bağdaştırıcısı, test çalıştırması için testler yüklendikten sonra gerçekleştirilmesi gereken yönetilen bir işlem kullanılarak çalışır. İzlemek istediğiniz işlem zaten başlatılmışsa, işlem zaten çalıştığından hiçbir IntelliTrace dosyası toplanmayacaktır. Bunu aşmak için, testler yüklenmeden önce işlemin durdurulduğundan emin olun. Ardından, testler yüklendikten veya ilk test başladıktan sonra işlemi başlatın.

::: moniker range="vs-2017"
Aşağıdaki yordamda, toplamak istediğiniz IntelliTrace verilerinin nasıl yapılandırılacağı açıklanmaktadır. Bu adımlar, Visual Studio 'daki Microsoft Test Yöneticisi ve test ayarları iletişim kutusundaki Yapılandırma Düzenleyicisi için geçerlidir.
::: moniker-end
::: moniker range=">=vs-2019"
Aşağıdaki yordamda, toplamak istediğiniz IntelliTrace verilerinin nasıl yapılandırılacağı açıklanmaktadır. Bu adımlar, Visual Studio 'daki test ayarları iletişim kutusu için geçerlidir.
::: moniker-end

> [!NOTE]
> IntelliTrace verilerini toplamak için kullanılan test aracısının Kullanıcı hesabı, Yöneticiler grubunun bir üyesi olmalıdır. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace Tanılama veri bağdaştırıcısı ile toplanacak verileri yapılandırın

::: moniker range="vs-2017"
Bu yordamdaki adımları gerçekleştirmeden önce, Microsoft Test Yöneticisi veya Visual Studio 'dan test ayarlarınızı açmanız ve **veri ve tanılama** sayfasını seçmeniz gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
Bu yordamdaki adımları gerçekleştirmeden önce, Visual Studio 'dan test ayarlarınızı açmanız ve **veri ve tanılama** sayfasını seçmeniz gerekir.
::: moniker-end

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace Tanılama veri bağdaştırıcısı ile toplanacak verileri yapılandırmak için

1. IntelliTrace verilerini toplamak için kullanılacak rolü seçin.

2. **IntelliTrace**' i seçin.

3. Bir Web istemci rolü için veya bir ASP.NET Web uygulaması için IntelliTrace ekliyorsanız, **IntelliTrace ve test etkisi için ASP.net Istemci proxy 'sini**de seçmeniz gerekir.

     Bu proxy, IntelliTrace ve test etkisi tanılama veri bağdaştırıcıları için bir istemciden bir Web sunucusuna http çağrıları hakkında bilgi toplamanıza olanak sağlar.

    > [!WARNING]
    > IntelliTrace verilerini toplamak istediğiniz Internet Information Server 'da (IIS) uygulama havuzu için kullanılmakta olan kimlik için özel bir hesap kullanmaya karar verirseniz, kullanılmakta olan özel hesap için IIS makinesinde yerel kullanıcı profili oluşturmanız gerekir. Tek seferde IIS makinesinde yerel olarak oturum açarak veya özel hesap kimlik bilgilerini kullanarak aşağıdaki komut satırını çalıştırarak özel hesap için yerel profil oluşturabilirsiniz:
    >
    > **runas/User: domain\name/profile cmd.exe**

4. **IntelliTrace** için **Yapılandır** ' ı seçerek varsayılan IntelliTrace ayarlarını değiştirin.

     Toplanacak verileri yapılandırmak için iletişim kutusu görüntülenir.

    > [!WARNING]
    > IntelliTrace verilerini toplamayı etkinleştirirseniz, kod kapsamı verilerinin toplanması işe alınacaktır.

5. **Genel** sekmesini seçin. **IntelliTrace olaylarını yalnızca** test yaparken performans üzerinde en az etkisi olan önemli Tanılama olaylarını kaydetmek için seçin.

     -veya-

     **IntelliTrace olaylarını seçin ve** çağrı bilgilerini gösteren Tanılama olaylarını ve Yöntem düzeyi izlemeyi kaydetmek için bilgileri çağırın. Testlerinizi çalıştırdığınızda bu düzeyde izlemenin performans etkisi olabilir.

6. Internet Information Services çalıştıran ASP.NET uygulamanızdan veri toplamak için **Internet Information Services üzerinde çalışan ASP.net uygulamalardan veri topla**' yı seçin. Web sunucusu rolünde Test Aracınızı ayarlayın ve yapılandırın. Bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

7. **Modüller** sekmesini seçin. Aşağıdakilerden birini **hariç tüm modüllerden veri topla** ' yı seçin ve modül listesine eklemek için **Ekle** ' yi kullanın ve bir modülü kaldırmak için öğesini **kaldırın** . Bu seçenek, belirttiğiniz modüller dışında sistemde çalışan tüm modülleri dahil etmenizi sağlar.

     -veya-

     **Yalnızca aşağıdaki modüllerden veri topla** ' yı seçin ve modül listesine eklemek için **Ekle** ' yi kullanın ve bir modülü kaldırmak için öğesini **kaldırın** . Bu seçenek tam olarak istediğiniz modülleri belirtmenizi sağlar.

    > [!NOTE]
    > Mümkünse, izlemek istediğiniz belirli süreçler ' ı seçin. Bu, en iyi performans için önerilir.

8. **Süreçler** sekmesini seçin. **Aşağıdakiler hariç tüm işlemlerden veri topla** ' yı seçin ve işlem listesine eklemek için **Ekle** ' yi ve bir işlemi kaldırmak için **Kaldır** ' ı kullanın. Bu seçenek, belirttiğiniz süreçler hariç sistemde çalışan tüm işlemlerin dahil etmenize olanak tanır.

     -veya-

     **Yalnızca belirtilen işlemlerden veri topla** ' yı seçin ve işlem listesine eklemek için **Ekle** ' yi ve bir işlemi kaldırmak için **Kaldır** ' ı kullanın. Bu seçenek tam olarak istediğiniz işlemi belirtmenizi sağlar.

9. Seçim **IntelliTrace olayları** sekmesini seçin. Tanılama olaylarını topladığınızda dahil etmek veya hariç tutmak istediğiniz her IntelliTrace olay kategorisini seçin veya temizleyin.

10. Seçim Her IntelliTrace olay kategorisini genişletin ve IntelliTrace olaylarına dahil etmek veya dışlamak istediğiniz her bir olayı seçin veya temizleyin.

11. Seçim **Gelişmiş** sekmesini seçin. Daha sonra, **kayıt Için maksimum disk alanı alanının** yanındaki oku seçin ve IntelliTrace dosyasının kullanması için etkinleştirmek istediğiniz en büyük boyutu seçin.

    > [!NOTE]
    > Kaydın boyutunu artırırsanız, bu kaydı test sonuçlarınızla birlikte kaydettiğinizde bir zaman aşımı sorunu oluşabilir.

12. Microsoft Test Yöneticisi kullanıyorsanız (Visual Studio 2017 ' de kullanım dışı), **Kaydet**' i seçin. Visual Studio kullanıyorsanız **Tamam**' ı seçin. IntelliTrace ayarları artık test ayarlarınız için yapılandırılır ve kaydedilir.

    ::: moniker range="vs-2017"
    > [!NOTE]
    > Bu tanılama veri bağdaştırıcısı için yapılandırmayı sıfırlamak üzere, Visual Studio için **varsayılan yapılandırmaya Sıfırla** veya Microsoft Test Yöneticisi Için varsayılana **Sıfırla** ' yı seçin.
    ::: moniker-end
    ::: moniker range=">=vs-2019"
    > [!NOTE]
    > Bu tanılama veri bağdaştırıcısı için yapılandırmayı sıfırlamak üzere Visual Studio 'da **varsayılan yapılandırmaya Sıfırla** ' yı seçin.
    ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test sırasında tanılama verilerini topla (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [Tanılama verilerini el ile testlerde topla (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
