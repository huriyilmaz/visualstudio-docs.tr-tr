---
title: Yükleme konumlarını seçme
description: İndirme önbelleğinin, paylaşılan bileşenlerin, VISUAL STUDIO ve araçların konumunu farklı sürücülere değiştirerek sistem sürücünize yükleme ayak izini azaltmayı öğrenin. Örneğin, bazı dosyaları C sürücüsünden D sürücüsüne taşı.
ms.date: 03/30/2019
ms.custom: acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e780cca2515118b92b71c406368d29424f7017c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307628"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Visual Studio'de yükleme konumlarını seçin

::: moniker range=">=vs-2019"

Bazı dosyalarının konumunu değiştirerek Visual Studio sürücüye yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK'lar ve araç dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

**Sürüm 15.7'de** yeni: Bazı dosyalarının konumunu değiştirerek Visual Studio sistem sürücünize yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK'lar ve araç dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

   > [!NOTE]
   > Yüklen onlarda farklı kurallara sahip olan bazı araçlar ve SDK'ler vardır. Başka bir konum seçmenize rağmen bu tür araçlar ve SDK'lar sistem sürücünize yüklenir.

Başlamaya hazır mısınız? Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

1. Yükleme konumlarını Visual Studio yükleme **konumları sekmesini** seçin.

   ![Visual Studio 2017 - Yükleme konumunu seçin](media/vs-installation-locations.png "Yükleme konumunu seçin.")

1. IDE **Visual Studio** varsayılanı kabul edin. Visual Studio, temel ürünü yüker ve bu sürümüne özgü dosyaları Visual Studio.

   ![Visual Studio Konumları sekmesinin IDE bölümü](media/vs-installation-locations-ide.png "Yüklemeler Konumu sekmesinin Visual Studio IDE bölümü için varsayılan değeri kabul edin.")

   > [!TIP]
   > Sistem sürücüniz bir katı hal sürücüsü (SSD) ise, sistem sürücüde varsayılan konumu kabul etmenizi öneririz. Bunun nedeni nedir? Yeni bir Visual Studio, birçok dosyadan okuma ve yazma ile disk I/O etkinliğini artırır. En iyisi yükü işlemek için en hızlı sürücüyü seçmektir.

1. Önbelleği **indir bölümünde,** indirme önbelleğini tutmak istediğinize karar verin ve ardından dosyalarını nerede depolamak istediğinize karar verin.

     ![Yükleme Konumları sekmesinin Önbelleği İndir bölümü](media/vs-installation-locations-cache.png "Yüklemeden sonra indirme önbelleğinin tut olup olmadığını seçin ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. Yüklemeden sonra İndirme **önbelleğini tut'un işaretini kaldırın veya işaretleyin.**

       İndirme önbelleğini tutmama kararınız varsa konum yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

    1. Yükleme dosyalarını ve bildirimlerini indirme önbelleğinden depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçersiniz, sistem sürücünüzde geçici olarak gereken boyut 1,58 GB'tır ve yükleme tamamlandıktan hemen sonra serbest bırak çıkar.

       > [!IMPORTANT]
       > Bu konum ilk yüklemeniz ile ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, [indirme önbelleğini taşımak için komut](use-command-line-parameters-to-install-visual-studio.md) satırı parametrelerini kullanabilirsiniz.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, yüklemelerde yan yana paylaşılan dosyaları depolamak istediğiniz Visual Studio belirtin. SDK'ler ve araçlar da bu dizinde depolanır.

   ![Yükleme Konumları sekmesinin Paylaşılan Bileşenler, Araçlar ve SDK'lar bölümü](media/vs-installation-locations-shared.png "Paylaşılan bileşenleri, araçları ve SDK'leri depolamak istediğiniz konumu belirtin.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Yükleme konumlarını Visual Studio yükleme **konumları sekmesini** seçin.

   ![Visual Studio 2019 - Yükleme konumunu seçin](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin.")

1. IDE **Visual Studio** varsayılanı kabul edin. Visual Studio, temel ürünü yüker ve bu sürümüne özgü dosyaları Visual Studio.

   > [!TIP]
   > Sistem sürücüniz bir katı hal sürücüsü (SSD) ise, sistem sürücüde varsayılan konumu kabul etmenizi öneririz. Bunun nedeni nedir? Yeni bir Visual Studio, birçok dosyadan okuma ve yazma ile disk I/O etkinliğini artırır. En iyisi yükü işlemek için en hızlı sürücüyü seçmektir.

1. Önbelleği **indir bölümünde,** indirme önbelleğini tutmak istediğinize karar verin ve ardından dosyalarını nerede depolamak istediğinize karar verin.

    * Yüklemeden sonra İndirme **önbelleğini tut'un işaretini kaldırın veya işaretleyin.**

       İndirme önbelleğini tutmama kararınız varsa konum yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

    * Yükleme dosyalarını ve bildirimlerini indirme önbelleğinden depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçersiniz, sistem sürücünüzde geçici olarak gereken boyut 1,58 GB'tır ve yükleme tamamlandıktan hemen sonra serbest bırak çıkar.

       > [!IMPORTANT]
       > Bu konum ilk yüklemeniz ile ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, [indirme önbelleğini taşımak için komut](use-command-line-parameters-to-install-visual-studio.md) satırı parametrelerini kullanabilirsiniz.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, "Önbelleği indir" bölümünde seçtiğiniz sürücüyü kullandığını unutmayın. \Microsoft\VisualStudio\Shared dizini, Visual Studio yüklemelerde yan yana paylaşılan dosyaları depolar Visual Studio dizindir. SDK'ler ve araçlar da bu dizinde depolanır.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
