---
title: Yük ASP.NET Için Profil Yükleyiciyi Yapılandırma
description: Profil oluşturma bilgilerini toplamak ASP.NET profil oluşturma tanılama veri bağdaştırıcısını ASP.NET öğrenin.
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
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>Nasıl yapılandırılır: ASP.NET'de test ayarlarını kullanarak yük testleri için bir profil Visual Studio

Profil oluşturma bilgilerini ASP.NET profil oluşturma tanılama veri bağdaştırıcısını ASP.NET kullanabilirsiniz. Bu tanılama veri bağdaştırıcısı, uygulamalar için performans ASP.NET toplar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Bu tanılama veri bağdaştırıcısı, Microsoft Test Yöneticisi kullanılarak çalıştır Visual Studio kullanılamaz. ASP.NET Profiler tanılama bağdaştırıcısını yalnızca web sitelerini kullanarak yük testleriyle kullanabilirsiniz. Bu, Visual Studio Enterprise.

ASP.NET profil oluşturma tanılama veri bağdaştırıcısı, bir ASP.NET testi çalıştırarak uygulama katmanından profil oluşturma verilerini toplamaya olanak sağlar. Profil oluşturma, örneğin bir saatten uzun süren yük testleri gibi uzun yük testleri için çalıştırmamalı. Bunun nedeni profil oluşturma dosyasının yüzlerce megabayt olmak için büyük hale geldi. Bunun yerine, performans sorunlarının derin tanılama avantajını ASP.NET profilleyiciyi kullanarak daha kısa yük testleri çalıştırın.

> [!NOTE]
> ASP.NET profil oluşturma tanılama veri bağdaştırıcısı, Internet Information Services (IIS) işleminin profilini oluşturmaz. Bu nedenle, geliştirme web sunucusuna karşı çalışmaz. Yük testinde web sitesinin profilini oluşturmak için IIS'nin üzerinde çalıştır olduğu makineye bir test aracısı yüklemeniz gerekir. Test aracısı yük oluşturmaz, yalnızca koleksiyon için bir aracı olur. Daha fazla bilgi için [bkz. Test aracılarını yükleme ve yapılandırma.](../test/lab-management/install-configure-test-agents.md)

Daha fazla bilgi için, [bkz. How to: Create a test setting for a distributed load test](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md).

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>Test ayarlarınız ASP.NET profil profilleyiciyi yapılandırma

Bu yordamda yer alan adımları gerçekleştirmeden önce test ayarlarınızı Visual Studio ve Tanılama **sayfasını seçmeniz** gerekir.

1. Profil profili oluşturma verilerini toplamak için ASP.NET seçin.

    > [!WARNING]
    > Bu rol bir web sunucusu olması gerekir.

2. Profil **ASP.NET veri toplamayı** etkinleştirmek için ASP.NET ProfilLeyici'yi seçin ve ardından Yapılandır'ı **seçin.**

     Profil oluşturma veri koleksiyonu ASP.NET iletişim kutusu görüntülenir.

3. Profil **Oluşturma Örnekleme aralığı'na,** profil oluşturma örneklerini almak arasında kaç tane durdurulmamış CPU saati döngüsü olduğunu gösteren ASP.NET yazın.

4. Katman etkileşimi profili oluşturmayı etkinleştirmek için Katman Etkileşim **Profili Oluşturmayı Etkinleştir'i seçin.**

     Katman etkileşimi profili oluşturma, her yapıt için web sunucusuna gönderilen isteklerin sayısını *(örneğin, MyPage.aspx* veya *CompanyLogo.gif*) ve her isteğin hizmet için geçen zamanı sayar. Ayrıca, katman etkileşim profili oluşturma ADO.NET isteğin bir parçası olarak hangi bağlantı bağlantılarının kullanıldığı ve bu isteğin bakımı kapsamında kaç sorgu ve saklı yordam çağrısının yürütültüğü toplanıyor.

     İki farklı zamanlama bilgisi kümesi toplanır:

    - Her web isteğinin bakımı için zamanlama bilgileri (Min, Max, Average ve Total).

    - Her sorguyu yürütmeye ilişkin zamanlama bilgileri (Min, Max, Average ve Total).

Test ASP.NET profil oluşturma verileri bağdaştırıcısı yapılandırıldığında, artık profil oluşturma verilerini ASP.NET web uygulamanıza ASP.NET toplayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
- [Nasıl yapıldı: Dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)