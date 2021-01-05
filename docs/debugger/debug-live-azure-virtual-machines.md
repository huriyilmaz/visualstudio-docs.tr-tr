---
title: Live ASP.NET Azure VM ve ölçek kümelerinde hata ayıklama
description: Azure VM 'lerinde ve ölçek kümelerinde canlı ASP.NET uygulamalarında hata ayıklarken anlık görüntü alma ve anlık görüntü alma işlemlerinin nasıl yapılacağını öğrenmek için Visual Studio 'daki Snapshot Debugger nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 9ed85616080859cd69c44c66b442f3f46d81f51a
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846954"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>Snapshot Debugger kullanarak Azure sanal makinelerinde ve Azure sanal makine ölçek kümelerinde canlı ASP.NET uygulamalarında hata ayıklayın

Snapshot Debugger, çalışırken ilgilendiğiniz kod olduğunda üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya bir anlık görüntü almasını söylemek için kodunuzda anlık görüntü noktaları ve günlüğe kaydetme noktaları ayarlarsınız. Hata ayıklayıcı, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

Anlık görüntü noktaları ve günlüğe kaydetme noktaları, kesme noktalarıyla benzerdir, ancak kesme noktalarından farklı olarak, anlık görüntü noktaları, isabet edildiğinde uygulamayı durdurmayın. Genellikle, bir anlık görüntü noktasında anlık görüntü yakalama 10-20 milisaniye sürer.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Snapshot Debugger başlatın
> * Anlık görüntü noktası ayarlama ve anlık görüntü görüntüleme
> * Günlüğe kaydetme noktası ayarlama

## <a name="prerequisites"></a>Ön koşullar

* Azure sanal makineler (VM) ve Azure sanal makine ölçek kümeleri için Snapshot Debugger yalnızca **Azure geliştirme iş yüküyle** Visual Studio 2019 Enterprise veya üzeri sürümlerde kullanılabilir. ( **Tek tek bileşenler** sekmesinde, **hata ayıklama ve test**  >  altında bulabilirsiniz **Anlık görüntü hata ayıklayıcısı**.)

    Henüz yüklenmemişse, [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)'ı yükleme.

* Anlık görüntü koleksiyonu şu Azure sanal makine ölçek kümeleri Web uygulamaları için kullanılabilir:
  * .NET Framework 4.6.1 veya sonraki sürümlerde çalışan uygulamalar ASP.NET.
  * .NET Core 2,0 veya üzeri sürümlerde çalışan uygulamaları Windows üzerinde ASP.NET Core.

  > [!NOTE]
  >  32 bit Windows üzerinde çalışan Visual Studio Enterprise, anlık görüntüleri görüntüleyemez.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Projenizi açın ve Snapshot Debugger başlatın

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

    ![Anlık görüntü noktası ayarla](../debugger/media/snapshot-set-snappoint.png)

1. Anlık görüntü noktasını açmak için **toplamayı Başlat** ' a tıklayın.

    ![Anlık görüntü noktasını aç](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Bir anlık görüntüyü görüntülerken ilerleyemiyorum, ancak farklı kod satırlarındaki yürütmeyi izlemek için kodunuza birden fazla anlık görüntü koyabilirsiniz. Kodunuzda birden fazla anlık görüntü noktanız varsa Snapshot Debugger, ilgili anlık görüntülerin aynı son kullanıcı oturumundan geldiğinden emin olur. Snapshot Debugger, uygulamanıza vurarak çok sayıda kullanıcı olsa da bunu yapar.

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir anlık görüntü noktası ayarlandıktan sonra, Web sitenizin tarayıcı görünümüne gidip, işaretlenmiş kod satırını çalıştırarak veya kullanıcılarınızın site kullanımlarından bir tane oluşturması için bekleyen bir anlık görüntüyü el ile oluşturabilirsiniz.

## <a name="inspect-snapshot-data"></a>Anlık görüntü verilerini İnceleme

1. Anlık görüntü noktası isabet edildiğinde, Tanılama Araçları penceresinde bir anlık görüntü görüntülenir. Bu pencereyi açmak için **hata ayıkla > Windows > tanılama araçları göster**' i seçin.

    ![Anlık görüntü noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Anlık görüntü noktasını kod düzenleyicisinde açmak için anlık görüntü noktasına çift tıklayın.

    ![Anlık görüntü verilerini İnceleme](../debugger/media/snapshot-inspect-data.png)

    Bu görünümden, veri Ipuçlarını görüntülemek, **Yereller**, **Izler** ve **çağrı yığını** pencerelerini kullanmak ve ayrıca Ifadeleri değerlendirmek için değişkenlerin üzerine geldiğinizde arama yapabilirsiniz.

    Web sitesinin kendisi de canlı ve son kullanıcılar etkilenmemektedir. Varsayılan olarak, anlık görüntü noktası başına yalnızca bir anlık görüntü yakalanır: bir anlık görüntü yakalandıktan sonra, anlık görüntü açılır. Anlık görüntü noktasında başka bir anlık görüntü yakalamak istiyorsanız, **koleksiyonu Güncelleştir**' e tıklayarak anlık görüntü noktasını yeniden açabilirsiniz.

Ayrıca, uygulamanıza daha fazla anlık görüntü ekleyebilir ve **koleksiyonu Güncelleştir** düğmesiyle bu noktaları açabilirsiniz.

**Yardıma mı ihtiyacınız var?** [Anlık görüntü hata ayıklama sayfaları Için](../debugger/debug-live-azure-apps-faq.md) [sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md) ve SSS bölümüne bakın.

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

    ![Günlüğe kaydetme noktası oluşturma](../debugger/media/snapshot-logpoint.png)

1. **İleti** alanına, günlüğe kaydetmek istediğiniz yeni günlük iletisini girebilirsiniz. Ayrıca, günlük iletinizde değişkenleri küme ayraçları içine yerleştirerek değerlendirebilirsiniz.

    **Çıkış penceresi gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, tanılama araçları penceresinde görünür.

    ![Tanılama Araçları penceresindeki logpoint verileri](../debugger/media/snapshot-logpoint-output.png)

    **Uygulama günlüğüne gönder**' i seçerseniz, günlüğe kaydetme noktası isabet edildiğinde ileti, `System.Diagnostics.Trace` `ILogger` [uygulama öngörüleri](/azure/application-insights/app-insights-asp-net-trace-logs)gibi (veya .NET Core) iletileri görebileceğiniz her yerde görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Azure sanal makineleri ve Azure sanal makine ölçek kümeleri için Snapshot Debugger nasıl kullanacağınızı öğrendiniz. Bu özellik hakkında daha fazla ayrıntı okumak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.md)
