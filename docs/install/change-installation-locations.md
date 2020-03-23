---
title: Yükleme konumlarını seçme
description: İndirme önbelleğinin, paylaşılan bileşenlerin, SDK'ların ve araçların konumunu farklı sürücülerle değiştirerek Visual Studio'nun sistem sürücünüzdeki kurulum ayak izini nasıl azaltacağınız hakkında bilgi edinin. Örneğin, bazı dosyaları C sürücüsünden D sürücüsüne taşıyın.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7f80d3c30c536e58811f8ca92676694b6d010010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111793"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Visual Studio'daki yükleme konumlarını seçin

::: moniker range="vs-2019"

Bazı dosyalarının konumunu değiştirerek Visual Studio'nun sistem sürücünüzdeki kurulum ayak izini azaltabilirsiniz. Özellikle, karşıdan yükleme önbelleği, paylaşılan bileşenler, SDK'lar ve araç dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

**Sürüm 15.7'de Yeni**: Bazı dosyalarının konumunu değiştirerek Visual Studio'nun sistem sürücünüzdeki kurulum ayak izini azaltabilirsiniz. Özellikle, karşıdan yükleme önbelleği, paylaşılan bileşenler, SDK'lar ve araç dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

   > [!NOTE]
   > Yüklenebilecekleri yerlere ilişkin farklı kurallara sahip bazı araçlar ve SDK'lar vardır. Başka bir konum seçseniz bile bu tür araçlar ve SDK'lar sistem sürücünüze yüklenir.

Başlamaya hazır mısınız? Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

1. Visual Studio'yu **yüklediğinizde, Yükleme konumları** sekmesini seçin.

   ![Visual Studio 2017 - Kurulum yerini seçin](media/vs-installation-locations.png "Yükleme konumunu seçin.")

1. Visual **Studio IDE** bölümünde varsayılanı kabul edin. Visual Studio çekirdek ürünü yükler ve Visual Studio'nun bu sürümüne özgü dosyaları içerir.

   ![Yükleme Konumları sekmesinin Visual Studio IDE bölümü](media/vs-installation-locations-ide.png "Yüklemeler Konum sekmesinin Visual Studio IDE bölümü için varsayılanı kabul edin.")

   > [!TIP]
   > Sistem sürücünüz katı hal sürücüsü (SSD) ise, sistem sürücünüzdeki varsayılan konumu kabul etmemi öneririz. Sebebi mi? Visual Studio ile geliştirdiğinizde, disk G/Ç etkinliğini artıran birçok dosyadan okuyup yazarsınız. Yükü işlemek için en hızlı sürücüseçmek en iyisidir.

1. İndir **önbelleği** bölümünde, karşıdan yükleme önbelleğini tutmak isteyip istemediğinize karar verin ve sonra dosyalarını nerede depolamak istediğinize karar verin.

     ![Yükleme Konumları sekmesinin Önbellek bölümünü indirin](media/vs-installation-locations-cache.png "Yüklemeden sonra karşıdan yükleme önbelleğini tutup tutmayacağınızı seçin ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. **Yüklemeden sonra indirme önbelleğini tut**veya denetlemeyi denetle.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

    1. Yükleme dosyalarını ve bildirimlerini yükleme önbelleğinden depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++'lı masaüstü geliştirme" iş yükünü seçerseniz, geçici olarak gerekli boyut sistem sürücünüzde 1,58 GB'dır ve yükleme tamamlanır tamamlanmaz serbest bırakılır.

       > [!IMPORTANT]
       > Bu konum ilk yüklemenizle birlikte ayarlanır ve daha sonra yükleyici nin ue'sinden değiştirilemez. Bunun yerine, karşıdan yükleme önbelleğini taşımak için [komut satırı parametrelerini kullanmanız](use-command-line-parameters-to-install-visual-studio.md) gerekir.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, yan yana Paylaşılan Dosyaları yan yana Paylaşılan dosyaları depolamak istediğiniz sürücüyü belirtin. SDK'lar ve araçlar da bu dizinde saklanır.

   ![Yükleme Konumları sekmesinin Paylaşılan Bileşenler, Araçlar ve SDK'lar bölümü](media/vs-installation-locations-shared.png "Paylaşılan bileşenleri, araçları ve SDK'ları depolamak istediğiniz konumu belirtin.")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu **yüklediğinizde, Yükleme konumları** sekmesini seçin.

   ![Visual Studio 2019 - Kurulum konumunu seçin](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin.")

1. Visual **Studio IDE** bölümünde varsayılanı kabul edin. Visual Studio çekirdek ürünü yükler ve Visual Studio'nun bu sürümüne özgü dosyaları içerir.

   > [!TIP]
   > Sistem sürücünüz katı hal sürücüsü (SSD) ise, sistem sürücünüzdeki varsayılan konumu kabul etmemi öneririz. Sebebi mi? Visual Studio ile geliştirdiğinizde, disk G/Ç etkinliğini artıran birçok dosyadan okuyup yazarsınız. Yükü işlemek için en hızlı sürücüseçmek en iyisidir.

1. İndir **önbelleği** bölümünde, karşıdan yükleme önbelleğini tutmak isteyip istemediğinize karar verin ve sonra dosyalarını nerede depolamak istediğinize karar verin.

    * **Yüklemeden sonra indirme önbelleğini tut**veya denetlemeyi denetle.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

    * Yükleme dosyalarını ve bildirimlerini yükleme önbelleğinden depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++'lı masaüstü geliştirme" iş yükünü seçerseniz, geçici olarak gerekli boyut sistem sürücünüzde 1,58 GB'dır ve yükleme tamamlanır tamamlanmaz serbest bırakılır.

       > [!IMPORTANT]
       > Bu konum ilk yüklemenizle birlikte ayarlanır ve daha sonra yükleyici nin ue'sinden değiştirilemez. Bunun yerine, karşıdan yükleme önbelleğini taşımak için [komut satırı parametrelerini kullanmanız](use-command-line-parameters-to-install-visual-studio.md) gerekir.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, "Önbelleği karşıdan yükle" bölümünde seçtiğiniz sürücüyü kullandığını unutmayın. \Microsoft\VisualStudio\Paylaşılan dizini Visual Studio'nun yan yana Paylaşılan Dosyaları depoladığı yerdir. SDK'lar ve araçlar da bu dizinde saklanır.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
