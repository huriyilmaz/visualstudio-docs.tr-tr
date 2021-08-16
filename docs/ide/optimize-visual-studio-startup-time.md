---
title: Başlangıç zamanını geliştirme
description: Visual Studio performansını yönet iletişim kutusunda uzantıları ve araç pencerelerinin ayarlarını Visual Studio başlangıç zamanını geliştirmek için nasıl denetleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/15/2017
ms.topic: how-to
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: cc13571011e7d4d50cb8643d14afe559c11caacdf4b4bb67ea24354eae477bea
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412880"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio başlangıç zamanını iyileştirin

Visual Studio, mümkün olduğunca hızlı ve verimli bir şekilde başlamak için tasarlanmıştır. ancak, bazı Visual Studio uzantıları ve araç pencereleri, yüklendiklerinde başlangıç süresini olumsuz etkileyebilir. **Visual Studio performansını yönet** iletişim kutusunda yavaş uzantıların ve araç pencerelerinin davranışını kontrol edebilirsiniz. performansı iyileştirme hakkında daha fazla genel ipucu için bkz. [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Başlangıç davranışı

başlangıç süresini genişletmemek için Visual Studio, _isteğe bağlı_ bir yaklaşım kullanarak uzantıları yükler. bu davranış, uzantıların Visual Studio başladıktan hemen sonra açılmayacağı, ancak gerekli olan bir temeldir. ayrıca, önceki bir Visual Studio oturumunda açık olan araç pencereleri başlangıç süresini yavaşlatabileceğinden, Visual Studio başlangıç süresini etkilememek için araç pencerelerini daha akıllı bir şekilde açar.

Visual Studio yavaş başlangıç algılarsa, bir açılır ileti görünür ve yavaşlamaya neden olan uzantı veya araç penceresinde sizi uyarır. ileti, **Visual Studio performansını yönet** iletişim kutusu için bir bağlantı sağlar. bu iletişim kutusuna   >  , menü çubuğundan **Visual Studio performansını yönet** ' i seçerek de erişebilirsiniz.

![Visual Studio performans-açılan okumayı yönetme ' bu uzantıyı belirledik... yavaşlatma Visual Studio '](../ide/media/vside_perfdialog_popup.png)

İletişim kutusu, başlangıç performansını etkileyen Uzantılar ve araçlar pencerelerini listeler. Başlangıç performansını artırmak için uzantı ve araç penceresi ayarlarını değiştirebilirsiniz.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Başlangıç, çözüm yükleme ve yazma performansını geliştirmek için uzantı ayarlarını değiştirme

1. menü çubuğundan Visual Studio performansını yönet ' i seçerek **Visual Studio performansını yönet** iletişim kutusunu açın  >   .

    bir uzantı Visual Studio başlatma, çözüm yükleme veya yazma için yavaşanıyorsa, uzantı, **uzantılar** başlangıcı (veya çözüm yükleme veya yazma) altındaki **Visual Studio performansını yönet** iletişim kutusunda görünür  >    . 

    ![Visual Studio performance-extensions görünümünü yönetme](../ide/media/vside_perfdialog_extensions.png)

2. Devre dışı bırakmak istediğiniz uzantıyı seçin ve **devre dışı bırak** düğmesini seçin.

uzantı **yöneticisi** veya **Visual Studio performansını yönet** iletişim kutusunu kullanarak, uzantıları gelecekteki oturumlarla her zaman yeniden etkinleştirebilirsiniz.

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Başlatma süresini artırmak üzere araç penceresi ayarlarını değiştirmek için

1. menü çubuğundan Visual Studio performansını yönet ' i seçerek **Visual Studio performansını yönet** iletişim kutusunu açın  >   .

    bir araç penceresi Visual Studio başlatmayı yavaşlayorsa araç penceresi **araç Windows** başlatma altındaki **Visual Studio performansı yönet** iletişim kutusunda görünür  >  .

2. Davranışını değiştirmek istediğiniz araç penceresini seçin.

3. Aşağıdaki üç seçenekten birini belirleyin:

   - **Varsayılan davranışı kullan:** Araç penceresi için varsayılan davranış. Bu seçeneğin seçili tutulması, başlangıç performansını iyileştirmeyecektir.

   - **Başlangıçta pencere gösterme:** belirtilen araç penceresi, daha önceki bir oturumda açık bıraktığınız halde Visual Studio açtığınızda her zaman kapalıdır. Araç penceresini, ihtiyacınız olduğunda uygun menüden açabilirsiniz.

   - **Başlangıçta pencereyi otomatik gizle:** Bir araç penceresi önceki bir oturumda açık bırakılmış ise, bu seçenek araç penceresinin başlatılmasını önlemek için başlangıçta araç penceresinin grubunu daraltır. Bu seçenek, genellikle bir araç penceresi kullanıyorsanız iyi bir seçenektir. araç penceresi hala kullanılabilir, ancak artık Visual Studio başlangıç zamanını olumsuz şekilde etkilemeye devam eder.

     ![Visual Studio performans-araç windows görünümünü yönetme](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Visual Studio 2017 ' nin bazı önceki sürümlerinde, **hafif çözüm yükü** adlı bir özellik vardı. Geçerli sürümlerde, basit çözüm yükü olmadan bile, yönetilen kod yükünü içeren büyük çözümler daha önceden daha hızlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 2017 sürüm 15,6 ile blog yükleme çözümlerini daha hızlı Visual Studio](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
