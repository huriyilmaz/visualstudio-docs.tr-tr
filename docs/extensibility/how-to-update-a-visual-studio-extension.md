---
title: 'Nasıl: Güncelleme Görsel Stüdyo Uzantısı | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710663"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Nasıl yapılsın: Visual Studio uzantısını güncelleştir
Güncelleştirilmiş sürümü yüklemek için **Uzantılar ve Güncelleştirmeler'i** kullanarak sisteminizdeki Visual Studio uzantısını güncelleştirebilirsiniz. Bir uzantının güncelleştirilmiş bir sürümünü oluşturursanız, VSIX bildirimindeki sürüm numarasını artışarak uzantıyı güncelleştirebilirsiniz.

 Gelen uzantının VSIX bildirimi yüklü olanla aynı `ID` ve daha yüksek `Version` bir sayıya sahip olduğunda güncelleştirmeler yüklenir. Numara `Version` aynı veya daha düşükse, paket yüklenemez. `ID` Değerler eşleşmiyorsa, henüz yüklenmemiş paket ayrı bir uzantı olarak kabul edilir.

 Geliştirme sırasında çakışmaları önlemeye yardımcı olmak için, devam eden uzantıların önceki sürümlerini kaldırmanızı ve çakışma potansiyeline sahip diğer uzantıları kaldırmanızı veya devre dışı bırakmanızı öneririz.

## <a name="to-update-an-extension-on-your-system"></a>Sisteminizdeki bir uzantıyı güncelleştirmek için

1. **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler**’e tıklayın.

2. Sol bölmede **Güncelleştirmeler'i**tıklatın.

3. Orta bölmede, yüklemek istediğiniz güncelleştirmeyi tıklatın.

     Güncelleştirilmiş uzantının sürüm numarası, diğer bilgilerle birlikte sağ bölmede görüntülenir.

4. Sağ bölmenin alt kısmında, **Güncelleştir'i**tıklatın.

## <a name="to-publish-an-update-of-an-extension"></a>Uzantının güncelleştirmesini yayımlamak için

1. Visual Studio'da, güncelleştirmek istediğiniz uzantıniçin çözümü açın. Değişiklikleri yap.

    > [!IMPORTANT]
    > İmzasız tüm kullanıcı uzantıları otomatik olarak güncelleştirilmemiş. Uzantılarınızı her zaman imzalamalısınız.

2. **Çözüm Gezgini'** nde , open *source.extension.manifest*.

3. Bildirim tasarımcısında, **Sürüm** alanındaki sayının değerini artırın.

4. Çözümü kaydedin ve oluşturun.

5. Yeni *.vsix* dosyasını (projenin *\bin\Debug\* klasöründe) [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Web sitesine yükleyin.

     Uzantının daha önceki bir sürümüne sahip bir kullanıcı **Uzantılar ve Güncelleştirmeler'i**açtığında, yeni sürüm, aracın güncelleştirmeleri otomatik olarak arayacak şekilde ayarlanmış olması koşuluyla **Güncelleştirmeler** listesinde görünür.

     **Güncelleştirmeler** bölmesinin altındaki güncelleştirmeleri otomatik olarak denetlemeyi etkinleştirebilir veya devre dışı kullanabilirsiniz **(Kullanılabilir güncelleştirmelerin otomatik algılamasını etkinleştirme/devre dışı)** bu da **Araçlar** > **Seçenekleri** > **Ortamı** > **Uzantıları ve Güncelleştirmeleri'ndeki** **güncelleştirmeler ayarını** değiştirir.

    > [!NOTE]
    > Visual Studio 2015 Update 2'den başlayarak, kullanıcı başına uzantılar için otomatik güncelleştirmeler, tüm kullanıcı uzantıları veya her ikisi için (varsayılan ayar) otomatik güncelleştirmeler isteyip istemediğiniz **(Araçlar** > **Seçenekleri** > **Ortamı** > **Uzantıları ve Güncelleştirmeleri'nde)** belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
- [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)
