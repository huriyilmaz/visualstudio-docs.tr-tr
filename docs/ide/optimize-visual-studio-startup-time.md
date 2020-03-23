---
title: Başlatma süresini iyileştirme
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 4824939b4ef3ed1bc7fa48b2508fc891c984a3c5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301869"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio başlangıç süresini optimize edin

Visual Studio mümkün olduğunca hızlı ve verimli bir şekilde başlamak için tasarlanmıştır. Ancak, bazı Visual Studio uzantıları ve araç pencereleri yüklendiklerinde başlangıç süresini olumsuz etkileyebilir. **Görsel Stüdyo Performansını Yönet** iletişim kutusunda yavaş uzantıların ve araç pencerelerinin davranışını denetleyebilirsiniz. Performansı artırmaya ilişkin daha genel ipuçları için [Visual Studio performans ipuçlarıve püf noktalarına](../ide/visual-studio-performance-tips-and-tricks.md)bakın.

## <a name="startup-behavior"></a>Başlangıç davranışı

Visual Studio, başlangıç süresini uzatmayı önlemek _için, isteğe bağlı_ bir yaklaşım kullanarak uzantıları yükler. Bu davranış, uzantıların Visual Studio başladıktan hemen sonra değil, gerektiği gibi açılmıyor anlamına gelir. Ayrıca, önceki Visual Studio oturumunda açık bırakılan araç pencereleri başlangıç süresini yavaşlatabildiği için Visual Studio, başlangıç süresini etkilemeyi önlemek için araç pencerelerini daha akıllı bir şekilde açar.

Visual Studio yavaş başlatma algılarsa, yavaşlamaya neden olan uzantı veya araç penceresi hakkında sizi uyaran bir açılır ileti görüntülenir. İleti, Görsel Stüdyo **Performansını Yönet** iletişim kutusuna bir bağlantı sağlar. Bu iletişim kutusuna menü çubuğundan**Görsel Stüdyo Performansını Yönetmene** **Yardım'ı** > seçerek de erişebilirsiniz.

![Görsel Stüdyo Performansı yönetin - pop-up okuma 'Biz bu uzantısı fark ettik ... Visual Studio'nun yavaşlaması](../ide/media/vside_perfdialog_popup.png)

İletişim kutusu, başlangıç performansını etkileyen uzantıları ve araçlar pencerelerini listeler. Başlatma performansını artırmak için uzantı ve araç penceresi ayarlarını değiştirebilirsiniz.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Başlatmayı, çözüm yükünü ve yazma performansını iyileştirmek için uzantı ayarlarını değiştirmek için

1. Menü çubuğundan Görsel Stüdyo Performansını **Yönet'e Yardım'ı** > **Manage Visual Studio Performance** seçerek **Görsel Stüdyo Performansını Yönet** iletişim kutusunu açın.

    Bir uzantı Visual Studio'nun başlatılmasını, çözüm yüklemesini veya yazılmasıyavaşlıyorsa, **uzantı, Uzantılar** > **Başlangıç** (veya **Çözüm Yükleme** veya **Yazma)** altındaki **Görsel Stüdyo Performansını Yönet** iletişim kutusunda görünür.

    ![Visual Studio performansını yönet - uzantıgörünümü](../ide/media/vside_perfdialog_extensions.png)

2. Devre dışı kalmak istediğiniz uzantıyı seçin ve ardından **Devre Dışı Devre düğmesini** seçin.

**Uzantı Yöneticisi'ni** veya **Görsel Stüdyo Performansını Yönet** iletişim kutusunu kullanarak uzantıyı gelecek oturumlar için her zaman yeniden etkinleştirebilirsiniz.

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Başlangıç süresini iyileştirmek için araç penceresi ayarlarını değiştirmek için

1. Menü çubuğundan Görsel Stüdyo Performansını **Yönet'e Yardım'ı** > **Manage Visual Studio Performance** seçerek **Görsel Stüdyo Performansını Yönet** iletişim kutusunu açın.

    Bir araç penceresi Visual Studio'nun başlatılmasını yavaşlatıyorsa, araç penceresi **Araç Windows** > **Başlangıç**altında Visual **Studio Performance'ı Yönet** iletişim kutusunda görünür.

2. Davranışı değiştirmek istediğiniz araç penceresini seçin.

3. Aşağıdaki üç seçenekten birini seçin:

   - **Varsayılan davranışı kullanma:** Araç penceresi için varsayılan davranış. Bu seçeneğin seçili tutulması başlangıç performansını artırmaz.

   - **Başlangıçta pencereyi göstermeyin:** Belirtilen araç penceresi, önceki bir oturumda açık bıraksanız bile Visual Studio'yu açtığınızda her zaman kapalıdır. İhtiyacınız olduğunda araç penceresini uygun menüden açabilirsiniz.

   - **Başlangıçta otomatik gizleme penceresi:** Bir önceki oturumda bir araç penceresi açık bırakılmışsa, bu seçenek, araç penceresinin başlatılmasını önlemek için başlangıçta araç penceresinin grubunu daraltır. Bir araç penceresi sık sık kullanıyorsanız, bu seçenek iyi bir seçimdir. Araç penceresi hala kullanılabilir, ancak artık Visual Studio başlangıç süresini olumsuz etkilemez.

     ![Visual Studio performansını yönet - araç windows görünümü](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Visual Studio 2017'nin önceki bazı sürümlerinde **hafif çözüm yükü**adı verilen bir özellik vardı. Geçerli sürümlerde, yönetilen kod yükünü içeren büyük çözümler, hafif çözüm yükü olmasa bile öncekinden çok daha hızlı yüklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Visual Studio 2017 sürümü 15.6 ile çözümleri daha hızlı yükleyin](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
