---
title: Yük testleri için ASP.NET Profiler'ı yapılandırma
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0132401df33bd65d7e328307167b6c228155bb42
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169397"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio'da test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuyu yapılandırma

ASP.NET Profil Oluşturucu bilgi toplamak için ASP.NET profiler tanılama veri bağdaştırıcısı'nı kullanabilirsiniz. Bu tanılama veri bağdaştırıcısı, ASP.NET uygulamaları için performans verilerini toplar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bu tanılama veri bağdaştırıcısı Microsoft Test Yöneticisi'ni kullanarak çalıştırılan testler için kullanılamaz. ASP.NET Profiler tanılama bağdaştırıcısı, Visual Studio Enterprise gerektiren bir yalnızca, Web siteleri kullanan yük testleriyle kullanabilirsiniz.

ASP.NET profiler tanılama veri bağdaştırıcısı, bir yük testi çalıştırdığınızda, uygulama katmanından ASP.NET Profil Oluşturucu verileri toplamanıza olanak tanır. Uzun yük testleri, örneğin, bir saatten daha uzun yük testleri için profil oluşturucu çalıştırmamanız gerekir. Profil oluşturucu dosyası büyüyebilir olmasıdır belki de yüz megabayt. Bunun yerine, ayrıntılı performans sorunlarını tanılama avantajı hala erişmenizi sağlayan ASP.NET profil oluşturucuyu kullanarak kısa yük testleri çalıştırın.

> [!NOTE]
> ASP.NET profiler tanılama veri bağdaştırıcısı Internet Information Services (IIS) işleminin profilini. Bu nedenle, bir geliştirme web sunucusuna karşı çalışmaz. Yük testinizde Web sitesinin profilini çıkarmak için IIS'in çalıştığı makineye bir test aracısı yüklemek zorunda. Test aracısı yük oluşturmayacak ancak yalnızca koleksiyon için bir aracı olacak. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

Daha fazla bilgi için bkz. [nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Test ayarlarınız için ASP.NET Profiler'ı yapılandırma

Bu yordamdaki adımları gerçekleştirmeden önce, Visual Studio 'dan test ayarlarınızı açmanız ve **veri ve tanılama** sayfasını seçmeniz gerekir.

1. ASP.NET Profil Oluşturucu verileri toplamak için kullanılacak rolü seçin.

    > [!WARNING]
    > Bu rol, bir web sunucusu olmalıdır.

2. ASP.NET profil oluşturma verilerini toplamayı etkinleştirmek için **ASP.net Profiler** ' ı seçin ve ardından **Yapılandır**' ı seçin.

     ASP.NET profil oluşturma veri koleksiyonu yapılandırmak için iletişim kutusu görüntülenir.

3. **Profil Oluşturucu örnekleme aralığı**içinde, ASP.NET profil oluşturma örnekleri almak arasında kaç tane DURDURULMAYAN CPU saati döngüsünü belirten bir değer yazın.

4. Katman etkileşimi profil oluşturmayı etkinleştirmek için **katman etkileşim profilini etkinleştir**' i seçin.

     Katman etkileşimi profili oluşturma, her bir yapıt için Web sunucusuna gönderilen isteklerin sayısını (örneğin, *MyPage. aspx* veya *CompanyLogo. gif*) ve her bir isteğe hizmet vermek için geçen süreyi sayar. Ayrıca, katman etkileşim profili oluşturma ve hangi ADO.NET bağlantı sayfası isteğin bir parçası olarak kullanılan kaç sorguları ve saklı yordam çağrılarını bu isteği hizmet parçası olarak dahil edilen toplar.

     İki farklı ayarlar, zamanlama bilgilerinin toplanır:

    - Her web isteğini bakım için zamanlama bilgileri (Min, Max, ortalama ve toplam).

    - Her sorguyu yürütmek için zamanlama bilgileri (Min, Max, ortalama ve toplam).

Bir test ayarında yapılandırılan ASP.NET profiler tanılama veri bağdaştırıcısı ile ASP.NET profil oluşturma ASP.NET web uygulamanızı şirket verilerini toplayabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [Nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)