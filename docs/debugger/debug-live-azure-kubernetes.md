---
title: Azure Kubernetes Services ASP.NET canlı hata ayıklama
description: Azure Kubernetes Services Snapshot Debugger hata ayıklarken anlık Visual Studio ve anlık görüntü almak için ASP.NET kullanmayı öğrenin.
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
ms.openlocfilehash: 43676a14dae83cde448ed032c0bbef46be2ee3fb55a6c0f4e60c91e2fc4f5f5a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344370"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Snapshot Debugger ASP.NET kullanarak Azure Kubernetes Services'de canlı Snapshot Debugger

Bu Snapshot Debugger, ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Anlık ek nokta ve günlük noktaları kesme noktalarına benzer, ancak kesme noktanın aksine, anlık ek nokta isabetli olduğunda uygulamayı durdurmaz. Bir anlık görüntüyü anlık görüntü yakalama genellikle 10-20 milisaniye sürer.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Start the Snapshot Debugger
> * Anlık görüntü ayarlama ve anlık görüntüyü görüntüleme
> * Günlük noktası ayarlama

## <a name="prerequisites"></a>Önkoşullar

* Azure Kubernetes Services için Snapshot Debugger 2019 Visual Studio 2019 veya Enterprise azure geliştirme iş **yükü ile kullanılabilir.** (Bağımsız **bileşenler sekmesinde** Hata ayıklama ve test altında **bulabilirsiniz**  >  **Snapshot debugger**.)

    Henüz yüklü değilse, [2019'Visual Studio yükleyin Enterprise.](https://visualstudio.microsoft.com/vs/)

* Anlık görüntü koleksiyonu aşağıdaki Azure Kubernetes Services web uygulamaları için kullanılabilir:
  * ASP.NET Core Debian 9'da .NET Core 2.2 veya sonraki bir sürümü üzerinde çalışan uygulamaları içerir.
  * ASP.NET Core 3.8'de .NET Core 2.2 veya sonraki bir üzerinde çalışan uygulamaları içerir.
  * ASP.NET Core Ubuntu 18.04'te .NET Core 2.2 veya sonraki sürümleri üzerinde çalışan uygulamalar.

    > [!NOTE]
    > AKS'de veri Snapshot Debugger yardımcı olmak için Docker görüntülerine kurulumu gösteren [bir dizi Dockerfile içeren bir repo sağladık.](https://github.com/Microsoft/vssnapshotdebugger-docker)

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Projenizi açın ve Snapshot Debugger

1. Hata ayıklamanın anlık görüntüsünü açmak için projeyi açın.

    > [!IMPORTANT]
    > Hata ayıklamanın anlık görüntüsünü ayıklamak için Azure Kubernetes hizmetinize yayımlanan kaynak kodun aynı sürümünü açmanız gerekir. 

1. Hata **Ayıkla ve > Ekle... Snapshot Debugger seçin.** Web uygulamasının dağıtılacağı AKS kaynağını ve bir Azure depolama hesabını seçin ve ardından Ekle'ye **tıklayın.** Snapshot Debugger, Sanal [Azure App Service](debug-live-azure-applications.md) Kümeleri için [Azure Sanal Makineleri (VM) & sanal makineleri de destekler.](debug-live-azure-virtual-machines.md)

    ![Hata Ayıklama menüsünden anlık görüntü hata ayıklayıcısını başlatma](../debugger/media/snapshot-debug-menu-attach.png)

    ![Azure Kaynağı'ı seçin](../debugger/media/snapshot-select-azure-resource-aks.png)

    > [!NOTE]
    > (Visual Studio 2019 sürüm 16.2 ve üzeri) Snapshot Debugger Azure bulut desteğini etkinleştirdi. Hem Azure kaynağının hem de Azure Depolama hesabının aynı bulutta olduğundan emin olun. Kuruma ilişkin Azure uyumluluk yapılandırmaları hakkında sorularınız varsa lütfen [Azure yöneticinize](https://azure.microsoft.com/overview/trusted-cloud/) başvurun.

Visual Studio artık anlık görüntü hata ayıklama modunda.

   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

   Modüller **penceresi,** modüller için tüm modüller yüklendiğinde size Azure App Service  (bu pencereyi açmak için > Windows > Modüllerde Hata Ayıkla'ya tıklayın).

   ![Modüller penceresini denetleme](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ek bileşen ayarlama

1. Kod düzenleyicisinde, bir ek bileşen ayarlamak için ilgilendiğimiz bir kod çizgisinin yanındaki sol olukluna tıklayın. Yürütülecek kodun bu olduğundan emin olun.

   ![Ek bileşen ayarlama](../debugger/media/snapshot-set-snappoint.png)

1. Ek **bileşeni açmak** için Koleksiyonu Başlat'a tıklayın.

   ![Ek bileşen noktası açma](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Bir anlık görüntüyü görüntülerken adım adım atabilirsiniz, ancak farklı kod satırlarında yürütmeyi takip etmek için kodunuza birden çok ek bileşen yer almaktadır. Kodunda birden çok ek bileşen varsa, Snapshot Debugger anlık görüntülerin aynı son kullanıcı oturumundan olduğundan emin olun. Uygulama Snapshot Debugger çok sayıda kullanıcı olsa bile bunu yapar.

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir ek bileşen ayarlandıktan sonra, web sitenizin tarayıcı görünümüne gidip işaretlenmiş kod satırı çalıştırarak el ile anlık görüntü oluşturabilir veya kullanıcılarının site kullanımlarından bir anlık görüntü oluşturmasını bekleyebilirsiniz.

## <a name="inspect-snapshot-data"></a>Anlık görüntü verilerini inceleme

1. Anlık görüntü, anlık görüntüye isabet Tanılama Araçları görüntülenir. Bu pencereyi açmak için Hata **ayıkla'> Windows > Show Tanılama Araçları**.

    ![Ek bileşen noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Anlık görüntüyü kod düzenleyicisinde açmak için anlık görüntüye çift tıklayın.

    ![Anlık görüntü verilerini inceleme](../debugger/media/snapshot-inspect-data.png)

    Bu görünümden değişkenlerin üzerine gelerek DataTips'i görüntüleyebilirsiniz, Yereller, **İzlemeler** ve **Çağrı** Yığını pencerelerini kullanabilir ve ifadeleri değerlendirebilirsiniz.

    Web sitesinin kendisi hala canlı ve son kullanıcılar bundan etkilenmez. Varsayılan olarak her anlık görüntüde yalnızca bir anlık görüntü yakalanır: Bir anlık görüntü yakalandikten sonra anlık görüntü kapattır. Ek bileşende başka bir anlık görüntü yakalamak için, Koleksiyonu Güncelleştir'e tıklayarak anlık görüntüyü **yeniden açabilirsiniz.**

Ayrıca, uygulamanıza daha fazla ek bileşen ekleyebilir ve Koleksiyonu Güncelleştir düğmesiyle **bunları açabilirsiniz.**

**Yardıma mı ihtiyacınız var?** Anlık görüntü [hata ayıklama sayfaları için Sorun giderme](../debugger/debug-live-azure-apps-troubleshooting.md) ve bilinen sorunlar ve [SSS bölümüne](../debugger/debug-live-azure-apps-faq.yml) bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu ek bileşen ayarlama

Uygulamanıza belirli bir durumu yeniden oluşturmak zorsa koşullu ek bileşen kullanmayı göz önünde bulundurabilirsiniz. Koşullu ek bileşen, bir değişkenin incelemek istediğiniz belirli bir değeri içerdiği durumlarda anlık görüntü alma zamanlarını denetlemeye yardımcı olur. İfadeleri, filtreleri veya isabet sayılarını kullanarak koşulları ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-snappoint"></a>Koşullu ek bileşen oluşturmak için

1. Bir anlık görüntü simgesine (boş top) sağ tıklayın ve **Ayarlar.**

   ![Ayarlar'ı seçme](../debugger/media/snapshot-snappoint-settings.png)

1. Ek bileşen ayarları penceresinde bir ifade yazın.

   ![İfade yazma](../debugger/media/snapshot-snappoint-conditions.png)

   Yukarıdaki çizimde anlık görüntü yalnızca anlık görüntü için olduğunda `visitor.FirstName == "Dan"` alınır.

## <a name="set-a-logpoint"></a>Günlük noktası ayarlama

Bir anlık görüntüye isabet olduğunda anlık görüntü almaya ek olarak, bir ileti günlüğe (yani, bir günlük noktası oluşturmak) için bir anlık görüntü de yapılandırabilirsiniz. Oturum açma noktaları, uygulamanın yeniden bir şekilde yenidend bayılamanıza gerek kalmadan ayarlandırabilirsiniz. Günlük noktaları sanal olarak yürütülür ve çalışan uygulamanıza hiçbir etkisi veya yan etkisi olmaz.

#### <a name="to-create-a-logpoint"></a>Günlük noktası oluşturmak için

1. Bir ek bileşen simgesine (mavi altıgen) sağ tıklayın ve **Ayarlar.**

1. Ek bileşen ayarları penceresinde Eylemler'i **seçin.**

    ![Günlük noktası oluşturma](../debugger/media/snapshot-logpoint.png)

1. İleti **alanına,** günlüğe almak istediğiniz yeni günlük iletiyi girebilirsiniz. Ayrıca günlük iletinizin değişkenlerini küme ayraçlarına yerleştirerek de değerlendirebilirsiniz.

    **Çıkış Penceresi'a** gönder'i seçerseniz, günlüğe kaydedilirse, ileti Tanılama Araçları görüntülenir.

    ![Tanılama Araçları penceresinde verileri günlüğe Tanılama Araçları noktası](../debugger/media/snapshot-logpoint-output.png)

    Uygulama günlüğüne **gönder'i** seçerseniz, günlüğe kaydedilirse, ileti App Analizler gibi üzerinden `System.Diagnostics.Trace` (veya `ILogger` .NET Core'da) iletileri gördüğünüz her [yerde görüntülenir.](/azure/application-insights/app-insights-asp-net-trace-logs)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide Azure Kubernetes için Snapshot Debugger kullanmayı öğrendiniz. Bu özellik hakkında daha fazla ayrıntıyı okumak istiyor olabilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)