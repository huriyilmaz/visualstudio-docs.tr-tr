---
title: Visual Studio ve IntelliTrace ile yayımlanmış bir Azure bulut hizmetinde hata ayıklama | Microsoft Docs
description: Bir bulut hizmetinde Visual Studio ve IntelliTrace ile hata ayıklama hakkında bilgi edinin
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 00e13c6f217c54b99dfe103b86f1e775e36fd62a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293540"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama
IntelliTrace ile Azure içinde çalıştığında bir rol örneği için kapsamlı hata ayıklama bilgileri günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmak gerekiyorsa, IntelliTrace günlüklerini, Visual Studio'dan, Azure'da çalışıyormuş gibi kodunuzda adım adım ilerleyin için de kullanabilirsiniz. Aslında Azure uygulamanızın Azure'daki bir bulut hizmeti olarak çalışan ve Visual Studio'dan kaydedilen verileri yeniden yürütme olanak tanır, Intellitrace'in kaydettiği kod yürütme ve ortam verilerini anahtarı. 

Visual Studio Enterprise yüklüyse IntelliTrace ve Azure uygulama hedeflerinizi .NET Framework 4 veya sonraki bir sürümünü kullanabilirsiniz. IntelliTrace rollerinizi Azure için bilgi toplar. Bu roller için sanal makinelerin her zaman 64-bit işletim sistemlerinde çalışır.

Alternatif olarak, [Uzaktan hata ayıklamayı](https://go.microsoft.com/fwlink/p/?LinkId=623041) kullanarak doğrudan Azure 'da çalışan bir bulut hizmetine ekleyebilirsiniz.

> [!IMPORTANT]
> IntelliTrace yalnızca hata ayıklama senaryoları içindir ve Üretim dağıtımı için kullanılmamalıdır.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Azure uygulaması için IntelliTrace'i yapılandırın
Azure uygulaması için IntelliTrace etkinleştirmek için oluşturma ve bir Visual Studio Azure project uygulamayı yayımlayın. Azure'da yayımlamadan önce Azure uygulamanız için IntelliTrace yapılandırmanız gerekir. IntelliTrace yapılandırmadan uygulamanızı yayımlayın, projeyi yeniden yayımlamanız gerekir. Daha fazla bilgi için bkz. [Visual Studio kullanarak Azure bulut hizmetleri projelerini yayımlama](https://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Azure uygulamanızı dağıtmaya hazırsanız, proje derleme hedeflerinizin **hata ayıklama**olarak ayarlandığını doğrulayın.

1. **Çözüm Gezgini**, proje öğesine sağ tıklayın ve bağlam menüsünden **Yayımla**' yı seçin.
   
1. **Azure uygulaması Yayımla** Iletişim kutusunda Azure aboneliğini seçin ve **İleri**' yi seçin.

1. **Ayarlar** sayfasında, **Gelişmiş ayarlar** sekmesini seçin.

1. Bulutta yayımlandığında uygulamanıza yönelik IntelliTrace günlüklerini toplamak için **IntelliTrace 'ı etkinleştir** seçeneğini etkinleştirin.
   
1. Temel IntelliTrace yapılandırmasını özelleştirmek için, **IntelliTrace 'ı etkinleştir ' in**yanındaki **Ayarlar** ' ı seçin.

    ![IntelliTrace ayarları bağlantısı](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. **IntelliTrace ayarları** iletişim kutusunda, hangi olayların günlüğe alınacağını, çağrı bilgilerinin toplanmasını, hangi modüllerin ve işlemlerin toplanacağını toplayacağınızı ve kayda ne kadar alan ayrılacağını belirtebilirsiniz. IntelliTrace hakkında daha fazla bilgi için bkz. [IntelliTrace Ile hata ayıklama](https://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![IntelliTrace ayarları](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace günlük (varsayılan boyutu 250 MB'tır) IntelliTrace ayarlarında belirtilen disk boyutu, döngüsel günlük dosyasıdır. Sanal makine dosya sistemindeki bir dosyaya IntelliTrace günlükleri toplanır. Günlükleri istediğinizde, bir anlık görüntü o noktasında alınan ve yerel bilgisayarınıza indirilir.

Azure bulut hizmeti Azure 'da yayımlandıktan sonra, aşağıdaki görüntüde gösterildiği gibi, IntelliTrace 'in **Sunucu Gezgini**Azure düğümünden etkinleştirilip etkinleştirilmediğini belirleyebilirsiniz:

![Sunucu Gezgini - etkin IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Bir rol örneği için IntelliTrace günlüklerini indir
Visual Studio kullanarak, aşağıdaki adımları izleyerek bir rol örneği için IntelliTrace günlüklerini indirebilirsiniz:

1. **Sunucu Gezgini**' de, **Cloud Services** düğümünü genişletin ve günlüklerini indirmek istediğiniz rol örneğini bulun. 

1. Rol örneğine sağ tıklayın ve s bağlam menüsünde **IntelliTrace günlüklerini görüntüle**' yi seçin. 

    ![IntelliTrace günlüklerini menü seçeneği görüntüleyin](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace günlüklerinin yerel bilgisayarınızda bir dizindeki bir dosya indirilir. IntelliTrace istek her zaman günlükleri, yeni bir anlık görüntü oluşturulur. Günlükler indirilirken, Visual Studio işlemin ilerleme durumunu **Azure etkinlik günlüğü** penceresinde görüntüler. Aşağıdaki resimde gösterildiği gibi işlemin daha fazla ayrıntı görmek için satır öğesi genişletebilirsiniz.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace günlüklerini indirerek Visual Studio'da çalışmaya devam edebilirsiniz. Günlük indirmeyi bitirdiğinde, Visual Studio'da açılır.

> [!NOTE]
> IntelliTrace günlüklerini framework oluşturur ve ardından işleyen özel durumları içerebilir. Bu özel durumlar için bunları güvenle yoksayabilirsiniz bir rolü, başlatma, normal bir parçası olarak iç framework kod oluşturur.
> 
> 

## <a name="next-steps"></a>Sonraki adımlar
- [Azure bulut hizmetlerinde hata ayıklama seçenekleri](vs-azure-tools-debugging-cloud-services-overview.md)
- [Visual Studio kullanarak Azure bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md)