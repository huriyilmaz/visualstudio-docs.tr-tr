---
title: IntelliTrace verileri
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, configuring test settings
- Diagnostic Data Adapter, InteliTrace
- debugging [Visual Studio ALM], difficult issues using IntelliTrace
- Test Runner, InteliTrace
ms.assetid: 02b6716f-569e-4961-938a-e790a0c74b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 826d16fa316340226df042b0d762d923c43d39c9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594779"
---
# <a name="how-to-collect-intellitrace-data-to-help-debug-difficult-issues"></a>Nasıl kullanılır: Zor sorunları hata ayıklamaya yardımcı olmak için IntelliTrace verilerini toplama

Visual Stdio'da belirli tanısal izleme bilgileri toplamak için IntelliTrace için tanısal veri bağdaştırıcısını yapılandırabilirsiniz. Testler bu bağdaştırıcıyı kullanabilir, test, uygulama için büyük miktarda tanılama olayları toplayabilir ve sonrasında bir geliştirici bu olayları, kodu izleyip bir hatanın nedenini bulmak üzere kullanabilir. IntelliTrace için tanısal veri bağdaştırıcısı manuel veya otomatik testler için kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> IntelliTrace yalnızca yönetilen kod kullanılarak yazılmış bir uygulamada çalışır. İstemci olarak tarayıcı kullanan bir web uygulamasını test ediyorsanız, izlenebilir yönetilen kod olmadığından test ayarlarınızda istemci için IntelliTrace'i etkinleştirmemelisiniz. Bu durumda, bir ortam kurmak ve Web sunucunuzda uzaktan IntelliTrace verileri toplamak isteyebilirsiniz.

IntelliTrace verileri *.iTrace*uzantısı olan bir dosyada depolanır. Testinizi çalıştırdığınızda ve bir test adımı başarısız olduğunda, bir hata oluşturabilirsiniz. Tanılama bilgilerini içeren IntelliTrace dosyası bu hataya otomatik olarak eklenir.

> [!NOTE]
> IntelliTrace için tanılama veri bağdaştırıcısı, test geçişi başarılı olduğunda IntelliTrace dosyası oluşturmaz. Bir dosyayı yalnızca başarısız bir test örneğine veya bir hata gönderdiğinde kaydeder.

IntelliTrace dosyasında toplanan veriler, kodunuzda bir hatayı çoğaltmak ve tanılamak için gereken süreyi azaltarak hata ayıklama üretkenliğini artırır. Ayrıca, IntelliTrace dosyasını kendi bilgisayarında yerel oturumunuzu çoğaltabilecek başka bir kişiyle paylaşabildiğiniziçin, bir hatanın tekrarlanamaz olma olasılığını azaltır.

> [!NOTE]
> Test ayarlarınızda IntelliTrace'i etkinleştiriseniz, kod kapsamı verilerini toplamak çalışmaz.

> [!WARNING]
> IntelliTrace için tanısal veri bağdaştırıcısı, test çalışması için testler yüklendikten sonra yapılması gereken yönetilen bir işlemi enstrümanting tarafından çalışır. İzlemek istediğiniz işlem zaten başlamışsa, işlem zaten çalıştığı için Hiçbir IntelliTrace dosyası toplanmaz. Bunu atlatmak için, testler yüklenmeden önce işlemin durdurulduğundan emin olun. Testler yüklendikten veya ilk test başladıktan sonra işlemi başlatın.

Aşağıdaki yordam, toplamak istediğiniz IntelliTrace verilerinin nasıl yapılandırılabildiğini açıklar. Bu adımlar, Visual Studio'daki Microsoft Test Yöneticisi'ndeki yapılandırma düzenleyicisi ve Test Ayarları iletişim kutusu için geçerlidir.

> [!NOTE]
> IntelliTrace verilerini toplamak için kullanılan test aracısının kullanıcı hesabı yönetici grubunun bir üyesi olmalıdır. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)

## <a name="configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>Verileri IntelliTrace tanıveri bağdaştırıcısıyla toplayacak şekilde yapılandırın

Bu yordamdaki adımları gerçekleştirmeden önce, test ayarlarınızı Microsoft Test Manager veya Visual Studio'dan açmanız ve **Veri ve Tanılama** sayfasını seçmeniz gerekir.

### <a name="to-configure-the-data-to-collect-with-the-intellitrace-diagnostic-data-adapter"></a>IntelliTrace tanıveri bağdaştırıcısı ile toplamak için verileri yapılandırmak için

1. IntelliTrace verilerini toplamak için kullanılacak rolü seçin.

2. **IntelliTrace'i**seçin.

3. Bir web istemcisi rolü veya ASP.NET bir web uygulaması için IntelliTrace ekliyorsanız, **IntelliTrace ve Test Impact için ASP.NET İstemci Proxy'yi**de seçmeniz gerekir.

     Bu proxy, bir istemciden IntelliTrace ve Test Impact tanıveri bağdaştırıcıları için bir web sunucusuna http aramaları hakkında bilgi toplamanızı sağlar.

    > [!WARNING]
    > IntelliTrace verilerini toplamayı planladığınız Internet Information Server 'daki (IIS) uygulama havuzu için kullanılan kimlik için özel bir hesap kullanmaya karar verirseniz, özel hesap için IIS makinesinde yerel kullanıcı profili oluşturmanız gerekir. kullanılmaktadır. Özel hesap için yerel profili, IIS makinesinde bir kez yerel olarak oturum açarak veya özel hesap kimlik bilgilerini kullanarak aşağıdaki komut satırını çalıştırarak oluşturabilirsiniz:
    >
    > **runas /user:domain\name /profil cmd.exe**

4. Varsayılan **IntelliTrace** ayarlarını değiştirmek için IntelliTrace için **Yapılandır'ı** seçin.

     Toplanacak verileri yapılandırmak için iletişim kutusu görüntülenir.

    > [!WARNING]
    > IntelliTrace verilerinin toplanmasını etkinleştiriseniz, kod kapsamı verilerini toplamak çalışmaz.

5. **Genel** sekmesini seçin. Yalnızca test ederken performans üzerinde en az etkiye sahip önemli tanılama olaylarını kaydetmek için **IntelliTrace olaylarını** seçin.

     -veya-

     Çağrı bilgilerini gösteren tanılama olaylarını ve yöntem düzeyini kaydetmek için **IntelliTrace olayları ve çağrı bilgilerini** seçin. Bu izleme düzeyi, testlerinizi çalıştırdığınızda performans etkisi ne olabilir.

6. Internet Bilgi Hizmetleri'nde çalışan ASP.NET uygulamanızdan veri toplamak için, **Internet Bilgi Hizmetleri'nde çalışan ASP.NET uygulamalarından veri topla'yı**seçin. Test aracınızı web sunucusu rolünde ayarlayın ve yapılandırır. Bkz. [Test aracılarını yükle ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

7. **Modüller** sekmesini seçin. **Aşağıdakiler dışında tüm modüllerden veri topla'yı** seçin ve modüller listesine eklemek için **Ekle'yi** ve bir modülü kaldırmak için **Kaldır'ı** kullanın. Bu seçenek, belirttiğiniz modüller dışında sistemde çalışan tüm modülleri eklemenize olanak tanır.

     -veya-

     **Yalnızca aşağıdaki modüllerden veri topla'yı** seçin ve modüller listesine eklemek için **Ekle** ve bir modülü kaldırmak için **Kaldır'ı** kullanın. Bu seçenek, tam olarak hangi modülleri istediğinizi belirtmenizi sağlar.

    > [!NOTE]
    > Mümkünse, izlemek istediğiniz belirli işlemleri seçin. Bu, optimum performans için önerilir.

8. **İşlemler** sekmesini seçin. **Aşağıdakiler dışında tüm işlemlerden veri topla'yı** seçin ve işlemler listesine eklemek için **Ekle'yi** ve bir işlemi kaldırmak için **Kaldır'ı** kullanın. Bu seçenek, belirttiğiniz işlemler dışında sistemde çalışan tüm işlemleri eklemenize olanak tanır.

     -veya-

     **Yalnızca belirtilen işlemlerden veri topla'yı** seçin ve işlemler listesine eklemek için **Ekle** ve bir işlemi kaldırmak için **Kaldır'ı** kullanın. Bu seçenek, tam olarak hangi işlemleri istediğinizi belirtmenizi sağlar.

9. (İsteğe bağlı) **IntelliTrace Events sekmesini** seçin. Tanılama olaylarını topladığınızda eklemek veya hariç tutmak istediğiniz her IntelliTrace etkinlik kategorisini seçin veya temizleyin.

10. (İsteğe bağlı) Her IntelliTrace etkinlik kategorisini genişletin ve IntelliTrace etkinliklerine eklemek veya hariç tutmak istediğiniz her özel olayı seçin veya temizleyin.

11. (İsteğe bağlı) **Gelişmiş** sekmesini seçin. Ardından, kayıt için **maksimum disk alanı miktarının** yanındaki oku seçin ve IntelliTrace dosyasının kullanmasını etkinleştirmek istediğiniz maksimum boyutu seçin.

    > [!NOTE]
    > Kaydın boyutunu artırırsanız, bu kaydı test sonuçlarınız ile birlikte kaydettiğinizde bir zaman sonu sorunu oluşabilir.

12. Microsoft Test Yöneticisi kullanıyorsanız **Kaydet'i**seçin. Visual Studio kullanıyorsanız, **Tamam'ı**seçin. IntelliTrace ayarları artık test ayarlarınız için yapılandırıldı ve kaydedilir.

    > [!NOTE]
    > Bu tanılama veri bağdaştırıcısının yapılandırmasını sıfırlamak için Visual Studio için **varsayılan yapılandırmaya sıfırla'yı** veya Microsoft Test Yöneticisi için **varsayılan olarak sıfırla'yı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ederken tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [El ile yapılan testlerde tanılama verileri toplama (Azure Test Planları)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [IntelliTrace verilerini toplama](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)
