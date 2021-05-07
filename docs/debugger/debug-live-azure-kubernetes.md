---
title: Azure Kubernetes Services ASP.NET canlı hata ayıklama
description: Azure Kubernetes Services'Snapshot Debugger canlı hata ayıklaması Visual Studio anlık görüntü almak için ASP.NET nasıl kullanabileceğinizi öğrenin.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: c1c8a593d147b8ba38393aabd89b293e0fbd5d26
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798472"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Azure Kubernetes Services ASP.NET de canlı hata ayıklaması Snapshot Debugger

Bu Snapshot Debugger, ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Anlık bileşen ve günlük noktaları kesme noktalarına benzer, ancak kesme noktanın aksine, anlık ek nokta isabetli olduğunda uygulamayı durdurmaz. Genellikle anlık görüntüyü bir anlık görüntüde yakalama 10-20 milisaniye sürer.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Start the Snapshot Debugger
> * Anlık görüntü ayarlama ve anlık görüntüyü görüntüleme
> * Günlük noktası ayarlama

## <a name="prerequisites"></a>Önkoşullar

* Azure Kubernetes Services Snapshot Debugger 2019 Enterprise Visual Studio veya daha yüksek bir azure **geliştirme iş yükü için kullanılabilir.** (Bağımsız **bileşenler sekmesinde** Hata ayıklama ve test altında **bulabilirsiniz**  >  **Snapshot debugger**.)

    Henüz yüklü değilse, [2019 Enterprise Visual Studio yükleyin.](https://visualstudio.microsoft.com/vs/)

* Anlık görüntü koleksiyonu aşağıdaki Azure Kubernetes Services web uygulamaları için kullanılabilir:
  * ASP.NET Debian 9'da .NET Core 2.2 veya sonraki bir sürümü üzerinde çalışan ASP.NET Core uygulamaları.
  * ASP.NET 3.8'de .NET Core 2.2 veya sonraki bir üzerinde çalışan ASP.NET Core uygulamaları.
  * ubuntu 18.04'te .NET Core 2.2 veya üzerinde çalışan ASP.NET Core uygulamaları.

    > [!NOTE]
    > AKS'de veri Snapshot Debugger yardımcı olmak için Docker görüntülerine kurulumu gösteren [bir dizi Dockerfile içeren bir repo sağladık.](https://github.com/Microsoft/vssnapshotdebugger-docker)

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Projenizi açın ve Snapshot Debugger başlatın

1. Anlık görüntü hata ayıklaması yapmak istediğiniz projeyi açın.

    > [!IMPORTANT]
    > Hata ayıklamanın anlık görüntüsünü almak için Azure Kubernetes hizmetinize yayınlanan *kaynak kodu sürümünü* açmanız gerekir.

1. **Hata ayıkla > Snapshot Debugger Ekle...** seçeneğini belirleyin. Web uygulamanızın dağıtıldığı AKS kaynağını ve bir Azure Depolama hesabını seçin ve ardından **Ekle**' ye tıklayın. Snapshot Debugger Ayrıca, [](debug-live-azure-applications.md) [sanal makine ölçek kümelerini & Azure App Service ve Azure sanal makinelerini (VM)](debug-live-azure-virtual-machines.md)destekler.

    ![Hata ayıklama menüsünden Snapshot Debugger 'ı başlatın](../debugger/media/snapshot-debug-menu-attach.png)

    ![Azure kaynağı seçin](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 sürüm 16,2 ve üstü) Snapshot Debugger Azure bulut desteğini etkinleştirdi. Seçtiğiniz Azure kaynağının ve Azure depolama hesabının aynı buluttan olduğundan emin olun. Kuruluşunuzun [Azure uyumluluk](https://azure.microsoft.com/overview/trusted-cloud/) yapılandırmalarına ilişkin sorularınız varsa lütfen Azure yöneticinize başvurun.

Visual Studio artık Snapshot hata ayıklama modunda.

   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

   **Modüller** penceresi, tüm modüllerin Azure App Service için ne zaman yüklendiğini gösterir (Bu pencereyi açmak için **Windows > modülleri > hata ayıkla** ' yı seçin).

   ![Modüller penceresini denetleyin](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Anlık görüntü noktası ayarla

1. Kod Düzenleyicisi 'nde, bir anlık görüntü noktası ayarlamak için ilgilendiğiniz kod satırının yanındaki sol cilt payı tıklatın. Uygulamasının çalıştırabildiğinizi bildiğiniz kodun olduğundan emin olun.

   ![Anlık görüntü noktası ayarla](../debugger/media/snapshot-set-snappoint.png)

1. Anlık görüntü noktasını açmak için **toplamayı Başlat** ' a tıklayın.

   ![Anlık görüntü noktasını aç](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Bir anlık görüntüyü görüntülerken adım adım atabilirsiniz, ancak farklı kod satırlarında yürütmeyi takip etmek için kodunuza birden çok ek bileşen yer almaktadır. Kodunda birden çok ek bileşen varsa, Snapshot Debugger anlık görüntülerin aynı son kullanıcı oturumundan olduğundan emin olun. Uygulama Snapshot Debugger çok sayıda kullanıcı olsa bile bunu yapar.

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir ek bileşen ayarlandıktan sonra, web sitenizin tarayıcı görünümüne gidip işaretlenmiş kod satırı çalıştırarak el ile anlık görüntü oluşturabilir veya kullanıcılarının site kullanımlarından bir anlık görüntü oluşturmasını bekleyebilirsiniz.

## <a name="inspect-snapshot-data"></a>Anlık görüntü verilerini inceleme

1. Anlık görüntü, anlık görüntüye isabet Tanılama Araçları görüntülenir. Bu pencereyi açmak için Windows **> Show > hata ayıkla'Tanılama Araçları.**

    ![Ek bileşen noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Anlık görüntüyü kod düzenleyicisinde açmak için anlık görüntüye çift tıklayın.

    ![Anlık görüntü verilerini inceleme](../debugger/media/snapshot-inspect-data.png)

    Bu görünümden değişkenlerin üzerine gelerek DataTips'i görüntüleyebilirsiniz, Yereller, **İzlemeler** ve **Çağrı** Yığını pencerelerini kullanabilir ve ifadeleri değerlendirebilirsiniz.

    Web sitesinin kendisi hala canlı ve son kullanıcılar bundan etkilenmez. Varsayılan olarak her anlık görüntüde yalnızca bir anlık görüntü yakalanır: Bir anlık görüntü yakalandikten sonra anlık görüntü kapattır. Ek bileşende başka bir anlık görüntü yakalamak için, Koleksiyonu Güncelleştir'e tıklayarak anlık görüntüyü **yeniden açabilirsiniz.**

Ayrıca, uygulamanıza daha fazla ek bileşen ekleyebilir ve Koleksiyonu Güncelleştir düğmesiyle **bunları açabilirsiniz.**

**Yardıma mı ihtiyacınız var?** Anlık görüntü [hata ayıklama sayfaları için Sorun giderme](../debugger/debug-live-azure-apps-troubleshooting.md) ve bilinen sorunlar ve [SSS bölümüne](../debugger/debug-live-azure-apps-faq.yml) bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu ek bileşen ayarlama

Uygulamanıza belirli bir durumu yeniden oluşturmak zorsa koşullu ek bileşen kullanmayı göz önünde bulundurabilirsiniz. Koşullu ek bileşen, bir değişkenin incelemek istediğiniz belirli bir değeri içerdiği durumlarda anlık görüntü alma zamanlarını denetlemeye yardımcı olur. İfadeleri, filtreleri veya isabet sayılarını kullanarak koşulları ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-snappoint"></a>Koşullu bir anlık görüntü noktası oluşturmak için

1. Bir anlık görüntü noktası simgesine (boş top) sağ tıklayın ve **Ayarlar**' ı seçin.

   ![Ayarlar'ı seçme](../debugger/media/snapshot-snappoint-settings.png)

1. Anlık görüntü noktası ayarları penceresinde bir ifade yazın.

   ![Bir ifade yazın](../debugger/media/snapshot-snappoint-conditions.png)

   Önceki çizimde, anlık görüntü yalnızca ne zaman anlık görüntü noktası için alınır `visitor.FirstName == "Dan"` .

## <a name="set-a-logpoint"></a>Günlüğe kaydetme noktası ayarlama

Anlık görüntü noktası isabet edildiğinde bir anlık görüntü almaya ek olarak, bir anlık görüntü noktasını bir iletiyi günlüğe kaydetmek için de yapılandırabilirsiniz (yani, bir logpoint oluşturun). Uygulamanızı yeniden dağıtmak zorunda kalmadan günlüğe kaydetme noktaları ayarlayabilirsiniz. Günlüğe kaydetme noktaları neredeyse yürütülür ve çalışan uygulamanız üzerinde hiçbir etkisi veya yan etkiye neden olmaz.

#### <a name="to-create-a-logpoint"></a>Günlüğe kaydetme noktası oluşturmak için

1. Bir anlık görüntü noktası simgesine (mavi altıon) sağ tıklayın ve **Ayarlar**' ı seçin.

1. Anlık görüntü noktası ayarları penceresinde **Eylemler**' i seçin.

    ![Günlüğe kaydetme noktası oluşturma](../debugger/media/snapshot-logpoint.png)

1. **İleti** alanına, günlüğe kaydetmek istediğiniz yeni günlük iletisini girebilirsiniz. Ayrıca, günlük iletinizde değişkenleri küme ayraçları içine yerleştirerek değerlendirebilirsiniz.

    **Çıkış penceresi gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, tanılama araçları penceresinde görünür.

    ![Tanılama Araçları penceresindeki logpoint verileri](../debugger/media/snapshot-logpoint-output.png)

    **Uygulama günlüğüne gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, `System.Diagnostics.Trace` `ILogger` [uygulama öngörüleri](/azure/application-insights/app-insights-asp-net-trace-logs)gibi (veya .NET Core) iletileri görebileceğiniz her yerde görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Azure Kubernetes için Snapshot Debugger kullanmayı öğrendiniz. Bu özellik hakkında daha fazla ayrıntı okumak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)