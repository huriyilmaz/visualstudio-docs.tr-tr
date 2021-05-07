---
title: Azure VM'de zaman ASP.NET hata ayıklama
description: Azure sanal makinelerini kullanarak canlı ASP.NET kaydetmeyi ve yeniden oynatmayı Snapshot Debugger.
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
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
ms.openlocfilehash: f8aabb109de02a1beec326407472a841fe16425a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798459"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Azure sanal makinelerde canlı ASP.NET kayıt ve yeniden oynatma Snapshot Debugger

Visual Studio Enterprise'daki Zaman Yolculuğu Hata Ayıklama (TTD) önizlemesi, Azure Sanal Makinesi (VM) üzerinde çalışan bir Web uygulamasını kaydetme ve yürütme yolunu doğru şekilde yeniden yapılandırma ve yeniden yürütme olanağı sağlar. TTD, Snapshot Debugger ile tümleştirildi ve kod satırlarını istediğiniz sayıda geri sarmanıza ve yeniden yürütmeye olanak tanıyarak yalnızca üretim ortamlarında ortaya çıkabilir sorunları yalıtmanıza ve tanımlamanıza yardımcı olur.

TTD kaydının yakalanması uygulamayı durdurmaz. Ancak TDD kaydı, işlem boyutunu ve etkin iş parçacığı sayısını içeren faktörlere göre yavaşlar ve çalışan sürecinize önemli bir yük getirir.

Bu özellik, go canlı lisansıyla Visual Studio 2019'un yayın sürümü için önizlemededir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Zaman Snapshot Debugger Hata Ayıklama etkinleştirilmiş şekilde çalışma adımlarını başlatma
> * Anlık görüntü ayarlama ve zaman yolculuğu kaydı toplama
> * Zaman yolculuğu kaydında hata ayıklamaya başlama

## <a name="prerequisites"></a>Önkoşullar

* Azure Sanal Makineler (VM) için Zaman Yolculuğu Hata Ayıklaması yalnızca Azure geliştirme iş yüküyle Visual Studio 2019 Enterprise **veya daha üst bir için kullanılabilir.** (Bağımsız **bileşenler sekmesinde** Hata ayıklama ve test altında **bulabilirsiniz**  >  **Snapshot debugger**.)

    Henüz yüklü değilse, [2019 Enterprise Visual Studio yükleyin.](https://visualstudio.microsoft.com/vs/)

* Zaman Yolculuğu Hata Ayıklaması aşağıdaki Azure VM web uygulamaları için kullanılabilir:
  * ASP.NET 4.8 veya sonraki bir .NET Framework çalışan .NET Framework uygulamaları (AMD64).

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Zaman Snapshot Debugger Hata Ayıklama etkinleştirilmiş şekilde çalışma adımlarını başlatma

1. Zaman yolculuğu kaydı toplamak için uygun projeyi açın.

    > [!IMPORTANT]
    > TTD'yi başlatmak için Azure VM *hizmetinize* yayımlanan kaynak kodun aynı sürümünü açabilirsiniz.

1. **Hata ayıkla > Snapshot Debugger Ekle...** seçeneğini belirleyin. Web uygulamanızın dağıtıldığı Azure sanal makinesini ve bir Azure Depolama hesabını seçin. **Zaman gezme hata ayıklama önizlemeyi etkinleştir** seçeneğini belirleyin ve ardından **Ekle**' ye tıklayın.

      ![Azure kaynağı seçin](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > VM 'niz için **Snapshot Debugger** ilk defa seçtiğinizde IIS otomatik olarak yeniden başlatılır.

    **Modüller** için meta veriler başlangıçta etkinleştirilmez. Web uygulamasına gidin ve **koleksiyonu Başlat** düğmesine gidip etkin hale gelir. Visual Studio artık Snapshot hata ayıklama modunda.

   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights site uzantısı anlık görüntü hata ayıklamayı da destekler. "Site uzantısı güncel değil" hata iletisiyle karşılaşırsanız, ayrıntıları yükseltmek için [sorun giderme ipuçlarına ve anlık görüntü hata ayıklaması için bilinen sorunlara](../debugger/debug-live-azure-apps-troubleshooting.md) bakın.

   **Modüller** penceresinde, tüm modüller Azure VM için yüklendiğinde görüntülenir (Bu pencereyi açmak için **Windows > modülleri hata ayıkla >** seçin).

   ![Modüller penceresini denetleyin](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Anlık görüntü noktası ayarlama ve zaman gezme kaydı toplama

1. Kod Düzenleyicisi 'nde, bir anlık görüntü noktası ayarlamak için ilgilendiğiniz bir yöntemde sol cilt paya tıklayın. Bunun yürütüleceğini bildiğiniz bir kod olduğundan emin olun.

   ![Anlık görüntü noktası ayarla](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Anlık görüntü noktası simgesine (boş top) sağ tıklayın ve **Eylemler**' i seçin. **Anlık görüntü ayarları** penceresinde, **eylem** onay kutusuna tıklayın. Daha sonra **Bu yöntemin sonuna bir zaman gezme izlemesi izleyin** onay kutusunu tıklayın.

   ![Yöntemin sonuna bir zaman gezme izlemesi toplayın](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Ek **bileşeni açmak** için Koleksiyonu Başlat'a tıklayın.

   ![Ek bileşen noktası açma](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir anlık görüntü açık olduğunda, anlık görüntü, ek bileşenin yerleştiril olduğu kod satırı yürütülürken bir anlık görüntü yakalar. Bu yürütmenin nedeni sunucunuzda gerçek bir istek olabilir. Anlık görüntü noktanızı isabete zorlamak için web sitenizin tarayıcı görünümüne gidin ve ek bileşen noktanıza isabet etmek için gereken tüm eylemleri gerçekleştirin.

## <a name="start-debugging-a-time-travel-recording"></a>Zaman yolculuğu kaydında hata ayıklamaya başlama

1. Anlık görüntü, anlık görüntüye isabet Tanılama Araçları görüntülenir. Bu pencereyi açmak için Windows **> Show > hata ayıkla'Tanılama Araçları.**

   ![Ek bileşen noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Kod düzenleyicisinde zaman yolculuğu kaydını açmak için Anlık Görüntüyü Görüntüle bağlantısına tıklayın.
  
   Devam ve Ters Devam Düğmelerini kullanarak TTD tarafından kaydedilen her kod **satırı** **yürütebilirsiniz.** Ayrıca, **Hata Ayıklama araç** çubuğu Sonraki Deyimini **Göstermek,** **Içine** Adımla **,** Adım At **,** Adım At **,** Içine Geri **Adımla,** Üzerinden Geri Adımla , Geri Adımla **için kullanılabilir.**

   ![Hata Ayıklamayı Başlat](../debugger/media/time-travel-debugging-step-commands.png)

   **Locals, Watches** ve Call Stack pencerelerini **de kullanabilir** ve ifadeleri değerlendirin.

   ![Anlık görüntü verilerini inceleme](../debugger/media/time-travel-debugging-start-debugging.png)

    Web sitesinin kendisi hala canlı ve son kullanıcılar sonraki TTD etkinliklerini etkilememektedir. Varsayılan olarak her anlık görüntüde yalnızca bir anlık görüntü yakalanır: Bir anlık görüntü yakalandikten sonra anlık görüntü kapattır. Ek bileşende başka bir anlık görüntü yakalamak için, Koleksiyonu Güncelleştir'e tıklayarak anlık görüntüyü **yeniden açabilirsiniz.**

**Yardıma mı ihtiyacınız var?** Anlık görüntü [hata ayıklama sayfaları için Sorun giderme](../debugger/debug-live-azure-apps-troubleshooting.md) ve bilinen sorunlar ve [SSS bölümüne](../debugger/debug-live-azure-apps-faq.yml) bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu ek bileşen ayarlama

Uygulamanızda belirli bir durumu yeniden oluşturmak güç alıyorsa, koşullu bir anlık görüntü noktası kullanmanın yardımcı olup olmadığını göz önünde bulundurun. Koşullu anlık görüntü noktaları, bir değişkenin incelemek istediğiniz belirli bir değere sahip olması gibi, uygulama istenen bir duruma girene kadar bir zaman seyahat kaydı toplamaktan kaçınmanıza yardımcı olur. [İfadeleri ifade, filtre veya isabet sayısı kullanarak ayarlayabilirsiniz](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Azure sanal makineleri için zaman gezme kaydını nasıl toplayacağınızı öğrendiniz. Snapshot Debugger hakkında daha fazla ayrıntı okumak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)