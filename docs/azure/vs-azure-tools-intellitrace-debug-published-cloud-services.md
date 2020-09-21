---
title: IntelliTrace ile yayımlanan Azure bulut hizmetinde hata ayıklama
ms.custom: SEO-VS-2020
description: Visual Studio ve IntelliTrace ile bir bulut hizmetinde hata ayıklamayı öğrenin
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: b89ed536e6483f54d4d7370a02935728dedfb517
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809826"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Visual Studio ve IntelliTrace ile yayımlanan bir Azure bulut hizmetinin hatalarını ayıklama
IntelliTrace ile, Azure 'da çalıştırıldığında bir rol örneği için kapsamlı hata ayıklama bilgilerini günlüğe kaydedebilirsiniz. Bir sorunun nedenini bulmanız gerekiyorsa, Visual Studio 'dan Azure 'da çalışıyor gibi kodunuzda adım adım ilerlemek için IntelliTrace günlüklerini kullanabilirsiniz. Aslında, IntelliTrace anahtar kodu yürütme ve ortam verilerini Azure uygulamanız Azure 'da bir bulut hizmeti olarak çalışırken kaydeder ve kaydedilen verileri Visual Studio 'dan yeniden oynamanızı sağlar.

Visual Studio Enterprise yüklüyse ve Azure uygulamanız .NET Framework 4 veya sonraki bir sürümü hedeflerse IntelliTrace 'i kullanabilirsiniz. IntelliTrace, Azure rolleriniz için bilgi toplar. Bu rollerin sanal makineleri daima 64 bitlik işletim sistemlerini çalıştırır.

Alternatif olarak, [Uzaktan hata ayıklamayı](vs-azure-tools-debugging-cloud-services-overview.md) kullanarak doğrudan Azure 'da çalışan bir bulut hizmetine ekleyebilirsiniz.

> [!IMPORTANT]
> IntelliTrace yalnızca hata ayıklama senaryolarına yöneliktir ve bir üretim dağıtımı için kullanılmamalıdır.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>IntelliTrace için bir Azure uygulaması yapılandırma
Bir Azure uygulaması için IntelliTrace 'i etkinleştirmek üzere uygulamayı bir Visual Studio Azure projesinden oluşturmanız ve yayımlamanız gerekir. Azure 'a yayımlamadan önce Azure uygulamanız için IntelliTrace 'i yapılandırmanız gerekir. Uygulamanızı IntelliTrace yapılandırması olmadan yayımlarsanız projeyi yeniden yayımlamanız gerekir. Daha fazla bilgi için bkz. [Visual Studio kullanarak Azure bulut hizmetleri projelerini yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

1. Azure uygulamanızı dağıtmaya hazırsanız, proje derleme hedeflerinizin **hata ayıklama**olarak ayarlandığını doğrulayın.

1. **Çözüm Gezgini**, proje öğesine sağ tıklayın ve bağlam menüsünden **Yayımla**' yı seçin.

1. **Azure uygulaması Yayımla** Iletişim kutusunda Azure aboneliğini seçin ve **İleri**' yi seçin.

1. **Ayarlar** sayfasında, **Gelişmiş ayarlar** sekmesini seçin.

1. Bulutta yayımlandığında uygulamanıza yönelik IntelliTrace günlüklerini toplamak için **IntelliTrace 'ı etkinleştir** seçeneğini etkinleştirin.

1. Temel IntelliTrace yapılandırmasını özelleştirmek için, **IntelliTrace 'ı etkinleştir ' in**yanındaki **Ayarlar** ' ı seçin.

    ![IntelliTrace ayarları bağlantısı](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. **IntelliTrace ayarları** iletişim kutusunda, hangi olayların günlüğe alınacağını, çağrı bilgilerinin toplanmasını, hangi modüllerin ve işlemlerin toplanacağını toplayacağınızı ve kayda ne kadar alan ayrılacağını belirtebilirsiniz. IntelliTrace hakkında daha fazla bilgi için bkz. [IntelliTrace Ile hata ayıklama](../debugger/intellitrace.md).

    ![IntelliTrace ayarları](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

IntelliTrace günlüğü, IntelliTrace ayarlarında belirtilen en büyük boyutun (varsayılan boyut 250 MB 'tır) bir dairesel günlük dosyasıdır. IntelliTrace günlükleri, sanal makinenin dosya sistemindeki bir dosyaya toplanır. Günlükleri istediğinizde, o zaman bu noktada bir anlık görüntü alınır ve yerel bilgisayarınıza indirilir.

Azure bulut hizmeti Azure 'da yayımlandıktan sonra, aşağıdaki görüntüde gösterildiği gibi, IntelliTrace 'in **Sunucu Gezgini**Azure düğümünden etkinleştirilip etkinleştirilmediğini belirleyebilirsiniz:

![Sunucu Gezgini-IntelliTrace etkin](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Rol örneği için IntelliTrace günlüklerini indirin
Visual Studio 'yu kullanarak, aşağıdaki adımları izleyerek bir rol örneği için IntelliTrace günlüklerini indirebilirsiniz:

1. **Sunucu Gezgini**' de, **Cloud Services** düğümünü genişletin ve günlüklerini indirmek istediğiniz rol örneğini bulun.

1. Rol örneğine sağ tıklayın ve s bağlam menüsünde **IntelliTrace günlüklerini görüntüle**' yi seçin.

    ![IntelliTrace günlüklerini görüntüle menü seçeneği](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. IntelliTrace günlükleri yerel bilgisayarınızdaki bir dizindeki bir dosyaya indirilir. IntelliTrace günlüklerini her istediğinizde yeni bir anlık görüntü oluşturulur. Günlükler indirilirken, Visual Studio işlemin ilerleme durumunu **Azure etkinlik günlüğü** penceresinde görüntüler. Aşağıdaki şekilde gösterildiği gibi, daha fazla ayrıntı görmek için işlem için satır öğesini genişletebilirsiniz.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

IntelliTrace günlükleri indirilirken Visual Studio 'da çalışmaya devam edebilirsiniz. Günlüğün indirilmesi tamamlandığında, Visual Studio 'da açılır.

> [!NOTE]
> IntelliTrace günlükleri Framework 'ün oluşturduğu ve daha sonra işlediği özel durumlar içerebilir. İç Framework kodu bu özel durumları bir rolün başlatılmasının normal bir parçası olarak oluşturur, bu nedenle onları güvenle yoksayabilirsiniz.
>
>

## <a name="next-steps"></a>Sonraki adımlar
- [Azure bulut hizmetlerinde hata ayıklama seçenekleri](vs-azure-tools-debugging-cloud-services-overview.md)
- [Visual Studio kullanarak Azure bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md)