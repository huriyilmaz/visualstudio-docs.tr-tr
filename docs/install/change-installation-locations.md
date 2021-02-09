---
title: Yükleme konumlarını seçme
description: İndirme önbelleğinin, paylaşılan bileşenlerin, SDK 'ların ve araçların konumunu farklı sürücülere değiştirerek, sistem sürücünüzdeki Visual Studio 'nun yükleme ayak izini nasıl azaltacağınızı öğrenin. Örneğin, bazı dosyaları C sürücüsünden D sürücüsüne taşıyın.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4db3a31c8baa578a17d14b3a740ff40a444ba208
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868640"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Visual Studio 'da yükleme konumlarını seçme

::: moniker range="vs-2019"

Bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio 'nun yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK 'lar ve araçlar dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

**Sürüm 15,7 ' de yeni**: bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio 'nun yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK 'lar ve araçlar dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

   > [!NOTE]
   > Yüklenebilecekleri farklı kurallara sahip bazı araçlar ve SDK 'lar vardır. Bu tür araçlar ve SDK 'lar, başka bir konum seçseniz bile sistem sürücünüze yüklenir.

Başlamaya hazır mısınız? Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

1. Visual Studio 'Yu yüklediğinizde, **yükleme konumları** sekmesini seçin.

   ![Visual Studio 2017-yükleme konumunu seçin](media/vs-installation-locations.png "Yükleme konumunu seçin.")

1. **Visual STUDIO IDE** bölümünde, Varsayılanı kabul edin. Visual Studio, çekirdek ürünü yükleyerek Visual Studio 'nun bu sürümüne özgü dosyaları içerir.

   ![Yükleme konumları sekmesinin Visual Studio IDE bölümü](media/vs-installation-locations-ide.png "Yükleme konumu sekmesinin Visual Studio IDE bölümü için varsayılanı kabul edin.")

   > [!TIP]
   > Sistem sürücünüz bir katı hal sürücüsü (SSD) ise, sistem sürücünüzdeki varsayılan konumu kabul etmenizi öneririz. Neden? Visual Studio ile geliştirirken, disk g/ç etkinliğini artıran ve çok sayıda dosyayı okur. Yükü işlemek için en hızlı sürücüyü seçmeniz önerilir.

1. **Önbelleği indir** bölümünde, indirme önbelleğini tutmak istediğinize karar verin ve sonra dosyalarını nerede saklamak istediğinize karar verin.

     ![Yükleme konumları sekmesinin önbellek indirme bölümü](media/vs-installation-locations-cache.png "Yükleme sonrasında indirme önbelleğinin tutulup tutulmayacağını seçin ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. **Yükleme sonrasında indirme önbelleğini koru** veya işaretini kaldır.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem önceki yüklemelerin dosyalarını etkilemez veya silmez.

    1. Yükleme önbelleğinden yükleme dosyalarını ve bildirimlerini depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçerseniz, geçici olarak gereken boyut sistem sürücünüzde 1,58 GB olur ve bu, yükleme tamamlanır tamamlanmaz serbest bırakılır.

       > [!IMPORTANT]
       > Bu konum, ilk yüklemenizde ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, indirme önbelleğini taşımak için [komut satırı parametrelerini kullanmanız](use-command-line-parameters-to-install-visual-studio.md) gerekir.

1. **Paylaşılan bileşenler, Araçlar ve SDK** 'lar bölümünde, yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depolamak istediğiniz sürücüyü belirtin. SDK 'lar ve araçlar bu dizinde da depolanır.

   ![Yükleme konumları sekmesinin paylaşılan bileşenler, Araçlar ve SDK 'lar bölümü](media/vs-installation-locations-shared.png "Paylaşılan bileşenleri, araçları ve SDK 'Ları depolamak istediğiniz konumu belirtin.")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 'Yu yüklediğinizde, **yükleme konumları** sekmesini seçin.

   ![Visual Studio 2019-yükleme konumunu seçin](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin.")

1. **Visual STUDIO IDE** bölümünde, Varsayılanı kabul edin. Visual Studio, çekirdek ürünü yükleyerek Visual Studio 'nun bu sürümüne özgü dosyaları içerir.

   > [!TIP]
   > Sistem sürücünüz bir katı hal sürücüsü (SSD) ise, sistem sürücünüzdeki varsayılan konumu kabul etmenizi öneririz. Neden? Visual Studio ile geliştirirken, disk g/ç etkinliğini artıran ve çok sayıda dosyayı okur. Yükü işlemek için en hızlı sürücüyü seçmeniz önerilir.

1. **Önbelleği indir** bölümünde, indirme önbelleğini tutmak istediğinize karar verin ve sonra dosyalarını nerede saklamak istediğinize karar verin.

    * **Yükleme sonrasında indirme önbelleğini koru** veya işaretini kaldır.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem önceki yüklemelerin dosyalarını etkilemez veya silmez.

    * Yükleme önbelleğinden yükleme dosyalarını ve bildirimlerini depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçerseniz, geçici olarak gereken boyut sistem sürücünüzde 1,58 GB olur ve bu, yükleme tamamlanır tamamlanmaz serbest bırakılır.

       > [!IMPORTANT]
       > Bu konum, ilk yüklemenizde ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, indirme önbelleğini taşımak için [komut satırı parametrelerini kullanmanız](use-command-line-parameters-to-install-visual-studio.md) gerekir.

1. **Paylaşılan bileşenler, Araçlar ve SDK** 'lar bölümünde, "önbelleği indirme" bölümünde seçtiğiniz sürücünün aynısını kullandığını unutmayın. \Microsoft\VisualStudio\Shared Directory, Visual Studio 'nun yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depoladığını gösterir. SDK 'lar ve araçlar bu dizinde da depolanır.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
