---
title: Unity için Visual Studio Araçları kullanmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c22b9c25f95ea26f2cdaf5c2035fb7a373123241
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408805"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları kullanmaya başlayın

## <a name="install-visual-studio"></a>Visual Studio yükleme

### <a name="unity-bundled-installation"></a>Unity ile birlikte yükleme

Unity 2018.1 itibarıyla Visual Studio, Unity için varsayılan C# betik düzenleyicisidir ve Unity Hub yükleme aracının yanı sıra Unity Download Assistant'ta mevcuttur.

- [Store.Unity.com](https://store.unity.com/)adresinden Unity 'yi indirin.

Yükleme sırasında Visual Studio'nun, Unity ile yüklenecek bileşenler listesinde işaretlendiğinden emin olun:

#### <a name="unity-hub"></a>Unity Hub

![Unity hub'ı yükleme](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Unity Yükleme Yardımcısı

![Unity Yükleme Yardımcısı'nı yükleme](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Visual Studio güncelleştirmelerini denetleme

Unity yüklemenize dahil olan Visual Studio sürümü, en son sürüm olmayabilir. En son araçlara ve özelliklere erişiminiz olduğundan emin olmak için güncelleştirmeleri denetlemeniz önerilir.

- [Visual Studio’yu güncelleştirme](../install/update-visual-studio.md)

### <a name="manual-installation"></a>El ile yükleme

Visual Studio 2017 zaten yüklüyse veya el ile yüklemeyi tercih ederseniz Visual Studio yükleyicisini çalıştırın.

1. [Visual Studio yükleyicisini indirin](../install/install-visual-studio.md)veya zaten yüklüyse açın.

1. İstediğiniz Visual Studio sürümünüz için **Değiştir** (zaten yüklüyse) veya **yükleme** (yeni yüklemeler için) seçeneğine tıklayın.

1. **Iş yükleri** sekmesinde, **mobil & oyunları** bölümüne kaydırın ve Unity iş yüküyle **oyun geliştirmeyi** seçin.

    ![Unity iş yükü](media/vstu_unity-workload.png)

1. Yükleyici penceresinin sağ alt köşesinde bulunan **Değiştir** (zaten yüklüyse) veya **yükleme** (yeni yüklemeler için) seçeneğine tıklayın.

## <a name="configure-unity-for-use-with-visual-studio"></a>Unity'yi Visual Studio ile kullanım için yapılandırma

Unity 2018.1 itibarıyla Visual Studio, Unity'de varsayılan dış kod düzenleyicisi olmalıdır. Bunu onaylayabilir veya dış betik düzenleyicisini Visual Studio'nun belirli bir sürümü olarak değiştirebilirsiniz:

1. **Düzenle** menüsünden **Tercihler** ' i seçin.

   ![Tercihler'i seçme](media/vstu_unity-preferences.png)

2. Tercihler iletişim kutusunda **dış araçlar** sekmesini seçin.

3. **Dış betik Düzenleyicisi** açılan listesinden, listede varsa, Istediğiniz Visual Studio sürümünü seçin, aksi takdirde, **araştır...** ' ı seçin.

   ![Visual Studio'yu seçme](media/vstu_unity-external-tools.png)

4. Eğer **gözatamıyorum...** seçilirse, Visual Studio yükleme dizininizin içindeki **Common7/IDE** dizinine gidin ve **devenv. exe**' yi seçin. Ardından **Aç**' a tıklayın.

   ![Aç'ı seçin](media/vstu_browse-for-application.png)

5. **Dış betik Düzenleyicisi** listesinde Visual Studio seçildikten sonra, **Düzenleyici iliştirme** onay kutusunun seçili olduğundan emin olun.

6. Yapılandırma işlemini gerçekleştirmek için **Tercihler** iletişim kutusunu kapatın.

## <a name="support-for-older-versions"></a>Eski sürümler için destek

 Unity için Visual Studio Araçları'nı Visual Studio Market'ten indirip yükleyin. Visual Studio sürümünüz için doğru paketi yüklemeniz gerekir.

- Visual Studio 2015 Community, Visual Studio 2015 Professional veya Visual Studio 2015 Enterprise için:

   [Unity için Visual Studio 2015 araçlarını indirin](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Unity için Visual Studio Araçları, Unity 5.2 veya sonraki bir sürümünün yanı sıra Visual Studio Community, Professional, Premium ya da Enterprise gibi uzantıları destekleyen bir Visual Studio sürümü gerektirir. Unity 'nin yüklemesinde Unity için Visual Studio Araçları etkinleştirildiğini doğrulamak için, **Yardım** menüsünde **Unity hakkında** ' yı seçin ve iletişim kutusunun sol alt kısmındaki "Unity için Microsoft Visual Studio Araçları" metnini arayın.
> Unity](media/vstu_about-unity.png) hakkında ![

## <a name="next-steps"></a>Sonraki adımlar

 Visual Studio 'da Unity projenizde çalışma ve hata ayıklama hakkında bilgi edinmek için bkz. [Unity için Visual Studio Araçları](../cross-platform/using-visual-studio-tools-for-unity.md).
