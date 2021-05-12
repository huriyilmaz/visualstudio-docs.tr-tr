---
title: Başlarken ile Unity için Visual Studio Araçları | Microsoft Docs
description: Unity geliştirmesi için Visual Studio ve ayarlamayı öğrenin.
ms.custom: ''
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
ms.openlocfilehash: 791f25b61c86f0115c225d505bdb1edb07869961
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782614"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Kullanmaya başlayın ve Unity Visual Studio ile birlikte

> [!NOTE]
> Bu kılavuzda Unity Hub programını kullanarak Unity'i zaten yüklemişsinizdir. Unity'ye yeni başladıysanız önce Unity Learn'i ziyaret ederek [Unity Essentials öğrenme yolunu tamamlamanız](https://learn.unity.com/pathway/unity-essentials) önerilir.

## <a name="install-unity-support-for-visual-studio"></a>Visual Studio için Unity desteğini Visual Studio

Unity için Visual Studio Araçları, C# ve daha fazlasını yazmak ve hata ayıklamak için destek sağlayan ücretsiz bir uzantıdır. Uzantıların [neler dahil olduğunu eksiksiz](./visual-studio-tools-for-unity.md) bir liste için Unity araçlarına genel bakış'ı ziyaret edin.

:::zone pivot="windows"

> [!NOTE]
> Bu yükleme kılavuzu, Visual Studio. Visual Studio Code kullanıyorsanız lütfen VS Code Unity [Geliştirme'VS Code ziyaret edin.](https://code.visualstudio.com/docs/other/unity)

1. [Yükleme Visual Studio indirin](/visualstudio/install/install-visual-studio.md)veya zaten yüklüyse çalıştırın.
2. İstediğiniz **sürüm** için Değiştir (zaten yüklüyse) veya **Yükle** (yeni yüklemeler için) seçeneğine Visual Studio.
3. İş Yükleri **sekmesinde Oyun** bölümüne kaydırın **ve** Unity ile oyun geliştirme **iş yükünü** seçin.

    ![Yükleyicide Unity iş yükü kutusuyla oyun geliştirme](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Bu yükleme kılavuzu, Mac için Visual Studio. Visual Studio Code kullanıyorsanız lütfen VS Code [Unity Geliştirme'VS Code ziyaret edin.](https://code.visualstudio.com/docs/other/unity)

Unity araçları, Mac için Visual Studio yüklemesine dahildir ve ayrı yükleme adımları gerekmez. Bunu Oyun Geliştirme menüsünde Mac için Visual Studio > **Uzantıları > doğruabilirsiniz.** **Mac için Visual Studio Unity araçları** etkinleştirilmelidir.

![Unity için Mac için Visual Studio'nin etkin olduğunu gösteren Uzantı Yöneticisi görünümü](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Güncelleştirmeleri denetle

Visual Studio 'Yu ve Mac için Visual Studio güncel tutmanız önerilir, böylece en son hata düzeltmeleri, Özellikler ve Unity desteğiniz vardır. Bu, Unity sürümlerinin güncelleştirilmesini gerektirmez.

:::zone pivot="windows"

1. **Güncelleştirmeler Için yardım > denetle** menüsüne tıklayın.

    ![Visual Studio 2019 ' de güncelleştirmeleri denetle menüsü](../media/vs/check-for-updates.png)

2. Kullanılabilir bir güncelleştirme varsa Visual Studio Yükleyicisi yeni bir sürüm gösterir. **Güncelleştir** düğmesine tıklayın.

:::zone-end
:::zone pivot="macos"

1. **Visual Studio güncelleştirme** iletişim kutusunu açmak Için **Güncelleştirmeleri denetle... menüsünü > Mac için Visual Studio** tıklayın.
2. Kullanılabilir bir güncelleştirme varsa, **Install** düğmesine tıklayın.

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Unity 'yi Visual Studio kullanacak şekilde yapılandırma

Varsayılan olarak, Unity, Visual Studio 'Yu veya bir betik düzenleyicisi olarak Mac için Visual Studio kullanacak şekilde yapılandırılmış olmalıdır. Bunu veya dış betik düzenleyicisini, Unity düzenleyicisinden Visual Studio 'nun belirli bir sürümüne değiştirebilirsiniz.

:::zone pivot="windows"

1. Unity düzenleyicisinde **> Tercihleri Düzenle** menüsünü seçin.
2. Sol taraftaki **dış araçlar** sekmesini seçin.
3. **Dış betik Düzenleyicisi** açılan listesi, farklı Visual Studio yüklemelerini seçmek için bir yol sağlar. Listelenmemiş bir sürüm eklemek için açılan listeden da, **gezinme...** ' a tıklayabilirsiniz.

    ![Windows 'da Unity düzenleyicisinde dış araçlar tercih menüsü](../media/vs/preferences-external-tools.png)

4. Eğer **gözatamıyorum...** seçilirse, Visual Studio yükleme dizininizin içindeki **Common7/IDE** dizinine gidin ve **devenv.exe**' yi seçin. Ardından **Aç**' a tıklayın.
5. **Dış betik Düzenleyicisi** listesinde Visual Studio seçildikten sonra, **Düzenleyici iliştirme** onay kutusunun seçili olduğundan emin olun.
6. Yapılandırma işlemini gerçekleştirmek için **Tercihler** iletişim kutusunu kapatın.

:::zone-end
:::zone pivot="macos"

1. Unity Düzenleyicisi 'nde **unity > tercihleri** menüsünü seçin.
2. Sol taraftaki **dış araçlar** sekmesini seçin.
3. **Dış betik Düzenleyicisi** açılan listesi, farklı Visual Studio yüklemelerini seçmek için bir yol sağlar. Listelenmemiş bir sürüm eklemek için açılan listeden da, **gezinme...** ' a tıklayabilirsiniz.

    ![MacOS 'ta Unity düzenleyicisinde dış araçlar tercih menüsü](../media/vsm/preferences-external-tools.png)

4. Yapılandırma işlemini gerçekleştirmek için **Tercihler** iletişim kutusunu kapatın.

:::zone-end

## <a name="next-steps"></a>Sonraki adımlar

 Visual Studio 'da Unity projenizde çalışma ve hata ayıklama hakkında bilgi edinmek için [Unity için Visual Studio araçları kullanma](using-visual-studio-tools-for-unity.md)makalesini ziyaret edin.
