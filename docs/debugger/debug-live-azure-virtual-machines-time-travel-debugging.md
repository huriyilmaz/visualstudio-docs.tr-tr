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
ms.openlocfilehash: 01dc29827f87f845d8c9e3fc4d72bedf68fe692b7f96e9dab07a73266f961a42
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121344254"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>Azure sanal makinelerde ASP.NET canlı kayıt ve yeniden oynatma Snapshot Debugger

Visual Studio Enterprise'daki Zaman Yolculuğu Hata Ayıklama (TTD) önizlemesi, Azure Sanal Makinesi (VM) üzerinde çalışan bir Web uygulamasını kaydetme ve yürütme yolunu doğru şekilde yeniden yapılandırma ve yeniden yürütme olanağı sağlar. TTD, Snapshot Debugger ile tümleştirildi ve kod satırlarını istediğiniz sayıda geri sarmanıza ve yeniden yürütmeye olanak tanıyarak yalnızca üretim ortamlarında ortaya çıkabilir sorunları yalıtmanıza ve tanımlamanıza yardımcı olur.

TTD kaydının yakalanması uygulamayı durdurmaz. Ancak TDD kaydı, işlem boyutunu ve etkin iş parçacığı sayısını içeren faktörlere bağlı olarak işlemi yavaşlatarak çalışan sürecinize önemli bir yük getirir.

Bu özellik, go canlı lisansıyla Visual Studio 2019'un yayın sürümü için önizlemededir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Zaman Snapshot Debugger Hata Ayıklama etkinleştirilmiş şekilde çalışma adımlarını başlatma
> * Anlık görüntü ayarlama ve zaman yolculuğu kaydı toplama
> * Zaman yolculuğu kaydında hata ayıklamaya başlama

## <a name="prerequisites"></a>Önkoşullar

* Azure Sanal Makineler (VM) için Zaman Yolculuğu Hata Ayıklaması yalnızca Azure geliştirme iş yükü Visual Studio 2019 Enterprise veya **daha yüksek bir süre için kullanılabilir.** (Bağımsız **bileşenler sekmesinde** Hata ayıklama ve test altında **bulabilirsiniz**  >  **Snapshot debugger**.)

    Henüz yüklü değilse, [2019'Visual Studio yükleyin Enterprise.](https://visualstudio.microsoft.com/vs/)

* Zaman Yolculuğu Hata Ayıklaması aşağıdaki Azure VM web uygulamaları için kullanılabilir:
  * ASP.NET 4.8 veya sonraki bir .NET Framework çalışan uygulamalar (AMD64).

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>Zaman Snapshot Debugger Hata Ayıklama etkinleştirilmiş şekilde çalışma adımlarını başlatma

1. Zaman yolculuğu kaydı toplamak için uygun projeyi açın.

    > [!IMPORTANT]
    > TTD'yi başlatmak için Azure VM *hizmetinize* yayımlanan kaynak kodun aynı sürümünü açabilirsiniz.

1. Hata **Ayıkla ve > Ekle... Snapshot Debugger seçin.** Web uygulamasının dağıtılacağı Azure VM'sini ve bir Azure depolama hesabını seçin. Zaman Yolculuğu **Hata Ayıklama önizlemesini etkinleştir seçeneğini** belirleyin ve Ekle'ye **tıklayın.**

      ![Azure Kaynağı'ı seçin](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > VM'niz için **Bir Snapshot Debugger'ı** ilk kez seçerek IIS otomatik olarak yeniden başlatılır.

    Modüller için **meta veriler** başlangıçta etkinleştirilmez. Web uygulamasına gidin ve Koleksiyonu **Başlat düğmesi** etkin hale gelir. Visual Studio artık anlık görüntü hata ayıklama modunda.

   ![Anlık görüntü hata ayıklama modu](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Analizler site uzantısı, Anlık Görüntü Hata Ayıklamayı da destekler. "Site uzantısı güncel değil" hata iletisiyle karşılaşırsanız, ayrıntıları yükseltmek için bkz. Anlık görüntü hata ayıklama ile ilgili [sorunları](../debugger/debug-live-azure-apps-troubleshooting.md) giderme ipuçları ve bilinen sorunlar.

   Modüller **penceresinde,** Azure VM için tüm modüller yüklendiğinde gösterilir (bu pencereyi açmak için Modüllerde **hata > Windows >'yi** seçin).

   ![Modüller penceresini denetleme](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>Anlık görüntü ayarlama ve zaman yolculuğu kaydı toplama

1. Kod düzenleyicisinde, bir ek bileşen ayarlamak için ilgilendiğiniz yöntemin sol olukluna tıklayın. Yürütülecek kod olduğundan emin olun.

   ![Ek bileşen ayarlama](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. Anlık görüntü simgesine (boş top) sağ tıklayın ve Eylemler'i **seçin.** Anlık görüntü **Ayarlar** Eylem onay **kutusuna** tıklayın. Ardından Bu **yöntemin sonuna kadar zaman yolculuğu izlemesi topla onay kutusuna** tıklayın.

   ![Yöntemin sonuna kadar bir zaman yolculuğu izlemesi toplama](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. Ek **bileşeni açmak** için Koleksiyonu Başlat'a tıklayın.

   ![Ek bileşen noktası açma](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>Anlık görüntü alma

Bir anlık görüntü açık olduğunda, anlık görüntü, ek bileşenin yerleştiril olduğu kod satırı yürütülürken bir anlık görüntü yakalar. Bu yürütmenin nedeni sunucunuzda gerçek bir istek olabilir. Anlık görüntü noktanızı isabete zorlamak için web sitenizin tarayıcı görünümüne gidin ve ek bileşen noktanıza isabet etmek için gereken tüm eylemleri gerçekleştirin.

## <a name="start-debugging-a-time-travel-recording"></a>Zaman yolculuğu kaydında hata ayıklamaya başlama

1. Anlık görüntü, anlık görüntüye isabet Tanılama Araçları görüntülenir. Bu pencereyi açmak için Hata **ayıkla'> Windows > Show Tanılama Araçları**.

   ![Ek bileşen noktası açma](../debugger/media/snapshot-diagsession-window.png)

1. Kod düzenleyicisinde zaman yolculuğu kaydını açmak için Anlık Görüntüyü Görüntüle bağlantısına tıklayın.
  
   Devam ve Ters Devam Düğmelerini kullanarak TTD tarafından kaydedilen her kod satırı **yürütebilirsiniz.**  Ayrıca, **Hata Ayıklama araç** çubuğu Sonraki Deyimini **Göstermek,** **Içine** Adımla **,** Adım At **,** Adım At **,** Içine Geri **Adımla,** Üzerinden Geri Adımla , Geri Adımla **için kullanılabilir.**

   ![Hata Ayıklamayı Başlat](../debugger/media/time-travel-debugging-step-commands.png)

   **Locals, Watches** ve Call Stack pencerelerini **de kullanabilir** ve ifadeleri değerlendirin.

   ![Anlık görüntü verilerini inceleme](../debugger/media/time-travel-debugging-start-debugging.png)

    Web sitesinin kendisi hala canlıdır ve son kullanıcılar sonraki TTD etkinliklerini etkilememektedir. Varsayılan olarak her anlık görüntüde yalnızca bir anlık görüntü yakalanır: Bir anlık görüntü yakalandikten sonra anlık görüntü kapattır. Ek bileşende başka bir anlık görüntü yakalamak için, Koleksiyonu Güncelleştir'e tıklayarak anlık görüntüyü **yeniden açabilirsiniz.**

**Yardıma mı ihtiyacınız var?** Anlık görüntü [hata ayıklama sayfaları için Sorun giderme](../debugger/debug-live-azure-apps-troubleshooting.md) ve bilinen sorunlar ve [SSS bölümüne](../debugger/debug-live-azure-apps-faq.yml) bakın.

## <a name="set-a-conditional-snappoint"></a>Koşullu ek bileşen ayarlama

Uygulamanıza belirli bir durumu yeniden oluşturmak zorsa, koşullu ek bileşen kullanımının yardımcı olup olmadığını göz önünde bulundurabilirsiniz. Koşullu ek bileşen, uygulama istenen durumu girene (örneğin, bir değişkenin incelemek istediğiniz belirli bir değere sahip olduğu durumlarda) bir zaman yolculuğu kaydı toplamadan kaçınmanıza yardımcı olur. [İfadeleri, filtreleri veya isabet sayılarını kullanarak koşulları ayarlayabilirsiniz.](../debugger/debug-live-azure-apps-troubleshooting.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Azure Sanal Makineler için zaman yolculuğu kaydı toplamayı öğrendiniz. Aşağıdakiler hakkında daha fazla bilgi Snapshot Debugger.

> [!div class="nextstepaction"]
> [Anlık görüntü hatalarını ayıklama hakkında SSS](../debugger/debug-live-azure-apps-faq.yml)