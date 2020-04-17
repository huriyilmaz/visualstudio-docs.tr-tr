---
title: IntelliTrace ile yayınlanan bir Azure bulut hizmetini hata ayıklama
description: Visual Studio ve IntelliTrace ile bulut hizmetini nasıl hata ayıklamayı öğrenin
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: c61af4a08c61cbfd16d33e2b5cf7402960163f12
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489720"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama
IntelliTrace ile, Azure'da çalıştığında bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmanız gerekiyorsa, Visual Studio'dan kodunuzu Azure'da çalışıyormuş gibi geçmek için IntelliTrace günlüklerini kullanabilirsiniz. Sonuç olarak, IntelliTrace Azure uygulamanız Azure'da bulut hizmeti olarak çalışırken anahtar kodu yürütme ve ortam verilerini kaydeder ve Visual Studio'dan kaydedilen verileri yeniden oynatmanızı sağlar.

Visual Studio Enterprise yüklüyse ve Azure uygulama hedefleriniz .NET Framework 4 veya daha sonraki bir sürümü varsa IntelliTrace'i kullanabilirsiniz. IntelliTrace, Azure rolleriniz için bilgi toplar. Bu roller için sanal makineler her zaman 64 bit işletim sistemleri çalıştırır.

Alternatif olarak, azure'da çalışan bir bulut hizmetine doğrudan bağlanmak için [uzaktan hata ayıklama](vs-azure-tools-debugging-cloud-services-overview.md) yı kullanabilirsiniz.

> [!IMPORTANT]
> IntelliTrace yalnızca hata ayıklama senaryoları için tasarlanmıştır ve bir üretim dağıtımı için kullanılmamalıdır.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>IntelliTrace için bir Azure uygulamasını yapılandırma
Bir Azure uygulaması için IntelliTrace'i etkinleştirmek için uygulamayı visual studio azure projesinden oluşturmanız ve yayımlamanız gerekir. Azure uygulamanızı Azure'da yayınlamadan önce IntelliTrace'i Azure'da yapılandırmanız gerekir. IntelliTrace yapılandırmadan uygulamanızı yayımlarsanız, projeyi yeniden yayımlamanız gerekir. Daha fazla bilgi için Visual [Studio'u kullanarak Azure bulut hizmetleri projeleri yayımlama](vs-azure-tools-publishing-a-cloud-service.md)'ya bakın.

1. Azure uygulamanızı dağıtmaya hazır olduğunuzda, proje oluşturma hedeflerinizin **Hata Ayıklama**olarak ayarlandığından doğrulayın.

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve bağlam menüsünden **Yayımla'yı**seçin.

1. Azure **Uygulamasını Yayımla** iletişim kutusunda Azure aboneliğini seçin ve **İleri'yi**seçin.

1. **Ayarlar** sayfasında **Gelişmiş Ayarlar** sekmesini seçin.

1. Bulutta yayınlandığında uygulamanız için IntelliTrace günlüklerini toplamak için **IntelliTrace'i Etkinleştir** seçeneğini açın.

1. Temel IntelliTrace yapılandırmasını özelleştirmek için, **IntelliTrace'i etkinleştirmek**için yanındaki **Ayarlar'ı** seçin.

    ![IntelliTrace ayarları bağlantısı](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. **IntelliTrace Ayarları** iletişim kutusunda, hangi olayların günlüğe kaydedileceğini, çağrı bilgilerini toplayıp toplayamayacağınızı, günlükleri hangi modülleri ve işlemleri toplayacaklarını ve kayda ne kadar alan ayıracaklarını belirtebilirsiniz. IntelliTrace hakkında daha fazla bilgi için, [IntelliTrace ile Hata Ayıklama](../debugger/intellitrace.md)bölümüne bakın.

    ![IntelliTrace ayarları](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace günlüğü, IntelliTrace ayarlarında belirtilen maksimum boyutta dairesel bir günlük dosyasıdır (varsayılan boyut 250 MB'dır). IntelliTrace günlükleri sanal makinenin dosya sistemindeki bir dosyada toplanır. Günlükleri istediğinizde, bu noktada anlık görüntü alınır ve yerel bilgisayarınıza indirilir.

Azure bulut hizmeti Azure'da yayımlandıktan sonra, Aşağıdaki resimde gösterildiği gibi, IntelliTrace'in **Sunucu Gezgini'ndeki**Azure düğümünden etkinleştirilip etkinleştirilemediğini belirleyebilirsiniz:

![Server Explorer - IntelliTrace etkin](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Bir rol örneği için IntelliTrace günlüklerini indirin
Visual Studio'u kullanarak, aşağıdaki adımları izleyerek bir rol örneği için IntelliTrace günlüklerini indirebilirsiniz:

1. **Sunucu Gezgini'nde** **Bulut Hizmetleri** düğümlerini genişletin ve indirmek istediğiniz günlükleri bulunan rol örneğini bulun.

1. Rol örneğine sağ tıklayın ve s bağlam menüsünden **IntelliTrace Günlüklerini Görüntüle'yi**seçin.

    ![IntelliTrace günlükleri menüsü seçeneğini görüntüle](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace günlükleri yerel bilgisayarınızdaki bir dizinde bir dosyaya indirilir. IntelliTrace günlüklerini her istediğinizde yeni bir anlık görüntü oluşturulur. Günlükler indirilirken, Visual Studio işlemin ilerlemesini **Azure Etkinlik Günlüğü** penceresinde görüntüler. Aşağıdaki şekilde gösterildiği gibi, daha fazla ayrıntı görmek için işlem için satır öğesini genişletebilirsiniz.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace günlükleri indirirken Visual Studio'da çalışmaya devam edebilirsiniz. Günlük indirme yi bitirdiğinde Visual Studio'da açılır.

> [!NOTE]
> IntelliTrace günlükleri, çerçevenin daha sonra oluşturduğu ve işlediği özel durumlar içerebilir. İç çerçeve kodu, bir rolü başlatmanın normal bir parçası olarak bu özel durumları oluşturur, böylece bunları güvenle yok sayabilirsiniz.
>
>

## <a name="next-steps"></a>Sonraki adımlar
- [Azure bulut hizmetlerini hata ayıklama seçenekleri](vs-azure-tools-debugging-cloud-services-overview.md)
- [Visual Studio'u kullanarak Azure bulut hizmeti yayınlama](vs-azure-tools-publishing-a-cloud-service.md)