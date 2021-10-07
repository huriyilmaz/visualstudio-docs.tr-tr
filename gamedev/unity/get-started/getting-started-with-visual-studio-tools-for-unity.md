---
title: Başlarken ile Unity için Visual Studio Araçları | Microsoft Docs
description: Unity geliştirme için Visual Studio ve ayarlamayı öğrenin.
ms.date: 01/27/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: c7daa1d99741cee9a480bfd2108ee093107ab58c
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635639"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Kullanmaya başlayın unity Visual Studio ile birlikte

> [!NOTE]
> Bu kılavuzda Unity Hub programını kullanarak Unity'i zaten yüklemişsinizdir. Unity'ye yeni başladıysanız önce Unity Learn'i ziyaret ederek [Unity Essentials öğrenme yolunu tamamlamanız](https://learn.unity.com/pathway/unity-essentials) önerilir.

## <a name="install-unity-support-for-visual-studio"></a>Visual Studio için Unity desteğini Visual Studio

Unity için Visual Studio Araçları, C# ve daha fazlasını yazmak ve hata ayıklamak için destek sağlayan ücretsiz bir uzantıdır. Uzantıların [neler dahil olduğunu eksiksiz](./visual-studio-tools-for-unity.md) bir liste için Unity araçlarına genel bakış'ı ziyaret edin.

:::zone pivot="windows"

> [!NOTE]
> Bu yükleme kılavuzu, Visual Studio. Visual Studio Code kullanıyorsanız lütfen VS Code [Unity Geliştirme'VS Code ziyaret edin.](https://code.visualstudio.com/docs/other/unity)

1. [Yükleme Visual Studio indirin](/visualstudio/install/install-visual-studio)veya zaten yüklüyse çalıştırın.
2. İstediğiniz **sürüm** için Değiştir (zaten yüklüyse) veya **Yükle** (yeni yüklemeler için) seçeneğine Visual Studio.
3. İş Yükleri **sekmesinde Oyun** bölümüne kaydırın **ve** Unity ile oyun geliştirme **iş yükünü** seçin.

    ![Yükleyicide Unity iş yükü kutusuyla oyun geliştirme](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Bu yükleme kılavuzu, Mac için Visual Studio. Visual Studio Code kullanıyorsanız lütfen VS Code [Unity Geliştirme'VS Code ziyaret edin.](https://code.visualstudio.com/docs/other/unity)

Unity araçları, Mac için Visual Studio yüklemesine dahildir ve ayrı yükleme adımları gerekmez. Bunu Oyun Geliştirme menüsünde **Mac için Visual Studio > Uzantıları > doğruabilirsiniz.** **Mac için Visual Studio Unity için araçlar** etkinleştirilmelidir.

![Unity için Mac için Visual Studio'nin etkin olduğunu gösteren Uzantı Yöneticisi görünümü](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Güncelleştirmeleri denetle

En son hata düzeltmeleri, Visual Studio ve Unity Mac için Visual Studio güncelliğini sürdürmenizi ve güncelleştirmenizi öneririz. Bu, Unity sürümlerinin güncelleştirilsini gerektirmez.

:::zone pivot="windows"

1. Güncelleştirmeleri **Denetleme > Yardım Menüsüne** tıklayın.

    ![Visual Studio 2019'da Güncelleştirmeleri Denetleme menüsü](../media/vs/check-for-updates.png)

2. Kullanılabilir bir güncelleştirme varsa, Visual Studio Yükleyicisi yeni bir sürüm gösterir. Güncelleştir **düğmesine** tıklayın.

:::zone-end
:::zone pivot="macos"

1. Güncelleştirmeleri **Mac için Visual Studio >... menüsüne** tıklayın ve güncelleştirme iletişim **Visual Studio** açın.
2. Kullanılabilir bir güncelleştirme varsa Yükle **düğmesine** tıklayın.

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Unity'yi Visual Studio

Varsayılan olarak Unity, betik düzenleyicisi olarak Visual Studio Mac için Visual Studio zaten yapılandırılmıştır. Bunu onaylayabilir veya Unity Düzenleyicisi'nde dış betik düzenleyicisini belirli bir Visual Studio sürümüyle değiştirebilirsiniz.

:::zone pivot="windows"

1. Unity Düzenleyicisi'nde, Düzenleme ve **> menüsünü** seçin.
2. Sol **tarafta Dış** Araçlar sekmesini seçin.
3. Dış **Betik Düzenleyicisi** açılan listesi, uygulamanın farklı yüklemelerini seçmenin bir Visual Studio. Listede olmayan bir sürüm eklemek için açılan listeden **Gözat...** 'a da tıkabilirsiniz.

    ![Windows'daki Unity Düzenleyicisi'nde Dış Araçlar tercih Windows](../media/vs/preferences-external-tools.png)

4. Gözat... **seçildiyse,** yükleme dizininizin içindeki **Common7/IDE** dizinine gidin ve Visual Studio'yi **devenv.exe.** Ardından **Aç'a tıklayın.**
5. Dış Visual Studio Düzenleyicisi listesinde bu onay kutusu **seçildikten** sonra Düzenleyici Ekleme **onay kutusunun** seçili olduğunu onaylayın.
6. Yapılandırma **işlemini tamamlamak için** Tercihler iletişim kutusunu kapatın.

:::zone-end
:::zone pivot="macos"

1. Unity Düzenleyicisi'nde Unity > **seçin.**
2. Sol **tarafta Dış** Araçlar sekmesini seçin.
3. Dış **Betik Düzenleyicisi** açılan listesi, uygulamanın farklı yüklemelerini seçmenin bir Visual Studio. Listede olmayan bir sürüm eklemek için açılan listeden **Gözat...** 'a da tıkabilirsiniz.

    ![macOS'ta Unity Düzenleyicisi'nde Dış Araçlar tercih menüsü](../media/vsm/preferences-external-tools.png)

4. Yapılandırma **işlemini tamamlamak için** Tercihler iletişim kutusunu kapatın.

:::zone-end

## <a name="next-steps"></a>Sonraki adımlar

 Visual Studio'da Unity projeniz ile çalışma ve hata ayıklama hakkında [Unity için Visual Studio Araçları.](using-visual-studio-tools-for-unity.md)
