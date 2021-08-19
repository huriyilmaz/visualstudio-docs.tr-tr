---
title: canlı ASP.NET Azure uygulamalarında hata ayıklama
titleSuffix: Visual Studio Enterprise
description: canlı ASP.NET Azure uygulamalarında hata ayıklama sırasında, anlık görüntü noktalarını ayarlamak ve anlık görüntüleri almak için Visual Studio Snapshot Debugger nasıl kullanacağınızı öğrenin.
ms.custom: ''
ms.date: 03/16/2018
ms.topic: how-to
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 288c13dbf249bfe953f46886cc55dee6e1408515
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090959"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Snapshot Debugger kullanarak canlı ASP.NET Azure uygulamalarında hata ayıklama

Snapshot Debugger, çalışırken ilgilendiğiniz kod olduğunda üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya bir anlık görüntü almasını söylemek için kodunuzda anlık görüntü noktaları ve günlüğe kaydetme noktaları ayarlarsınız. Hata ayıklayıcı, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

Anlık görüntü noktaları ve günlüğe kaydetme noktaları, kesme noktalarıyla benzerdir, ancak kesme noktalarından farklı olarak, anlık görüntü noktaları, isabet edildiğinde uygulamayı durdurmayın. Genellikle, bir anlık görüntü noktasında anlık görüntü yakalama 10-20 milisaniye sürer.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Snapshot Debugger başlatın
> * Anlık görüntü noktası ayarlama ve anlık görüntü görüntüleme
> * Günlüğe kaydetme noktası ayarlama

## <a name="prerequisites"></a>Önkoşullar

* Snapshot Debugger yalnızca **Azure geliştirme iş yükü** ile Visual Studio 2017 15,5 Enterprise veya üzeri sürümlerde kullanılabilir. ( **Tek tek bileşenler** sekmesinde, **hata ayıklama ve test**  >  altında bulabilirsiniz **Anlık görüntü hata ayıklayıcısı**.)

   ::: moniker range=">=vs-2019"
   henüz yüklenmemişse [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)' i yükleme. önceki bir Visual Studio yüklemesinden güncelleştiriyorsanız, Visual Studio Yükleyicisi çalıştırın ve **ASP.NET ve web geliştirme iş** yükünde Snapshot Debugger bileşenini kontrol edin.
   ::: moniker-end
   ::: moniker range="<=vs-2017"
   henüz yüklenmemişse, [2017 Enterprise sürüm 15,5](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) veya sonraki bir sürümünü Visual Studio. önceki bir Visual Studio 2017 yüklemesinden güncelleştiriyorsanız, Visual Studio Yükleyicisi çalıştırın ve **ASP.NET ve web geliştirme iş** yükünde Snapshot Debugger bileşenini kontrol edin.
   ::: moniker-end

* Temel veya daha yüksek Azure App Service planı.

* Anlık görüntü koleksiyonu, Azure App Service çalıştıran aşağıdaki Web uygulamaları için kullanılabilir:
  * .NET Framework 4.6.1 veya sonraki sürümlerde çalışan uygulamalar ASP.NET.
  * Windows ASP.NET Core .net Core 2,0 veya üzeri sürümlerde çalışan uygulamalar.

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
   > (Visual Studio 2019 sürüm 16,2 ve üstü) Snapshot Debugger Azure bulut desteğini etkinleştirdi. seçtiğiniz azure kaynağının ve azure Depolama hesabının aynı buluttan olduğundan emin olun. Kuruluşunuzun [Azure uyumluluk](https://azure.microsoft.com/overview/trusted-cloud/) yapılandırmalarına ilişkin sorularınız varsa lütfen Azure yöneticinize başvurun.
   ::: moniker-end

   Visual Studio artık anlık görüntü hata ayıklama modunda.
   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

   **modüller** penceresi, tüm modüllerin Azure App Service için ne zaman yüklendiğini gösterir (bu pencereyi açmak için **hata ayıkla > Windows > modüller** ' i seçin).

   ![Modüller penceresini denetleyin](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Anlık görüntü noktası ayarla

1. Kod Düzenleyicisi 'nde, bir anlık görüntü noktası ayarlamak için ilgilendiğiniz kod satırının yanındaki sol cilt payı tıklatın. Uygulamasının çalıştırabildiğinizi bildiğiniz kodun olduğundan emin olun.

   ![Anlık görüntü noktası ayarla](../debugger/media/snapshot-set-snappoint.png)

2. Anlık görüntü noktasını açmak için **toplamayı Başlat** ' a tıklayın.

   ![Anlık görüntü noktasını aç](../debugger/media/snapshot-start-collection.png)

   > [!TIP]
   > Bir anlık görüntüyü görüntülerken ilerleyemiyorum, ancak farklı kod satırlarındaki yürütmeyi izlemek için kodunuza birden fazla anlık görüntü koyabilirsiniz. Kodunuzda birden fazla anlık görüntü noktanız varsa Snapshot Debugger, ilgili anlık görüntülerin aynı son kullanıcı oturumundan geldiğinden emin olur. Snapshot Debugger, uygulamanıza vurarak çok sayıda kullanıcı olsa da bunu yapar.

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir anlık görüntü noktası ayarlandıktan sonra, Web sitenizin tarayıcı görünümüne gidip, işaretlenmiş kod satırını çalıştırarak veya kullanıcılarınızın site kullanımlarından bir tane oluşturması için bekleyen bir anlık görüntüyü el ile oluşturabilirsiniz.

## <a name="inspect-snapshot-data"></a>Anlık görüntü verilerini İnceleme

1. Anlık görüntü noktası isabet edildiğinde, Tanılama Araçları penceresinde bir anlık görüntü görüntülenir. bu pencereyi açmak için **hata ayıkla > Windows > Tanılama Araçları göster**' i seçin.

   ![Anlık görüntü noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Anlık görüntü noktasını kod düzenleyicisinde açmak için anlık görüntü noktasına çift tıklayın.

   ![Anlık görüntü verilerini İnceleme](../debugger/media/snapshot-inspect-data.png)

   Bu görünümden, veri Ipuçlarını görüntülemek, **Yereller**, **Izler** ve **çağrı yığını** pencerelerini kullanmak ve ayrıca Ifadeleri değerlendirmek için değişkenlerin üzerine geldiğinizde arama yapabilirsiniz.

   Web sitesinin kendisi de canlı ve son kullanıcılar etkilenmemektedir. Varsayılan olarak, anlık görüntü noktası başına yalnızca bir anlık görüntü yakalanır: bir anlık görüntü yakalandıktan sonra, anlık görüntü açılır. Anlık görüntü noktasında başka bir anlık görüntü yakalamak istiyorsanız, **koleksiyonu Güncelleştir**' e tıklayarak anlık görüntü noktasını yeniden açabilirsiniz.

Ayrıca, uygulamanıza daha fazla anlık görüntü ekleyebilir ve **koleksiyonu Güncelleştir** düğmesiyle bu noktaları açabilirsiniz.

**Yardıma mı ihtiyacınız var?** [Anlık görüntü hata ayıklama sayfaları Için](../debugger/debug-live-azure-apps-faq.yml) [sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md) ve SSS bölümüne bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu bir anlık görüntü noktası ayarlama

Uygulamanızda belirli bir durumu yeniden oluşturmayı zorlaştırıyorsa, koşullu bir anlık görüntü noktası kullanmayı düşünün. Koşullu anlık görüntü noktaları, bir değişken, incelemek istediğiniz belirli bir değeri içerdiğinde olduğu gibi, bir anlık görüntünün ne zaman ele alıp denetistemediğinizi denetlemenize yardımcı olur. İfadeleri ifade, filtre veya isabet sayısı kullanarak ayarlayabilirsiniz.

#### <a name="to-create-a-conditional-snappoint"></a>Koşullu bir anlık görüntü noktası oluşturmak için

1. bir anlık görüntü noktası simgesine (boş top) sağ tıklayın ve **Ayarlar**' yi seçin.

   ![Ayarlar'ı seçme](../debugger/media/snapshot-snappoint-settings.png)

1. Anlık görüntü noktası ayarları penceresinde bir ifade yazın.

   ![Bir ifade yazın](../debugger/media/snapshot-snappoint-conditions.png)

   Önceki çizimde, anlık görüntü yalnızca ne zaman anlık görüntü noktası için alınır `visitor.FirstName == "Dan"` .

## <a name="set-a-logpoint"></a>Günlüğe kaydetme noktası ayarlama

Anlık görüntü noktası isabet edildiğinde bir anlık görüntü almaya ek olarak, bir anlık görüntü noktasını bir iletiyi günlüğe kaydetmek için de yapılandırabilirsiniz (yani, bir logpoint oluşturun). Uygulamanızı yeniden dağıtmak zorunda kalmadan günlüğe kaydetme noktaları ayarlayabilirsiniz. Günlüğe kaydetme noktaları neredeyse yürütülür ve çalışan uygulamanız üzerinde hiçbir etkisi veya yan etkiye neden olmaz.

#### <a name="to-create-a-logpoint"></a>Günlüğe kaydetme noktası oluşturmak için

1. bir anlık görüntü noktası simgesine (mavi altıon) sağ tıklayın ve **Ayarlar**' yi seçin.

1. Anlık görüntü noktası ayarları penceresinde **Eylemler**' i seçin.

   ![Günlüğe kaydetme noktası oluşturma](../debugger/media/snapshot-logpoint.png)

1. **İleti** alanına, günlüğe kaydetmek istediğiniz yeni günlük iletisini girebilirsiniz. Ayrıca, günlük iletinizde değişkenleri küme ayraçları içine yerleştirerek değerlendirebilirsiniz.

   **Çıkış penceresi gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, tanılama araçları penceresinde görünür.

   ![Tanılama Araçları penceresindeki logpoint verileri](../debugger/media/snapshot-logpoint-output.png)

   **uygulama günlüğüne gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, `System.Diagnostics.Trace` `ILogger` [uygulama Analizler](/azure/application-insights/app-insights-asp-net-trace-logs)gibi (veya .net Core) iletileri görebileceğiniz her yerde görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, uygulama hizmetleri için Snapshot Debugger kullanmayı öğrendiniz. Bu özellik hakkında daha fazla ayrıntı okumak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)