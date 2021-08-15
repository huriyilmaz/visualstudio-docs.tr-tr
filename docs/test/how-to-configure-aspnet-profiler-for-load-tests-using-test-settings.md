---
title: yük testleri için ASP.NET profil oluşturucuyu yapılandırma
description: ASP.NET profiler bilgilerini toplamak için ASP.NET profiler tanılama veri bağdaştırıcısını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/13/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 23973a9ac44cdfcf58df57eed54c070fdb9388dcf3ff257add9e418588f9bf12
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384931"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>nasıl yapılır: Visual Studio içindeki test ayarlarını kullanarak yük testleri için ASP.NET profil oluşturucuyu yapılandırma

ASP.NET profiler bilgilerini toplamak için ASP.NET profil oluşturucu tanılama veri bağdaştırıcısını kullanabilirsiniz. bu tanılama veri bağdaştırıcısı ASP.NET uygulamalar için performans verilerini toplar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> bu tanılama veri bağdaştırıcısı, Microsoft Test Yöneticisi (Visual Studio 2017 ' de kullanım dışı) kullanılarak çalıştırılan testler için kullanılamaz. ASP.NET Profiler tanılama bağdaştırıcısını yalnızca, Visual Studio Enterprise gerektiren web sitelerini kullanarak yük testleriyle kullanabilirsiniz.

ASP.NET profiler tanılama veri bağdaştırıcısı, bir yük testi çalıştırdığınızda uygulama katmanından ASP.NET profiler verileri toplamanızı sağlar. Uzun yük testleri için profil oluşturucuyu çalıştırmamanız gerekir, örneğin, bir saatten uzun süren yük testleri. Bunun nedeni profil oluşturucu dosyasının yüzlerce megabayt olması olabilir. bunun yerine, ASP.NET profil oluşturucuyu kullanarak daha kısa yük testlerini çalıştırın. bu, performans sorunlarının derin tanılaması avantajlarından faydalanacaktır.

> [!NOTE]
> ASP.NET profiler tanılama veri bağdaştırıcısı Internet Information Services (ııs) işlemini profillerdir. Bu nedenle, bir geliştirme Web sunucusuna karşı çalışmaz. Yük testinizde web sitesinin profilini almak için, IIS 'nin çalıştığı makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, ancak yalnızca koleksiyon için bir aracı olacaktır. Daha fazla bilgi için bkz. [test aracılarını yükleyip yapılandırma](../test/lab-management/install-configure-test-agents.md).

Daha fazla bilgi için bkz. [nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>test ayarlarınız için ASP.NET profil oluşturucuyu yapılandırın

bu yordamdaki adımları gerçekleştirmeden önce, Visual Studio ' den test ayarlarınızı açmanız ve **veri ve tanılama** sayfasını seçmeniz gerekir.

1. ASP.NET profiler verilerini toplamak için kullanılacak rolü seçin.

    > [!WARNING]
    > Bu rol bir Web sunucusu olmalıdır.

2. ASP.NET profil oluşturma verilerini toplamayı etkinleştirmek için **ASP.NET profil oluşturucu** seçin ve ardından **yapılandır**' ı seçin.

     ASP.NET profil oluşturma veri toplamayı yapılandırmak için iletişim kutusu görüntülenir.

3. **profil oluşturucu örnekleme aralığı**' nda, kaç tane ununununununununununununununununununsuz CPU saati ASP.NET döngüsünü

4. Katman etkileşimi profil oluşturmayı etkinleştirmek için **katman etkileşim profilini etkinleştir**' i seçin.

     Katman etkileşimi profili oluşturma, her bir yapıt için Web sunucusuna gönderilen isteklerin sayısını sayar (örneğin, *MyPage. aspx* veya *CompanyLogo.gif*) ve her bir isteğe hizmet vermek için geçen süre. ayrıca, katman etkileşim profili oluşturma, sayfa isteğinin bir parçası olarak hangi ADO.NET bağlantılarının kullanıldığını ve bu isteğin hizmet verme işleminin bir parçası olarak kaç tane sorgu ve saklı yordam çağrısı yapıldığını toplar.

     İki farklı zamanlama bilgisi kümesi toplanır:

    - Her Web isteğine hizmet vermek için zamanlama bilgileri (en küçük, en fazla, ortalama ve toplam).

    - Her sorguyu yürütmenin zamanlama bilgileri (en az, en fazla, ortalama ve toplam).

test ayarınızda yapılandırılmış ASP.NET profil oluşturucu tanılama veri bağdaştırıcısı ile, artık ASP.NET web uygulamanızda ASP.NET profil oluşturma verileri toplayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
- [Nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)