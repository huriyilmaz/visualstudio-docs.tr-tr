---
title: Azure VM ve ASP.NET kümelerde canlı hata ayıklama
description: Azure VM'leri Snapshot Debugger ölçek Visual Studio ASP.NET canlı uygulamalarda hata ayıklarken anlık görüntü almak için Snapshot Debugger'ni nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/06/2019
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
ms.openlocfilehash: bdab6b3f559628506dd301d6ced449f1e69152a6
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798498"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Azure sanal ASP.NET ve Azure sanal makine ölçek kümelerini kullanarak canlı uygulama hata ayıklaması Snapshot Debugger

Bu Snapshot Debugger, ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

Anlık bileşen ve günlük noktaları kesme noktalarına benzer, ancak kesme noktanın aksine, anlık ek nokta isabetli olduğunda uygulamayı durdurmaz. Genellikle anlık görüntüyü bir anlık görüntüde yakalama 10-20 milisaniye sürer.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Start the Snapshot Debugger
> * Anlık görüntü ayarlama ve anlık görüntüyü görüntüleme
> * Günlük noktası ayarlama

## <a name="prerequisites"></a>Önkoşullar

* Snapshot Debugger Sanal Makineler (VM) ve Azure Sanal Makine Ölçek Kümeleri için azure geliştirme iş yükü ile yalnızca Visual Studio 2019 Enterprise veya daha yeni bir şirket **için kullanılabilir.** (Bağımsız **bileşenler sekmesinde** Hata ayıklama ve test altında **bulabilirsiniz**  >  **Snapshot debugger**.)

    Henüz yüklü değilse, [2019 Enterprise Visual Studio yükleyin.](https://visualstudio.microsoft.com/vs/)

* Anlık görüntü koleksiyonu aşağıdaki Azure Sanal Makineler\Sanal Makine Ölçek Kümeleri web uygulamaları için kullanılabilir:
  * ASP.NET 4.6.1 veya .NET Framework üzerinde çalışan uygulamalar.
  * ASP.NET.NET Core 2.0 veya sonraki bir sürümü üzerinde çalışan ASP.NET Core uygulamaları.

  > [!NOTE]
  >  Visual Studio Enterprise 32 bit Windows üzerinde çalışan sanal makinelerde anlık görüntüleri görüntüleyemzin.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Projenizi açın ve Snapshot Debugger

1. Anlık görüntü hata ayıklaması yapmak istediğiniz projeyi açın.

    > [!IMPORTANT]
    > Hata ayıklamanın anlık görüntüsünü almak için Azure sanal makine ölçek kümesi hizmetinizde yayınlanan *kaynak kodu sürümünü* açmanız gerekir.

1. **Hata ayıkla > Snapshot Debugger Ekle...** seçeneğini belirleyin. Web uygulamanızın dağıtıldığı Azure sanal makinesanal makine ölçek kümesini ve bir Azure Depolama hesabını seçin ve ardından **Ekle**' ye tıklayın. Snapshot Debugger Ayrıca [Azure Kubernetes hizmetini](debug-live-azure-kubernetes.md) ve [Azure App Service](debug-live-azure-applications.md)destekler.

    ![Hata ayıklama menüsünden Snapshot Debugger 'ı başlatın](../debugger/media/snapshot-debug-menu-attach.png)

    ![Azure kaynağı seçin](../debugger/media/snapshot-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > VM 'niz için **Snapshot Debugger** ilk defa seçtiğinizde IIS otomatik olarak yeniden başlatılır.
    > Sanal makine ölçek kümeleriniz için Snapshot Debugger ilk kez **Ekle** ' yi seçtiğinizde, sanal makine ölçek kümelerinin her bir örneğinin el ile yükseltilmesi gerekir.

    > [!NOTE]
    > (Visual Studio 2019 sürüm 16,2 ve üstü) Snapshot Debugger Azure bulut desteğini etkinleştirdi. Seçtiğiniz Azure kaynağının ve Azure depolama hesabının aynı buluttan olduğundan emin olun. Kuruluşunuzun [Azure uyumluluk](https://azure.microsoft.com/overview/trusted-cloud/) yapılandırmalarına ilişkin sorularınız varsa lütfen Azure yöneticinize başvurun.

    **Modüller** için meta veriler başlangıçta etkinleştirilmeyecektir, Web uygulamasına gidin ve **koleksiyonu Başlat** düğmesi etkin olur. Visual Studio artık Snapshot hata ayıklama modunda.

    ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > VMSS için, ilk kez Snapshot Debugger iliştirdikten sonra kullanıcının sanal makine ölçek kümelerinde örnekleri el ile yükseltmesi gerekir.

    **Modüller** penceresi, tüm modüllerin Azure sanal Makinesanal makine ölçek kümesi için ne zaman yüklendiğini gösterir (Bu pencereyi açmak için **Windows > modüllerini hata ayıkla >** seçin).

    ![Modüller penceresini denetleyin](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Anlık görüntü noktası ayarla

1. Kod Düzenleyicisi 'nde, bir anlık görüntü noktası ayarlamak için ilgilendiğiniz kod satırının yanındaki sol cilt payı tıklatın. Uygulamasının çalıştırabildiğinizi bildiğiniz kodun olduğundan emin olun.

    ![Ek bileşen ayarlama](../debugger/media/snapshot-set-snappoint.png)

1. Ek **bileşeni açmak** için Koleksiyonu Başlat'a tıklayın.

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

    Web sitesinin kendisi hala canlı ve son kullanıcılar bundan etkilenmez. Varsayılan olarak her anlık görüntüde yalnızca bir anlık görüntü yakalanır: Bir anlık görüntü yakalandikten sonra anlık görüntü kapattır. Ek bileşende başka bir anlık görüntü yakalamak için, Koleksiyonu Güncelleştir'e tıklayarak anlık görüntüyü **yeniden açabilirsiniz.**

Ayrıca, uygulamanıza daha fazla ek bileşen ekleyebilir ve Koleksiyonu Güncelleştir düğmesiyle **bunları açabilirsiniz.**

**Yardıma mı ihtiyacınız var?** Anlık görüntü [hata ayıklama sayfaları için Sorun giderme](../debugger/debug-live-azure-apps-troubleshooting.md) ve bilinen sorunlar ve [SSS bölümüne](../debugger/debug-live-azure-apps-faq.yml) bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu ek bileşen ayarlama

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

    ![Günlüğe kaydetme noktası oluşturma](../debugger/media/snapshot-logpoint.png)

1. **İleti** alanına, günlüğe kaydetmek istediğiniz yeni günlük iletisini girebilirsiniz. Ayrıca, günlük iletinizde değişkenleri küme ayraçları içine yerleştirerek değerlendirebilirsiniz.

    **Çıkış penceresi gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, tanılama araçları penceresinde görünür.

    ![Tanılama Araçları penceresindeki logpoint verileri](../debugger/media/snapshot-logpoint-output.png)

    Uygulama günlüğüne **gönder'i** seçerseniz, günlüğe kaydedilirse, ileti App Insights gibi `System.Diagnostics.Trace` (veya `ILogger` .NET Core'da) iletileri gördüğünüz her yerde [görüntülenir.](/azure/application-insights/app-insights-asp-net-trace-logs)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Azure Sanal Makineler ve Azure Sanal Snapshot Debugger Kümeleri için azure sanal makine ölçek kümelerini kullanmayı öğrendinsiniz. Bu özellik hakkında daha fazla ayrıntıyı okumak istiyor olabilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)
