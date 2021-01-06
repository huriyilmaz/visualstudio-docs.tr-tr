---
title: Unity için Visual Studio Araçları kullanmaya başlama | Microsoft Docs
description: Unity geliştirme için Visual Studio 'Yu yükleme ve kurma hakkında bilgi edinin.
ms.custom: ''
ms.date: 07/13/2020
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
ms.openlocfilehash: 1f8cbe1629aab6a177a46888fe25cf8e3565d91d
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903759"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Visual Studio ve Unity ile çalışmaya başlama

> [!NOTE]
> Bu kılavuzda Unity hub programını kullanarak Unity 'yi zaten yüklemiş olduğunuz varsayılmaktadır. Unity kullanmaya yeni başladıysanız Unity Öğrenini öğrenmenizi ve öncelikle [Unity Ile çalışmaya başlama öğreticisini](https://learn.unity.com/course/getting-started-with-unity) tamamlamayı öneririz.

## <a name="install-unity-support-for-visual-studio"></a>Visual Studio için Unity desteği 'ni yükler

Unity için Visual Studio Araçları, C# ve daha fazlasını yazmak ve hatalarını ayıklamak için destek sağlayan ücretsiz bir uzantıdır. Uzantıların neleri içerdiğine ilişkin tüm liste için [Unity 'ye genel bakış araçlarını](./visual-studio-tools-for-unity.md) ziyaret edin.

:::zone pivot="windows"

> [!NOTE]
> Bu yükleme kılavuzu, Visual Studio içindir. Visual Studio Code kullanıyorsanız, lütfen [vs Code belgeler Ile Unity geliştirmeyi](https://code.visualstudio.com/docs/other/unity)ziyaret edin.

1. [Visual Studio yükleyicisini indirin](/visualstudio/docs/install/install-visual-studio.md)veya zaten yüklüyse çalıştırın.
2. İstediğiniz Visual Studio sürümünüz için **Değiştir** (zaten yüklüyse) veya **yükleme** (yeni yüklemeler için) seçeneğine tıklayın.
3. **Iş yükleri** sekmesinde, **oyun** bölümüne gidin ve Unity iş yüküyle **oyun geliştirmeyi** seçin.

    ![Yükleyicideki Unity iş yükü kutusuyla oyun geliştirme](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Bu Yükleme Kılavuzu Mac için Visual Studio içindir. Visual Studio Code kullanıyorsanız, lütfen [vs Code belgeler Ile Unity geliştirmeyi](https://code.visualstudio.com/docs/other/unity)ziyaret edin.

Unity için Araçlar Mac için Visual Studio yüklemesine dahildir ve ayrı bir yükleme adımı gerekmez. Bunu, **Mac için Visual Studio > uzantıları > oyun geliştirme** menüsünde doğrulayabilirsiniz. **Unity için Mac için Visual Studio Araçları** etkinleştirilmelidir.

![Unity için Mac için Visual Studio Araçları gösteren Uzantı Yöneticisi görünümü](../media/vsm/unity-workload.png)

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
