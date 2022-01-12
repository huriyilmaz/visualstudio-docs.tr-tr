---
title: 'hızlı başlangıç: ınstall & configure Unity için Visual Studio Araçları'
description: platformlar arası geliştirme için Unity ve Visual Studio bağlamayı öğrenin.
ms.date: 12/10/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: quickstart
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 67e0893ad5fd0329a9542ecec5991f8ae641df02
ms.sourcegitcommit: 2a4744fb312396d36086dd59fd55ab741ae8e106
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/28/2021
ms.locfileid: "135575976"
---
# <a name="quickstart-configure-visual-studio-for-cross-platform-development-with-unity"></a>hızlı başlangıç: Unity ile platformlar arası geliştirme için Visual Studio yapılandırma

bu hızlı başlangıçta, Unity için Visual Studio Araçları uzantısını yüklemeyi ve Unity ile platformlar arası oyunlar ve uygulamalar geliştirmeye yönelik yapılandırmayı öğreneceksiniz.  Unity için Visual Studio Araçları uzantısı ücretsizdir ve C# ve daha fazlasını yazmak ve hatalarını ayıklamak için destek sağlar. Uzantıların neleri içerdiğine ilişkin tüm liste için [Unity 'ye genel bakış araçlarını](./visual-studio-tools-for-unity.md) ziyaret edin.

> [!NOTE]
> unity & Visual Studio Code için [VS Code belgelerindeki unity geliştirmeyi](https://code.visualstudio.com/docs/other/unity)ziyaret edin.

## <a name="install-visual-studio-and-unity"></a>Visual Studio ve Unity 'yi yükleyip

:::zone pivot="windows"

1. [Visual Studio yükleyicisini indirin](/visualstudio/install/install-visual-studio.md)veya zaten yüklüyse açın.
2. İstediğiniz Visual Studio sürümünüz için **Değiştir** (zaten yüklüyse) veya **yükleme** (yeni yüklemeler için) öğesini seçin.
3. **Iş yükleri** sekmesini seçin ve ardından Unity iş yüküyle **oyun geliştirmeyi** seçin.    
4. Unity zaten yüklü değilse, yükleyicinin Isteğe bağlı bölümünde Unity hub onay kutusunu seçin.
5. Yüklemeyi gerçekleştirmek için **Değiştir** veya **Yükleme ' yi** seçin.

![Yükleyicideki Unity iş yükü ile oyun geliştirme 'nın ekran görüntüsü](../media/vs/unity-workload.png)

Visual Studio, yükleme işlemini tamamladıktan sonra Unity kurulumuna hazırsınız demektir.

1. Unity için Visual Studio Araçları yüklemesi sırasında yüklenen Unity Hub 'ını açın.
1. Unity hub penceresinin sol tarafında, **yüklemeler** sekmesini seçin.
1. **Ekle** düğmesini seçin.
1. Unity sürümü Ekle penceresinde, bir Unity sürümünü yüklemek için seçin.
1. Yüklemeye devam etmek için **İleri ' yi** seçin.
1. **Yüklemeye modüller ekleme** adımından **bitti**' yi seçin.

>[!NOTE]
>zaten 2022 Visual Studio yüklediyseniz, Microsoft Visual Studio Community 2019 seçeneğinin seçimini kaldırabilirsiniz.

Unity hub, arka planda Unity yüklemeye devam edecektir. Bu tamamlandığında, **Projeler** sekmesini seçerek ve **Yeni** düğmesini seçerek yeni bir proje oluşturabilirsiniz.

>[!TIP]
>Projeler, Visual Studio değil Unity Düzenleyicisi kullanılarak oluşturulur.

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> bu yükleme kılavuzu Mac için Visual Studio içindir. Visual Studio Code kullanıyorsanız, lütfen [VS Code belgeler ile Unity geliştirmeyi](https://code.visualstudio.com/docs/other/unity)ziyaret edin.

Unity için Mac için Visual Studio araçları, Mac için Visual Studio yüklemesine dahildir ve ayrı yükleme adımları gerekli değildir. bunu, **Mac için Visual Studio > uzantıları > oyun geliştirme** menüsünde doğrulayabilirsiniz. **Unity için Mac için Visual Studio araçları** etkinleştirilmelidir.

![Unity için Mac için Visual Studio araçları gösteren uzantı yöneticisi görünümünün ekran görüntüsü](../media/vsm/unity-workload.png)

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Unity 'yi Visual Studio kullanacak şekilde yapılandırma

varsayılan olarak, Unity zaten bir betik düzenleyicisi olarak Visual Studio veya Mac için Visual Studio kullanacak şekilde yapılandırılmalıdır. bunu veya dış betik düzenleyicisini Unity düzenleyicisinden Visual Studio belirli bir sürümüne değiştirebilirsiniz.

:::zone pivot="windows"

1. Unity düzenleyicisinde **> tercihlerini Düzenle** menüsünü seçin.
2. Sol tarafta **dış araçlar** sekmesini seçin.

    ![Windows 'daki Unity düzenleyicisinde dış araçlar tercihi menüsünün ekran görüntüsü](../media/vs/preferences-external-tools.png)

### <a name="install-or-update-the-visual-studio-editor-package"></a>Visual Studio düzenleyicisi paketini yükler veya güncelleştirir

Unity sürümleri 2020 ve daha yeni sürümlerde, Visual Studio gibi en iyi deneyim ile çalışma için ayrı bir Unity paketi gerekir. Bu, varsayılan olarak dahil edilmelidir, ancak bu pakete, dilediğiniz zaman güncelleyebilir güncelleştirmeler yayınlarız.

1. Unity düzenleyicisinde **Windows > Paket Yöneticisi** menüsünü seçin.
1. **Visual Studio düzenleyicisi** paketini seçin.
1. Yeni bir sürüm varsa **Güncelleştir** düğmesini seçin.

![Windows üzerinde Unity düzenleyicisinde Paket Yöneticisi penceresinin ekran görüntüsü](../media/vs/unity-package-manager.png)

### <a name="add-a-version-of-visual-studio-that-is-not-listed"></a>listelenmeyen Visual Studio bir sürümünü ekleyin
listelenmemiş ve özel bir dizinde yüklü olan Visual Studio diğer sürümlerini seçmek mümkündür.

1. Açılan listeden **araştır...** seçeneğini belirleyin.
2. Visual Studio yükleme dizininizin içindeki **Common7/ıde** dizinine gidin ve **devenv.exe**' i seçin. Ardından **Aç**' a tıklayın.
3. Yalnızca Unity 2019 ve üzeri için **Düzenleyici iliştirme** onay kutusunun seçili olduğundan emin olun.
4. Yapılandırma işlemini gerçekleştirmek için **Tercihler** iletişim kutusunu kapatın.

:::zone-end
:::zone pivot="macos"

1. Unity Düzenleyicisi 'nde **unity > tercihleri** menüsünü seçin.
2. Sol tarafta **dış araçlar** sekmesini seçin.
3. **dış betik düzenleyicisi** açılır listesini kullanmak, farklı Mac için Visual Studio yüklemelerini seçmek için bir yol sağlar.

    ![MacOS 'ta Unity düzenleyicisinde dış araçlar tercihi menüsünün ekran görüntüsü](../media/vsm/preferences-external-tools.png)

4. Yapılandırma işlemini gerçekleştirmek için **Tercihler** iletişim kutusunu kapatın.

:::zone-end

## <a name="check-for-updates"></a>Güncelleştirmeleri denetle

en son hata düzeltmeleri, özellikler ve Unity desteği için Visual Studio ve Mac için Visual Studio güncel tutmanız önerilir. Bu, Unity sürümlerinin güncelleştirilmesini gerektirmez.

:::zone pivot="windows"

1. **Güncelleştirmeler Için yardım > denetle** menüsüne tıklayın.

    ![Visual Studio 2019 ' de güncelleştirmeleri denetle menüsünün ekran görüntüsü](../media/vs/check-for-updates.png)    

2. kullanılabilir bir güncelleştirme varsa Visual Studio Yükleyicisi yeni bir sürüm gösterir. **Güncelleştir** düğmesine tıklayın.

:::zone-end
:::zone pivot="macos"

1. **Visual Studio güncelleştirme** iletişim kutusunu açmak için **güncelleştirmeleri denetle... menüsünü Mac için Visual Studio >** tıklayın.
2. Kullanılabilir bir güncelleştirme varsa, **Install** düğmesine tıklayın.

:::zone-end

## <a name="next-steps"></a>Sonraki adımlar

bu uzantının [tümleştirme ve üretkenlik özellikleri hakkında bilgi edinin ve Unity geliştirme için Visual Studio hata ayıklayıcı 'yı nasıl kullanacağınızı](using-visual-studio-tools-for-unity.md)öğrenin.
