---
title: Azure uygulamaları ASP.NET hata ayıklama
titleSuffix: Visual Studio Enterprise
description: Anlık görüntü noktaları ayarlamak Snapshot Debugger azure Visual Studio canlı hata ayıklaması yaparken anlık görüntü almak için ASP.NET öğrenin.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 94c65814572c99f95d7a6edc6769e5af0ea6e748
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798381"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Snapshot Debugger kullanarak Azure ASP.NET canlı uygulama hata ayıklaması Snapshot Debugger

Bu Snapshot Debugger, ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Anlık bileşen ve günlük noktaları kesme noktalarına benzer, ancak kesme noktanın aksine, anlık ek nokta isabetli olduğunda uygulamayı durdurmaz. Genellikle anlık görüntüyü bir anlık görüntüde yakalama 10-20 milisaniye sürer.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Start the Snapshot Debugger
> * Anlık görüntü ayarlama ve anlık görüntüyü görüntüleme
> * Günlük noktası ayarlama

## <a name="prerequisites"></a>Önkoşullar

* Snapshot Debugger, Azure geliştirme iş yüküyle Visual Studio 2017 Enterprise sürüm 15.5 veya daha yeni bir **sürümden başlayarak kullanılabilir.** (Bağımsız **bileşenler sekmesinde** Hata ayıklama ve test altında **bulabilirsiniz**  >  **Snapshot debugger**.)

   ::: moniker range=">=vs-2019"
   Henüz yüklü değilse, [2019'Visual Studio yükleyin.](https://visualstudio.microsoft.com/downloads) Önceki bir Visual Studio yüklemesini güncelleştiriyorsanız, Visual Studio Yükleyicisi'i çalıştırın ve Snapshot Debugger ve web geliştirme **iş yükünde ASP.NET bileşenini kontrol edin.**
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   Henüz yüklenmemişse, [2017 Enterprise Visual Studio 15.5 veya sonraki bir sürümü](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) yükleyin. Önceki bir Visual Studio 2017 yüklemesini güncelleştiriyorsanız, Visual Studio Yükleyicisi'i çalıştırın ve Snapshot Debugger ve web geliştirme iş yükünde **ASP.NET bileşenini kontrol edin.**
   ::: moniker-end

* Temel veya daha Azure App Service plan.

* Anlık görüntü koleksiyonu, aşağıdaki web uygulamaları için Azure App Service:
  * .NET Framework 4.6.1 veya sonraki sürümlerde çalışan uygulamalar ASP.NET.
  * .NET Core 2,0 veya üzeri sürümlerde çalışan uygulamaları Windows üzerinde ASP.NET Core.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Projenizi açın ve Snapshot Debugger başlatın

1. Anlık görüntü hata ayıklaması yapmak istediğiniz projeyi açın.

   > [!IMPORTANT]
   > Hata ayıklamanın anlık görüntüsünü almak için Azure App Service yayımlanan *kaynak kodu sürümünü* açmanız gerekir.

::: moniker range="<=vs-2017"

2. Cloud Explorer 'da (**bulut gezginini > görüntüleyin**), projenizin dağıtıldığı Azure App Service sağ tıklayın ve **Snapshot Debugger Ekle**' yi seçin.

   ![Snapshot Debugger 'ı başlatın](../debugger/media/snapshot-launch.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. **Hata ayıkla > Snapshot Debugger Ekle...** seçeneğini belirleyin. Projenizin dağıtıldığı Azure App Service seçin ve bir Azure depolama hesabına ve ardından **Ekle**' ye tıklayın. Snapshot Debugger Ayrıca, sanal makine ölçek kümeleri & [Azure Kubernetes hizmetini](debug-live-azure-kubernetes.md) ve [Azure sanal makinelerini (VM)](debug-live-azure-virtual-machines.md)destekler.

   ![Hata ayıklama menüsünden Snapshot Debugger 'ı başlatın](../debugger/media/snapshot-debug-menu-attach.png)

   ![Azure kaynağı seçin](../debugger/media/snapshot-select-azure-resource-appservices.png)

::: moniker-end

   > [!IMPORTANT]
   > **Snapshot Debugger Ekle**' yi ilk kez seçtiğinizde, Snapshot Debugger site uzantısını Azure App Service yüklemeniz istenir. Bu yükleme Azure App Service yeniden başlatılmasını gerektirir.

   ::: moniker range="<=vs-2017"
   > [!NOTE]
   > Application Insights site uzantısı anlık görüntü hata ayıklamayı da destekler. "Site uzantısı güncel değil" hata iletisiyle karşılaşırsanız, ayrıntıları yükseltmek için bkz. [sorun giderme ipuçları ve anlık görüntü hata ayıklaması için bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md) .
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   > [!NOTE]
   > (Visual Studio 2019 sürüm 16,2 ve üstü) Snapshot Debugger Azure bulut desteğini etkinleştirdi. Seçtiğiniz Azure kaynağının ve Azure depolama hesabının aynı buluttan olduğundan emin olun. Kuruluşunuzun [Azure uyumluluk](https://azure.microsoft.com/overview/trusted-cloud/) yapılandırmalarına ilişkin sorularınız varsa lütfen Azure yöneticinize başvurun.
   ::: moniker-end

   Visual Studio artık Snapshot hata ayıklama modunda.
   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

   Modüller **penceresi,** tüm modüller Azure App Service yüklendiğinde gösterilir (bu pencereyi açmak > **Windows >** Modüller'de hata ayıkla'ya tıklayın).

   ![Modüller penceresini denetleme](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ek bileşen ayarlama

1. Kod düzenleyicisinde, bir ek bileşen ayarlamak için ilgilendiğimiz bir kod çizgisinin yanındaki sol olukluna tıklayın. Yürütülecek kodun bu olduğundan emin olun.

   ![Ek bileşen ayarlama](../debugger/media/snapshot-set-snappoint.png)

2. Ek **bileşeni açmak** için Koleksiyonu Başlat'a tıklayın.

   ![Ek bileşen noktası açma](../debugger/media/snapshot-start-collection.png)

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

   Web sitesinin kendisi hala canlı ve son kullanıcılar bundan etkilenmez. Varsayılan olarak, anlık görüntü noktası başına yalnızca bir anlık görüntü yakalanır: bir anlık görüntü yakalandıktan sonra, anlık görüntü açılır. Anlık görüntü noktasında başka bir anlık görüntü yakalamak istiyorsanız, **koleksiyonu Güncelleştir**' e tıklayarak anlık görüntü noktasını yeniden açabilirsiniz.

Ayrıca, uygulamanıza daha fazla anlık görüntü ekleyebilir ve **koleksiyonu Güncelleştir** düğmesiyle bu noktaları açabilirsiniz.

**Yardıma mı ihtiyacınız var?** [Anlık görüntü hata ayıklama sayfaları Için](../debugger/debug-live-azure-apps-faq.yml) [sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md) ve SSS bölümüne bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu bir anlık görüntü noktası ayarlama

Uygulamanızda belirli bir durumu yeniden oluşturmayı zorlaştırıyorsa, koşullu bir anlık görüntü noktası kullanmayı düşünün. Koşullu anlık görüntü noktaları, bir değişken, incelemek istediğiniz belirli bir değeri içerdiğinde olduğu gibi, bir anlık görüntünün ne zaman ele alıp denetistemediğinizi denetlemenize yardımcı olur. İfadeleri ifade, filtre veya isabet sayısı kullanarak ayarlayabilirsiniz.

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

   ![Günlük noktası oluşturma](../debugger/media/snapshot-logpoint.png)

1. İleti **alanına,** günlüğe almak istediğiniz yeni günlük iletiyi girebilirsiniz. Ayrıca günlük iletinizin değişkenlerini küme ayraçlarına yerleştirerek de değerlendirebilirsiniz.

   **Çıkış Penceresi'a gönder'i** seçerseniz, günlüğe kaydedilirse, ileti Tanılama Araçları görüntülenir.

   ![Tanılama Araçları penceresinde verileri günlüğe Tanılama Araçları noktası](../debugger/media/snapshot-logpoint-output.png)

   Uygulama günlüğüne **gönder'i** seçerseniz, günlüğe kaydedilirse, ileti App Insights gibi `System.Diagnostics.Trace` (veya `ILogger` .NET Core'da) iletileri gördüğünüz her yerde [görüntülenir.](/azure/application-insights/app-insights-asp-net-trace-logs)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, App Services için Snapshot Debugger kullanmayı öğrendiniz. Bu özellik hakkında daha fazla ayrıntıyı okumak istiyor olabilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)