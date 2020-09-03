---
title: Unity için Visual Studio Araçları kullanmaya başlama | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a8f3e183bd72e9894eae55a5ed7c4f9322d44953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250103"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçları kullanmaya başlayın

## <a name="install-visual-studio"></a>Visual Studio'yu yükleme

### <a name="unity-bundled-installation"></a>Unity paketlenmiş yükleme

Unity 2018,1 ' den itibaren, Visual Studio Unity için varsayılan C# betik düzenleyicisidir ve Unity hub yükleme aracına ek olarak Unity Indirme Yardımcısı ' na de dahildir.

- [Store.Unity.com](https://store.unity.com/)adresinden Unity 'yi indirin.

Yükleme sırasında, Visual Studio 'Nun Unity ile yüklenecek bileşenler listesinde işaretli olduğundan emin olun:

#### <a name="unity-hub"></a>Unity hub 'ı

:::moniker range="vs-2017"
![Unity hub yüklemesi](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![Unity hub yüklemesi](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Unity Indirme Yardımcısı

![Unity indirme Yardımcısı yüklemesi](media/vs-2017/vstu-download-assistant.png)

Unity yüklemenize dahil olan Visual Studio sürümü en son sürüm olmayabilir. Visual Studio 2017 ' i yüklemeniz istenirse, Visual Studio 'nun daha yeni bir sürümünü el ile yüklemenizi öneririz.
:::moniker-end

### <a name="manual-installation"></a>El ile yükleme

Zaten Visual Studio yüklüyse veya el ile yüklemeyi tercih ediyorsanız, Visual Studio yükleyicisini çalıştırın.

1. [Visual Studio yükleyicisini indirin](../install/install-visual-studio.md)veya zaten yüklüyse açın.

1. İstediğiniz Visual Studio sürümünüz için **Değiştir** (zaten yüklüyse) veya **yükleme** (yeni yüklemeler için) seçeneğine tıklayın.

1. **Iş yükleri** sekmesinde, **Mobil & oyunları** bölümüne kaydırın ve Unity iş yüküyle **oyun geliştirmeyi** seçin.

   :::moniker range="vs-2017"
   ![Unity iş yükü](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Unity iş yükü](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. Yükleyici penceresinin sağ alt köşesinde bulunan **Değiştir** (zaten yüklüyse) veya **yükleme** (yeni yüklemeler için) seçeneğine tıklayın.

#### <a name="check-for-updates-to-visual-studio"></a>Visual Studio güncelleştirmelerini denetle

En son araçlara ve özelliklere erişiminizin olduğundan emin olmak için Visual Studio içindeki güncelleştirmelerin denetlenmesi önerilir. Bu, Unity projenizi bozmaz.

- [Visual Studio’yu güncelleştirme](../install/update-visual-studio.md)

## <a name="configure-unity-for-use-with-visual-studio"></a>Unity 'yi Visual Studio ile kullanım için yapılandırma

Unity 2018,1 ' den itibaren, Visual Studio 'Nun Unity 'de varsayılan dış betik Düzenleyicisi olması gerekir. Bunu doğrulayabilirsiniz veya dış betik düzenleyicisini Visual Studio 'nun belirli bir sürümüne değiştirebilirsiniz:

1. **Düzenle** menüsünden **Tercihler** ' i seçin.

   :::moniker range="vs-2017"
   ![Tercihleri seçin](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Tercihleri seçin](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. Tercihler iletişim kutusunda **dış araçlar** sekmesini seçin.

3. **Dış betik Düzenleyicisi** açılan listesinden, listede varsa, Istediğiniz Visual Studio sürümünü seçin, aksi takdirde, **araştır...**' ı seçin.

   :::moniker range="vs-2017"
   ![Visual Studio 'Yu seçin](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Visual Studio 'Yu seçin](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end

4. Eğer **gözatamıyorum...** seçilirse, Visual Studio yükleme dizininizin içindeki **Common7/IDE** dizinine gidin ve **devenv.exe**' yi seçin. Ardından **Aç**' a tıklayın.

   :::moniker range="vs-2017"
   ![Açık Seç](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Açık Seç](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. **Dış betik Düzenleyicisi** listesinde Visual Studio seçildikten sonra, **Düzenleyici iliştirme** onay kutusunun seçili olduğundan emin olun.

6. Yapılandırma işlemini gerçekleştirmek için **Tercihler** iletişim kutusunu kapatın.

## <a name="support-for-older-versions"></a>Eski sürümler için destek

Visual Studio Market Unity için Visual Studio Araçları indirin ve yükleyin. Visual Studio sürümünüz için doğru paketi yüklemeniz gerekir.

- Visual Studio 2015 Community, Visual Studio 2015 Professional veya Visual Studio 2015 Enterprise için:

   [Unity için Visual Studio 2015 araçlarını indirin](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Unity için Visual Studio Araçları Unity 5,2 ve üzeri ve Visual Studio Community, Professional, Premium veya Enterprise gibi uzantıları destekleyen bir Visual Studio sürümü gerektirir. Unity 'nin yüklemesinde Unity için Visual Studio Araçları etkinleştirildiğini doğrulamak için, **Yardım** menüsünde **Unity hakkında** ' yı seçin ve iletişim kutusunun sol alt kısmındaki "Unity için Microsoft Visual Studio Araçları" metnini arayın.
> ![Unity hakkında](media/vs-2019/vstu-about-unity.png)

## <a name="next-steps"></a>Sonraki adımlar

 Visual Studio 'da Unity projenizde çalışma ve hata ayıklama hakkında bilgi edinmek için bkz. [Unity için Visual Studio Araçları](../cross-platform/using-visual-studio-tools-for-unity.md).
