---
title: Yük Testleri için ASP.NET Profil oluşturun
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 07df32104394dffcd61d1561309b77e61593f6e6
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880240"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Nasıl yapılır: Visual Studio'daki test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucusu yapılandırın

ASP.NET profilci bilgilerini toplamak için ASP.NET profiloluşturucu tanıveri bağdaştırıcısını kullanabilirsiniz. Bu tanılama veri bağdaştırıcısı ASP.NET uygulamalar için performans verileri toplar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bu tanılama veri bağdaştırıcısı, Microsoft Test Manager (Visual Studio 2017'de amortismana tabi) kullanılarak çalıştırılan testler için kullanılamaz. Yalnızca web sitelerini kullanarak yük testleri ile ASP.NET Profiler tanı bağdaştırıcısını kullanabilirsiniz, bu da Visual Studio Enterprise gerektirir.

ASP.NET profil oluşturucu tanıveri bağdaştırıcısı, bir yük testi çalıştırdığınızda uygulama katmanından ASP.NET profil oluşturucu verileri toplamanızı sağlar. Profil oluşturucuyu uzun yük testleri için çalıştırmamalısınız, örneğin, bir saatten uzun süren yükleme testleri. Profil oluşturucu dosyasının büyük, belki de yüzlerce megabayt olabiliyor olmasıdır. Bunun yerine, yine de performans sorunları derin tanı yarar verecektir ASP.NET profilleyici kullanarak daha kısa yük testleri çalıştırın.

> [!NOTE]
> ASP.NET profilci tanıveri bağdaştırıcısı Internet Information Services (IIS) işlemini profiller. Bu nedenle, bir geliştirme web sunucusuna karşı çalışmaz. Yükleme testinizdeki web sitesinin profilini çıkarmak için, IIS'nin çalıştırdığı makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, ancak yalnızca toplama aracısı olur. Daha fazla bilgi için [bkz.](../test/lab-management/install-configure-test-agents.md)

Daha fazla bilgi için [bkz: Dağıtılmış yük testi için test ayarı oluşturun.](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Test ayarlarınız için ASP.NET profil oluşturucuyu yapılandırın

Bu yordamdaki adımları gerçekleştirmeden önce Visual Studio'dan test ayarlarınızı açmanız ve **Veri ve Tanılama** sayfasını seçmeniz gerekir.

1. ASP.NET profil oluşturucu verilerini toplamak için kullanılacak rolü seçin.

    > [!WARNING]
    > Bu rol bir web sunucusu olmalıdır.

2. Profil oluşturma verilerinin ASP.NET toplamayı etkinleştirmek için **ASP.NET Profiler'ı** seçin ve sonra **Yapıl'ı**seçin.

     Profil oluşturma veri toplama ASP.NET yapılandırmak için iletişim kutusu görüntülenir.

3. **Profiler Örnekleme aralığında,** profil oluşturma örnekleri nin alınması arasında kaç tane durdurulmayan CPU saat döngüsünün ASP.NET kadar bekleyeceklerini gösteren bir değer yazın.

4. Katman etkileşimi profilini etkinleştirmek için **Katman Etkileşimprofiloluşturmayı Etkinleştir'i**seçin.

     Katman etkileşimi profil oluşturma, her yapı için web sunucusuna gönderilen istek sayısını (örneğin, *MyPage.aspx* veya *CompanyLogo.gif)* ve her isteğe hizmet vermek için geçen süreyi sayar. Ayrıca, katman etkileşimi profil oluşturma, sayfa isteğinin bir parçası olarak hangi ADO.NET bağlantıların kullanıldığını ve bu isteğe hizmet in bir parçası olarak kaç sorgu ve depolanan yordam çağrısının yürütüldedildiğini toplar.

     İki farklı zamanlama bilgisi kümesi toplanır:

    - Her web isteğine hizmet vermek için zamanlama bilgileri (Min, Max, Average ve Total).

    - Her sorguyu yürütmenin zamanlama bilgileri (Min, Max, Average ve Total).

Test ayarınızda yapılandırılan ASP.NET profil oluşturucu suyla, artık ASP.NET web uygulamanızda ASP.NET profil oluşturma verileri toplayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [Nasıl? Dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)