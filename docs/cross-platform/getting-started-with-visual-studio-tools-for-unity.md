---
title: Unity için Visual Studio Araçları ile Başlarken | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302275"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Unity için Visual Studio Tools ile başlayın

## <a name="install-visual-studio"></a>Visual Studio yükleme

### <a name="unity-bundled-installation"></a>Birlik birlikte yükleme

Unity 2018.1 ile başlayan Visual Studio, Unity için varsayılan C# komut dosyası düzenleyicisidir ve Unity Download Assistant'ın yanı sıra Unity Hub yükleme aracına da dahildir.

- [store.unity.com'dan](https://store.unity.com/)Unity indirin.

Yükleme sırasında Visual Studio'nun Unity ile yüklenmesi gereken bileşenler listesinde işaretlendiğinden emin olun:

#### <a name="unity-hub"></a>Birlik Merkezi

![unity hub kurulumu](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Birlik İndirme Asistanı

![unity download asistan yükleme](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Visual Studio için güncellemeleri kontrol edin

Unity yüklemenize dahil olan Visual Studio sürümü en son sürüm olmayabilir. En son araçlara ve özelliklere erişebildiğinizden emin olmak için güncelleştirmeleri denetlemeniz önerilir.

- [Visual Studio’yu güncelleştirme](../install/update-visual-studio.md)

### <a name="manual-installation"></a>El ile yükleme

Visual Studio 2017 yüklüyse veya el ile yüklemeyi tercih ediyorsanız, Visual Studio yükleyicisini çalıştırın.

1. [Visual Studio yükleyicisini indirin](../install/install-visual-studio.md)veya zaten yüklüyse açın.

1. Visual Studio'nun istediğiniz sürümü için **Değiştir** (zaten yüklüyse) veya **Yükle** 'yi (yeni yüklemeler için) tıklatın.

1. İş **Yükleri** sekmesinde, **Mobil & Oyun** bölümüne gidin ve Unity iş **yüküyle Oyun geliştirme öğesini** seçin.

    ![Birlik iş yükü](media/vstu_unity-workload.png)

1. Yükleyici penceresinin sağ alt köşesinde **Değiştir** (zaten yüklüyse) veya **Yükle'yi** (yeni yüklemeler için) tıklatın.

## <a name="configure-unity-for-use-with-visual-studio"></a>Visual Studio ile kullanım için Birliği Yapılandır

Unity 2018.1 ile başlayan Visual Studio, Unity'de varsayılan dış komut dosyası düzenleyicisi olmalıdır. Bunu onaylayabilir veya harici komut dosyası düzenleyicisini Visual Studio'nun belirli bir sürümüyle değiştirebilirsiniz:

1. **Edit** menüsünden **Tercihler'i** seçin.

   ![Tercihleri Seçin](media/vstu_unity-preferences.png)

2. Tercihler iletişim kutusunda Dış **Araçlar** sekmesini seçin.

3. Harici **Komut Dosyası Düzenleyicisi** açılır listesinden, listelenirse Visual Studio'nun istediğiniz sürümünü seçin, aksi takdirde **Gözat'ı seçin...**.

   ![Visual Studio'yı seçin](media/vstu_unity-external-tools.png)

4. **Browse...** seçildiyse, Visual Studio yükleme dizininizin içindeki **Common7/IDE** dizinine gidin ve **devenv.exe'yi**seçin. Sonra **Aç'ı**tıklatın.

   ![Aç'ı Seçin](media/vstu_browse-for-application.png)

5. Visual Studio **Dış Komut Dosyası Düzenleyicisi** listesinde seçildikten **sonra, Düzenleyici Ekleme** onay kutusunun seçildiğini onaylayın.

6. Yapılandırma işlemini tamamlamak için **Tercihler** iletişim kutusunu kapatın.

## <a name="support-for-older-versions"></a>Eski sürümler için destek

 Visual Studio Marketplace'ten Visual Studio Tools for Unity'yi indirin ve kurun. Visual Studio sürümünüz için doğru paketi yüklemeniz gerekir.

- Visual Studio 2015 Community, Visual Studio 2015 Professional veya Visual Studio 2015 Enterprise için:

   [Visual Studio 2015 Birlik Araçları İndir](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools for Unity 5.2 ve üzeri araçların yanı sıra Visual Studio Community, Professional, Premium veya Enterprise gibi uzantıları destekleyen bir Visual Studio sürümü gerektirir. Unity yüklemenizde Visual Studio Tools for Unity'nin etkin olduğunu doğrulamak için Yardım **menüsünden** **Birlik Hakkında'yı** seçin ve iletişim kutusunun sol alt kısmındaki "Microsoft Visual Studio Tools for Unity enabled" metnini arayın.
> ![hakkında Birlik](media/vstu_about-unity.png)

## <a name="next-steps"></a>Sonraki adımlar

 Visual Studio'da Unity projenizle nasıl çalışacağınızı ve hata ayıklamayı öğrenmek [için Visual Studio Tools for Unity bölümüne](../cross-platform/using-visual-studio-tools-for-unity.md)bakın.
