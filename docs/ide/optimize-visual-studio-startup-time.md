---
title: Başlangıç zamanını geliştirme
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 84f91b9fd6338698f3ffa918ff34011ac3d3acb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666022"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio başlangıç zamanını iyileştirin

Visual Studio, mümkün olduğunca hızlı ve etkili bir şekilde başlamak için tasarlanmıştır. Ancak, belirli Visual Studio uzantıları ve araç pencereleri, yüklendiklerinde başlangıç süresini olumsuz etkileyebilir. Yavaş uzantıların ve araç pencerelerinin davranışını **Visual Studio performansını Yönet** iletişim kutusunda kontrol edebilirsiniz. Performansı iyileştirme hakkında daha fazla genel ipucu için bkz. [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Başlangıç davranışı

Başlangıç süresini genişletmemek için, Visual Studio _isteğe bağlı_ bir yaklaşım kullanarak uzantıları yükler. Bu davranış, uzantıların Visual Studio başladıktan hemen sonra açılmayacağı, ancak gerekli olduğu anlamına gelir. Ayrıca, önceki bir Visual Studio oturumunda açık olan araç pencereleri başlangıç süresini yavaşlatabileceğinden, Visual Studio başlangıç süresini etkilememek için araç pencerelerini daha akıllı bir şekilde açar.

Visual Studio yavaş başlangıç algılarsa, yavaşlamaya neden olan uzantı veya araç penceresine uyarı veren bir açılır ileti görüntülenir. İleti, **Visual Studio performansını Yönet** iletişim kutusu için bir bağlantı sağlar. Bu iletişim kutusuna, menü çubuğundan **yardım**  > **Visual Studio performansını Yönet** ' i seçerek de erişebilirsiniz.

![Visual Studio performansı-açılan menü okumayı yönetme ' uzantısının olduğunu belirledik... Visual Studio 'Yu yavaşlayor '](../ide/media/vside_perfdialog_popup.png)

İletişim kutusu, başlangıç performansını etkileyen Uzantılar ve araçlar pencerelerini listeler. Başlangıç performansını artırmak için uzantı ve araç penceresi ayarlarını değiştirebilirsiniz.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />To başlatma, çözüm yükleme ve yazma performansını geliştirmek için uzantı ayarlarını değiştirin

1. Menü çubuğundan **yardım**  > **Visual Studio performansını Yönet** ' i seçerek **Visual Studio performansını Yönet** iletişim kutusunu açın.

    Bir uzantı Visual Studio başlatma, çözüm yükleme veya yazma için yavaşanıyorsa, **uzantı  > ** **Başlangıç** (veya **Çözüm yükü** **) altındaki Visual Studio performansını Yönet iletişim kutusunda görünür. Yazma**).

    ![Visual Studio performansı-uzantıları görünümünü yönetme](../ide/media/vside_perfdialog_extensions.png)

2. Devre dışı bırakmak istediğiniz uzantıyı seçin ve **devre dışı bırak** düğmesini seçin.

Uzantı **Yöneticisi** veya **Visual Studio performansını Yönet** iletişim kutusunu kullanarak, gelecekteki oturumların uzantısını her zaman yeniden etkinleştirebilirsiniz.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a>başlatma süresini artırmak için araç penceresi ayarlarını değiştirin <a name="tool-windows" />To

1. Menü çubuğundan **yardım**  > **Visual Studio performansını Yönet** ' i seçerek **Visual Studio performansını Yönet** iletişim kutusunu açın.

    Bir araç penceresi Visual Studio başlangıcını yavaşlayorsa araç penceresi, **araç Windows**  > **başlatma**altındaki **Visual Studio performansını Yönet** iletişim kutusunda görünür.

2. Davranışını değiştirmek istediğiniz araç penceresini seçin.

3. Aşağıdaki üç seçenekten birini belirleyin:

   - **Varsayılan davranışı kullan:** Araç penceresi için varsayılan davranış. Bu seçeneğin seçili tutulması, başlangıç performansını iyileştirmeyecektir.

   - **Başlangıçta pencere gösterme:** Belirtilen araç penceresi, önceki bir oturumda açık bıraktığınız halde, Visual Studio 'Yu açtığınızda her zaman kapalıdır. Araç penceresini, ihtiyacınız olduğunda uygun menüden açabilirsiniz.

   - **Başlangıçta pencereyi otomatik gizle:** Bir araç penceresi önceki bir oturumda açık bırakılmış ise, bu seçenek araç penceresinin başlatılmasını önlemek için başlangıçta araç penceresinin grubunu daraltır. Bu seçenek, genellikle bir araç penceresi kullanıyorsanız iyi bir seçenektir. Araç penceresi hala kullanılabilir, ancak artık Visual Studio başlangıç zamanını olumsuz şekilde etkilemesiz.

     ![Visual Studio performansı yönetme-araç Windows görünümü](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Visual Studio 2017 ' nin bazı önceki sürümlerinde **basit çözüm yükü**adlı bir özellik vardı. Geçerli sürümlerde, basit çözüm yükü olmadan bile, yönetilen kod yükünü içeren büyük çözümler daha önceden daha hızlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirin](../ide/optimize-visual-studio-performance.md)
- [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blogu-Visual Studio 2017 sürüm 15,6 ile çözümleri daha hızlı yükleme](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)