---
title: IntelliTrace ile yayımlanmış Azure bulut hizmeti hata ayıklaması
ms.custom: SEO-VS-2020
description: Visual Studio ve IntelliTrace ile bulut hizmette hata ayıklamayı öğrenin
author: mikejo5000
manager: jmartens
ms.technology: vs-azure
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: d298983e3dae549b09a96873d4325011fda5f51b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633129"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama
IntelliTrace ile, Azure'da çalışan bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe görüntüebilirsiniz. Bir sorunun nedenini bulmanız gerekirse IntelliTrace günlüklerini kullanarak azure'da çalışıyor gibi Visual Studio adım adım kod atabilirsiniz. Aslında IntelliTrace, Azure uygulama Azure'da bulut hizmeti olarak çalıştır çalıştırken anahtar kodu yürütme ve ortam verilerini kaydeden ve kaydedilen verileri azure'dan Visual Studio.

4 veya daha yeni bir sürüme sahip Visual Studio Enterprise Azure uygulama hedefleriniz varsa IntelliTrace.NET Framework kullanabilirsiniz. IntelliTrace, Azure rolleriniz için bilgi toplar. Bu rollerin sanal makineleri her zaman 64 bit işletim sistemlerini çalıştırmaktadır.

Alternatif olarak, [Azure'da çalışan bir bulut](vs-azure-tools-debugging-cloud-services-overview.md) hizmetine doğrudan eklemek için uzaktan hata ayıklamayı kullanabilirsiniz.

> [!IMPORTANT]
> IntelliTrace yalnızca hata ayıklama senaryolarına yöneliktir ve üretim dağıtımı için kullanılmamalı.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>IntelliTrace için Azure uygulaması yapılandırma
Bir Azure uygulamasında IntelliTrace'i etkinleştirmek için uygulamayı bir Azure projesinden Visual Studio yayımlamanız gerekir. Azure'da yayımlamadan önce Azure uygulamanıza IntelliTrace'i yapılandırmanız gerekir. IntelliTrace'i yapılandırmadan uygulama yayımlarsanız projeyi yeniden yayımlamanız gerekir. Daha fazla bilgi için [bkz. Azure bulut hizmetleri projelerini Visual Studio.](vs-azure-tools-publishing-a-cloud-service.md)

1. Azure uygulamanızı dağıtmaya hazır olduğunda proje derleme hedeflerinizi Hata Ayıkla olarak **ayarlı olduğunu doğrulayın.**

1. Bu **Çözüm Gezgini** proje'ye sağ tıklayın ve bağlam menüsünde Yayımla'yı **seçin.**

1. Azure Uygulamasını **Yayımla iletişim** kutusunda Azure aboneliğini ve ardından Sonraki'yi **seçin.**

1. Yeni **Ayarlar** Gelişmiş Giriş sekmesini **Ayarlar** seçin.

1. Uygulama bulutta yayımlanırken uygulamanıza intelliTrace günlüklerini toplamak için **IntelliTrace'i** Etkinleştir seçeneğini etkinleştirin.

1. Temel IntelliTrace yapılandırmasını özelleştirmek için, IntelliTrace'i **Ayarlar** **seçeneğinin yanındaki Seç'i seçin.**

    ![IntelliTrace ayarları bağlantısı](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. **IntelliTrace Ayarlar** iletişim kutusunda günlüğe kaydedilebilecek olayları, çağrı bilgilerini toplayıp toplamayacaksınız, hangi modüllerin ve işlemlerin günlükleri toplayacaksınız ve kayda ne kadar alan ayrılacaklarını belirtebilirsiniz. IntelliTrace hakkında daha fazla bilgi için [bkz. IntelliTrace ile Hata Ayıklama.](../debugger/intellitrace.md)

    ![IntelliTrace ayarları](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace günlüğü, IntelliTrace ayarlarında belirtilen en büyük boyuta sahip döngüsel bir günlük dosyasıdır (varsayılan boyut 250 MB'tır). IntelliTrace günlükleri, sanal makinenin dosya sisteminde bir dosyaya toplanır. Günlükleri isteğinde bulundurarak o noktada bir anlık görüntü alınır ve yerel bilgisayarınıza indirilir.

Azure bulut hizmeti Azure'da yayımlandıktan sonra, aşağıdaki görüntüde gösterildiği gibi IntelliTrace'in **Sunucu Gezgini'daki** Azure düğümünden etkinleştirildiğinden karar veabilirsiniz:

![Sunucu Gezgini - IntelliTrace etkin](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Rol örneği için IntelliTrace günlüklerini indirme
Aşağıdaki Visual Studio kullanarak bir rol örneği için IntelliTrace günlüklerini indirebilirsiniz:

1. Bu **Sunucu Gezgini,** Cloud Services **düğümünü** genişletin ve günlüklerini indirmek istediğiniz rol örneğini bulun.

1. Rol örneğine sağ tıklayın ve bağlam **menüsünden IntelliTrace Günlüklerini Görüntüle'yi seçin.**

    ![IntelliTrace günlüklerini görüntüle menü seçeneği](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace günlükleri yerel bilgisayarınızda bir dizinde yer alan bir dosyaya indirilir. IntelliTrace günlüklerini her isteğiniz için yeni bir anlık görüntü oluşturulur. Günlükler indirilirken Visual Studio ilerlemesini Azure Etkinlik Günlüğü **penceresinde** görüntüler. Aşağıdaki şekilde gösterildiği gibi, daha fazla ayrıntı görmek için işlem için satır öğesini genişletebilirsiniz.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace günlükleri Visual Studio bu günlüklerde çalışmaya devam edin. Günlük indirdikten sonra günlük, Visual Studio.

> [!NOTE]
> IntelliTrace günlükleri, çerçevenin daha sonra oluşturması ve işlemesi için özel durumlar içerebilir. İç çerçeve kodu bu özel durumları bir rolü başlatmanın normal bir parçası olarak oluşturur, bu nedenle bunları güvenle yoksayabilirsiniz.
>
>

## <a name="next-steps"></a>Sonraki adımlar
- [Azure bulut hizmetlerde hata ayıklama seçenekleri](vs-azure-tools-debugging-cloud-services-overview.md)
- [Azure bulut hizmetini Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)