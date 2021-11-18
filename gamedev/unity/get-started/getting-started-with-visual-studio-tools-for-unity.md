---
title: 'Hızlı Başlangıç: Yapılandırma & yükleme Unity için Visual Studio Araçları'
description: Platformlar arası geliştirme için Unity ve Visual Studio bağlamayı öğrenin.
ms.date: 11/17/2021
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
ms.openlocfilehash: a27ec6f2fa0cd9ffc6eb3e62b7de4b7a2adaee0a
ms.sourcegitcommit: dd66ab447c6f33de525f9429de1f912dd538a6d5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2021
ms.locfileid: "132773167"
---
# <a name="quickstart-configure-visual-studio-for-cross-platform-development-with-unity"></a>Hızlı Başlangıç: Unity Visual Studio platformlar arası geliştirme için yapılandırma

Bu hızlı başlangıçta, Unity için Visual Studio Araçları uzantısını yükleme ve Unity ile platformlar arası oyunlar ve uygulamalar geliştirmek için yapılandırmayı öğrenirsiniz.  Bu Unity için Visual Studio Araçları ücretsizdir ve C# yazmak ve hata ayıklamak için destek sağlar. Uzantıların [neler dahil olduğunu tam](./visual-studio-tools-for-unity.md) bir liste için Unity araçlarına genel bakış'ı ziyaret edin.

> [!NOTE]
> Unity Visual Studio Code & için Unity Ile [Unity Geliştirme VS Code ziyaret edin.](https://code.visualstudio.com/docs/other/unity)

## <a name="prerequisites"></a>Önkoşullar

+ Bu kılavuzda Unity Hub programını kullanarak Unity'i zaten yüklemişsinizdir. Unity'ye yeni başladıysanız önce [Unity Essentials öğrenme yolunu](https://learn.unity.com/pathway/unity-essentials) tamamlar.

## <a name="install-visual-studio-tools-for-unity"></a>Yükleme Unity için Visual Studio Araçları

:::zone pivot="windows"

1. [Yükleme Visual Studio indirin](/visualstudio/install/install-visual-studio)veya zaten yüklüyse çalıştırın.
2. İstediğiniz **sürüm** için Değiştir (zaten yüklüyse) veya **Yükle** (yeni yüklemeler için) seçeneğine Visual Studio.
3. İş Yükleri **sekmesinde Oyun** bölümüne kaydırın **ve** Unity ile oyun geliştirme **iş yükünü** seçin.

    ![Yükleyicide Unity iş yükü kutusuyla oyun geliştirme](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

Unity araçları, Mac için Visual Studio yüklemesine dahildir ve ayrı yükleme adımları gerekmez. Bunu Oyun Geliştirme menüsünde **Mac için Visual Studio > uzantıları > doğruabilirsiniz.** **unity Mac için Visual Studio araçları** etkinleştirilmelidir.

![Unity için Mac için Visual Studio'nin etkin olduğunu gösteren Uzantı Yöneticisi görünümü](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Güncelleştirmeleri denetle

En son hata düzeltmelerini, Visual Studio ve Unity Mac için Visual Studio güncel tutmanın ve güncelleştirmenin güncelliğini sürdürmenizi öneririz. Bu, Unity sürümlerinin güncelleştirilsini gerektirmez.

:::zone pivot="windows"

1. Güncelleştirmeleri **Denetleme > Yardım Menüsüne** tıklayın.

    ![Visual Studio 2019'da Güncelleştirmeleri Denetleme menüsü](../media/vs/check-for-updates.png)

2. Kullanılabilir bir güncelleştirme varsa, Visual Studio Yükleyicisi sürümü gösterir. Güncelleştir **düğmesine** tıklayın.

:::zone-end
:::zone pivot="macos"

1. Güncelleştirmeleri **Mac için Visual Studio >... menüsüne** tıklayın ve güncelleştirme iletişim **Visual Studio** açın.
2. Kullanılabilir bir güncelleştirme varsa Yükle **düğmesine** tıklayın.

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Unity'yi Visual Studio

Varsayılan olarak Unity, betik düzenleyicisi olarak Visual Studio Mac için Visual Studio zaten yapılandırılmıştır. Bunu onaylayabilir veya Unity Düzenleyicisi'nde dış betik düzenleyicisini belirli bir Visual Studio sürümüyle değiştirebilirsiniz.

:::zone pivot="windows"

1. Unity Düzenleyicisi'nde, **Tercihler menüsünü > seçin.**
2. Sol **tarafta Dış** Araçlar sekmesini seçin.
3. Dış **Betik Düzenleyicisi** açılan listesi, uygulamanın farklı yüklemelerini seçmenin bir Visual Studio. Listede olmayan bir sürüm eklemek için açılan listeden **Gözat...** 'a da tıkabilirsiniz.

    ![Windows'daki Unity Düzenleyicisi'nde Dış Araçlar tercih Windows](../media/vs/preferences-external-tools.png)

4. Gözat... **seçildiyse,** uygulama yükleme dizininizin içindeki **Common7/IDE** dizinine Visual Studio ve **devenv.exe.** Ardından **Aç'a tıklayın.**
5. Dış Visual Studio Düzenleyicisi listesinde bu onay kutusu **seçildikten** sonra Düzenleyici Ekleme **onay kutusunun** seçili olduğunu onaylayın.
6. Yapılandırma **işlemini tamamlamak için** Tercihler iletişim kutusunu kapatın.

:::zone-end
:::zone pivot="macos"

1. Unity Düzenleyicisi'nde Unity > **menüsünü** seçin.
2. Sol **tarafta Dış** Araçlar sekmesini seçin.
3. Dış **Betik Düzenleyicisi** açılan listesi, uygulamanın farklı yüklemelerini seçmenin bir Visual Studio. Listede olmayan bir sürüm eklemek için açılan listeden **Gözat...** 'a da tıkabilirsiniz.

    ![macOS'ta Unity Düzenleyicisi'nde Dış Araçlar tercih menüsü](../media/vsm/preferences-external-tools.png)

4. Yapılandırma **işlemini tamamlamak için** Tercihler iletişim kutusunu kapatın.

:::zone-end

## <a name="next-steps"></a>Sonraki adımlar

Bu uzantının tümleştirme ve üretkenlik özellikleri hakkında bilgi edinmek ve Unity geliştirmesi için [Visual Studio hata ayıklayıcısını kullanmayı öğrenin.](using-visual-studio-tools-for-unity.md)
