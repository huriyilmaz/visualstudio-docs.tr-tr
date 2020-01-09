---
title: Başlatma süresi geliştirin
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585788"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio Başlangıç süresini iyileştirme

Visual Studio, olabildiğince çabuk ve mümkün olduğunca verimli bir şekilde başlamak için tasarlanmıştır. Ancak, bazı Visual Studio uzantıları ve araç pencerelerini yüklü olduğunda başlangıç zamanını olumsuz etkileyebilir. Yavaş uzantıları davranışını denetleyen ve aracı windows **Visual Studio performansını Yönet** iletişim kutusu. Performansı artırma ile ilgili daha fazla genel ipuçları için bkz: [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Başlangıç davranışı

Başlangıç süresini genişletmemek için, Visual Studio _isteğe bağlı_ bir yaklaşım kullanarak uzantıları yükler. Bu davranış uzantıları hemen sonra Visual Studio başlatılır, ancak gerektiğinde olarak açmayın anlamına gelir. Ayrıca, önceki bir Visual Studio oturumu açık sol araç pencereleri başlangıç zamanını yavaşlatabileceği için Visual Studio Başlangıç süresini etkileyen önlemek için daha akıllı bir şekilde araç pencereleri açılır.

Visual Studio yavaş başlatma algılarsa, yavaşlama neden olan uzantı veya araç penceresinin için uyarı bir açılır ileti görüntülenir. İleti bir sayfaya bağlantı verilmektedir **Visual Studio performansını Yönet** iletişim kutusu. Bu iletişim kutusunu seçerek de erişebilirsiniz **yardımcı** > **Visual Studio performansını Yönet** menü çubuğundan.

![Açılan okuma - Visual Studio performansını Yönet ' uzantısının... ettik Visual Studio'yu yavaşlatıyor '](../ide/media/vside_perfdialog_popup.png)

İletişim kutusunun başlangıç performansı etkileyen uzantıları ve araçları windows listeler. Başlangıç performansı artırmak için uzantı ve araç penceresi ayarlarını değiştirebilirsiniz.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Başlangıç, çözüm yükü ve performans yazarak geliştirmek için uzantı ayarları değiştirmek için

1. Açık **Visual Studio performansını Yönet** iletişim kutusunu **yardımcı** > **Visual Studio performansını Yönet** menü çubuğundan.

    Bir uzantı yüklenirken, çözümü Visual Studio Başlangıç yavaşlatıyor veya yazarak, görünen uzantıyı **Visual Studio performansını Yönet** iletişim kutusunun altında **uzantıları**  >   **Başlangıç** (veya **çözüm yükü** veya **yazarak**).

    ![Visual Studio performansını - uzantıları görünümü yönetme](../ide/media/vside_perfdialog_extensions.png)

2. Devre dışı bırakın ve ardından istediğiniz uzantıyı seçin **devre dışı** düğmesi.

Her zaman uzantı için gelecekteki oturumları kullanarak yeniden etkinleştirebilirsiniz **Uzantı Yöneticisi** veya **Visual Studio performansını Yönet** iletişim kutusu.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Başlangıç süresini kısaltmak için araç penceresi ayarlarını değiştirmek için

1. Açık **Visual Studio performansını Yönet** iletişim kutusunu **yardımcı** > **Visual Studio performansını Yönet** menü çubuğundan.

    Araç penceresi Visual Studio Başlangıç yavaşlatıyor araç penceresi görünür **Visual Studio performansını Yönet** iletişim kutusunun altında **aracı Windows** > **başlatma**.

2. Davranışını değiştirmek istediğiniz araç penceresi seçin.

3. Aşağıdaki üç seçenekten birini seçin:

   - **Varsayılan davranışı kullan:** araç penceresi için varsayılan davranış. Bu seçenek tutma başlangıç performansı artırmak değildir.

   - **Başlangıçta pencere gösterme:** Visual Studio'da açtığınızda belirtilen araç penceresi önceki bir oturum açma sol olsa bile her zaman kapatılır. İhtiyacınız olduğunda, araç penceresi uygun menüsünden açabilirsiniz.

   - **Otomatik Gizle penceresi başlangıçta:** araç penceresini önceki bir oturumda açık bırakıldı, bu seçeneği araç penceresi başlatma önlemek için aracının pencere grubu başlangıçta daraltır. Araç penceresi genellikle kullanıyorsanız bu seçeneği iyi bir seçimdir. Araç penceresi hala kullanılabilir ancak Visual Studio Başlangıç süresini artık olumsuz etkiler.

     ![Visual Studio performansını Yönet - araç pencerelerini görüntüleyin](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Visual Studio 2017'in önceki bazı sürümlerinde denilen bir özelliği olan **basit çözüm yükü**. Geçerli sürümlerde, basit çözüm yükü olmadan bile, yönetilen kod yükünü içeren büyük çözümler daha önceden daha hızlıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio performansını iyileştirme](../ide/optimize-visual-studio-performance.md)
- [Visual Studio performans ipuçları ve püf noktaları](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blogu - Visual Studio 2017 sürüm 15.6 ile daha hızlı yük çözümleri](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
