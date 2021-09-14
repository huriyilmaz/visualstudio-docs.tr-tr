---
title: Azure sanal makinesinde canlı ASP.NET zaman gezme hatası
description: Snapshot Debugger kullanarak Azure sanal makinelerinde canlı ASP.NET uygulamalarını kaydetme ve yeniden oynatma hakkında bilgi edinin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626558"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Snapshot Debugger kullanarak Azure sanal makinelerinde canlı ASP.NET uygulamalarını kaydedin ve yeniden yürütün

Visual Studio Enterprise seyahat hata ayıklaması (ttd) önizlemesi, Azure sanal makinesinde (VM) çalışan bir Web uygulamasını kaydetme ve ardından yürütme yolunu doğru şekilde yeniden oluşturma ve yeniden yürütme özelliği sağlar. TTD, Snapshot Debugger ile tümleşir ve her bir kod satırını dilediğiniz sayıda geri sararak yeniden oynamanıza ve yalnızca üretim ortamlarında oluşabilecek sorunları ayırmanıza ve belirlemenize yardımcı olur.

Bir TTD kaydının yakalanması, uygulamayı durdurmayacak. Ancak, TDD kaydı, çalışan sürecinizi önemli ölçüde artırır, işlem boyutunu ve etkin iş parçacıklarının sayısını içeren faktörlere bağlı olarak yavaşlatmayı yavaşlatır.

bu özellik, bir go canlı lisansıyla Visual Studio 2019 sürümünün önizlemesine yönelik önizlemededir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Snapshot Debugger seyahat hata ayıklaması etkinken başlatın
> * Anlık görüntü noktası ayarlama ve zaman gezme kaydı toplama
> * Zaman gezme kaydında hata ayıklamayı Başlat

## <a name="prerequisites"></a>Önkoşullar

* azure sanal makineler (VM) için zaman gezme hata ayıklaması yalnızca **azure geliştirme iş yükü** ile Visual Studio 2019 Enterprise veya daha yüksek bir sürümü için kullanılabilir. ( **Tek tek bileşenler** sekmesinde, **hata ayıklama ve test**  >  altında bulabilirsiniz **Anlık görüntü hata ayıklayıcısı**.)

    henüz yüklenmemişse [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)' yi yükleme.

* Zaman gezme hata ayıklaması aşağıdaki Azure VM Web uygulamaları için kullanılabilir:
  * .NET Framework 4,8 veya sonraki sürümlerde çalışan ASP.NET uygulamalar (AMD64).

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Snapshot Debugger seyahat hata ayıklaması etkinken başlatın

1. Zaman gezisi kaydı toplamak istediğiniz projeyi açın.

    > [!IMPORTANT]
    > TTD 'yi başlatmak için, Azure VM hizmetinize yayınlanan *kaynak kodu sürümünü* açmanız gerekir.

1. **Hata ayıkla > Snapshot Debugger Ekle...** seçeneğini belirleyin. Web uygulamanızın dağıtıldığı Azure sanal makinesini ve bir Azure Depolama hesabını seçin. **Zaman gezme hata ayıklama önizlemeyi etkinleştir** seçeneğini belirleyin ve ardından **Ekle**' ye tıklayın.

      ![Azure kaynağı seçin](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > VM 'niz için **Snapshot Debugger** ilk defa seçtiğinizde IIS otomatik olarak yeniden başlatılır.

    **Modüller** için meta veriler başlangıçta etkinleştirilmez. Web uygulamasına gidin ve **koleksiyonu Başlat** düğmesine gidip etkin hale gelir. Visual Studio artık anlık görüntü hata ayıklama modunda.

   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights site uzantısı anlık görüntü hata ayıklamayı da destekler. "Site uzantısı güncel değil" hata iletisiyle karşılaşırsanız, ayrıntıları yükseltmek için [sorun giderme ipuçlarına ve anlık görüntü hata ayıklaması için bilinen sorunlara](../debugger/debug-live-azure-apps-troubleshooting.md) bakın.

   **modüller** penceresinde, tüm modüller Azure VM için yüklendiğinde görüntülenir (bu pencereyi açmak için **hata ayıkla > Windows > modüller** ' i seçin).

   ![Modüller penceresini denetleyin](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Anlık görüntü noktası ayarlama ve zaman gezme kaydı toplama

1. Kod Düzenleyicisi 'nde, bir anlık görüntü noktası ayarlamak için ilgilendiğiniz bir yöntemde sol cilt paya tıklayın. Bunun yürütüleceğini bildiğiniz bir kod olduğundan emin olun.

   ![Anlık görüntü noktası ayarla](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Anlık görüntü noktası simgesine (boş top) sağ tıklayın ve **Eylemler**' i seçin. **anlık görüntü Ayarlar** penceresinde **eylem** onay kutusuna tıklayın. Daha sonra **Bu yöntemin sonuna bir zaman gezme izlemesi izleyin** onay kutusunu tıklayın.

   ![Yöntemin sonuna bir zaman gezme izlemesi toplayın](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Anlık görüntü noktasını açmak için **toplamayı Başlat** ' a tıklayın.

   ![Anlık görüntü noktasını aç](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir anlık görüntü noktası açık olduğunda, her bir kod satırı, her ne zaman Bu yürütmeye, sunucunuzdaki gerçek bir istek neden olmuş olabilir. Anlık görüntü noktanızı vurmaya zorlamak için Web sitenizin tarayıcı görünümüne gidin ve anlık görüntü noktanızda vuruş yapılmasına neden olan tüm eylemleri gerçekleştirin.

## <a name="start-debugging-a-time-travel-recording"></a>Zaman gezme kaydında hata ayıklamayı Başlat

1. Anlık görüntü noktası isabet edildiğinde, Tanılama Araçları penceresinde bir anlık görüntü görüntülenir. bu pencereyi açmak için **hata ayıkla > Windows > Tanılama Araçları göster**' i seçin.

   ![Anlık görüntü noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Kod düzenleyicisinde zaman gezme kaydını açmak için anlık görüntüyü görüntüle bağlantısına tıklayın.
  
   **Devam et** ve **geri kaydet** düğmelerini kullanarak TTD tarafından kaydedilen her kod satırını çalıştırabilirsiniz. Ayrıca, **hata ayıklama** araç çubuğu bir **sonraki Ifadeyi göstermek**, **içine** geçmek, **baştan adımla**, Step **Out**, Step **into**, geri dönme, **geri dönme**, geri dönme, adım geri **alma** için de kullanılabilir.

   ![Hata ayıklamayı Başlat](../debugger/media/time-travel-debugging-step-commands.png)

   **Yereller**, **Izler** ve **çağrı yığını** pencerelerini de kullanabilir ve ayrıca ifadeleri de değerlendirebilirsiniz.

   ![Anlık görüntü verilerini İnceleme](../debugger/media/time-travel-debugging-start-debugging.png)

    Web sitesinin kendisi de canlı ve son kullanıcılar bundan sonraki bir TTD etkinliği tarafından etkilenmemektedir. Varsayılan olarak, anlık görüntü noktası başına yalnızca bir anlık görüntü yakalanır: bir anlık görüntü yakalandıktan sonra, anlık görüntü açılır. Anlık görüntü noktasında başka bir anlık görüntü yakalamak istiyorsanız, **koleksiyonu Güncelleştir**' e tıklayarak anlık görüntü noktasını yeniden açabilirsiniz.

**Yardıma mı ihtiyacınız var?** [Anlık görüntü hata ayıklama sayfaları Için](../debugger/debug-live-azure-apps-faq.yml) [sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md) ve SSS bölümüne bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu bir anlık görüntü noktası ayarlama

Uygulamanızda belirli bir durumu yeniden oluşturmak güç alıyorsa, koşullu bir anlık görüntü noktası kullanmanın yardımcı olup olmadığını göz önünde bulundurun. Koşullu anlık görüntü noktaları, bir değişkenin incelemek istediğiniz belirli bir değere sahip olması gibi, uygulama istenen bir duruma girene kadar bir zaman seyahat kaydı toplamaktan kaçınmanıza yardımcı olur. [İfadeleri ifade, filtre veya isabet sayısı kullanarak ayarlayabilirsiniz](../debugger/debug-live-azure-apps-troubleshooting.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Azure sanal makineleri için zaman gezme kaydını nasıl toplayacağınızı öğrendiniz. Snapshot Debugger hakkında daha fazla ayrıntı okumak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)