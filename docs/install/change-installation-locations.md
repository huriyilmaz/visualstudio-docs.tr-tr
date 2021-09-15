---
title: Yükleme konumlarını seçme
description: İndirme önbelleğinin, paylaşılan bileşenlerin, VISUAL STUDIO ve araçların konumunu farklı sürücülere değiştirerek sistem sürücünize yükleme ayak izini azaltmayı öğrenin. Örneğin, bazı dosyaları C sürücüsünden D sürücüsüne taşı.
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: be2c18e531af3a0aa6dd059206ce81db7734ab08
ms.sourcegitcommit: 559c662b2d60048300b76ea6ed3defaa2a259492
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779589"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Visual Studio'de yükleme konumlarını seçin

::: moniker range=">=vs-2022"

Bazı dosyalarının konumunu değiştirerek Visual Studio disklerin yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği ve paylaşılan  bileşenler, araçlar ve **SDK'lar için farklı bir konum kullanabilirsiniz.**

::: moniker-end

::: moniker range="vs-2019"

Bazı dosyalarının konumunu değiştirerek Visual Studio sürücüye yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK'lar ve araç dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

**Sürüm 15.7'de** yeni: Bazı dosyalarının konumunu değiştirerek Visual Studio'nin yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK'lar ve araç dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Yüklen onlarda farklı kurallara sahip olan bazı araçlar ve SDK'ler vardır. Başka bir konum seçmenize rağmen bu tür araçlar ve SDK'lar sistem sürücünize yüklenir.

::: moniker-end

Başlamaya hazır mısınız? Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

1. Yükleme konumlarını Visual Studio yükleme **konumları sekmesini** seçin.

   ![Uygulamanın Yükleme konumları sekmesini gösteren Visual Studio Yükleyicisi.](media/vs-installation-locations.png "Yükleme konumunu seçin.")

1. IDE **Visual Studio** varsayılanı kabul edin. Visual Studio, temel ürünü yüker ve bu sürümüne özgü dosyaları Visual Studio.

   ![Uygulamanın Visual Studio yükleme konumları sekmesinin IDE Visual Studio Yükleyicisi.](media/vs-installation-locations-ide.png "Yüklemeler Konumu sekmesinin Visual Studio IDE bölümü için varsayılan değeri kabul edin.")

   > [!TIP]
   > Sistem sürücüniz bir katı hal sürücüsü (SSD) ise, sistem sürücüde varsayılan konumu kabul etmenizi öneririz. Bunun nedeni nedir? Yeni bir Visual Studio, birçok dosyadan okuma ve yazma ile disk I/O etkinliğini artırır. En iyisi yükü işlemek için en hızlı sürücüyü seçmektir.

1. Önbelleği **indir bölümünde,** indirme önbelleğini tutmak istediğinize karar verin ve ardından dosyalarını nerede depolamak istediğinize karar verin.

     ![Uygulamanın Yükleme konumları sekmesinin Önbelleği indir bölümünün ekran Visual Studio Yükleyicisi.](media/vs-installation-locations-cache.png "Yüklemeden sonra indirme önbelleğinin tut olup olmadığını seçin ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. Yüklemeden sonra İndirme **önbelleğini tut'un işaretini kaldırın veya işaretleyin.**

       İndirme önbelleğini tutmama kararınız varsa konum yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

    1. Yükleme dosyalarını ve bildirimlerini indirme önbelleğinden depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçersiniz, sistem sürücünüzde geçici olarak gereken boyut 1,58 GB'tır ve yükleme tamamlandıktan hemen sonra serbest bırak çıkar.

       > [!IMPORTANT]
       > Bu konum ilk yüklemeniz ile ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, indirme [önbelleğini taşımak için komut](use-command-line-parameters-to-install-visual-studio.md) satırı parametrelerini kullanabilirsiniz.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, yüklemelerde yan yana paylaşılan dosyaları depolamak istediğiniz sürücüyü Visual Studio belirtin. SDK'ler ve araçlar da bu dizinde depolanır.

   ![Yükleme konumları sekmesinin Paylaşılan bileşenler, araçlar ve SDK'lar bölümünün ekran Visual Studio Yükleyicisi.](media/vs-installation-locations-shared.png "Paylaşılan bileşenleri, araçları ve SDK'leri depolamak istediğiniz konumu belirtin.")

::: moniker-end

::: moniker range="vs-2019"

1. Yükleme konumlarını Visual Studio yükleme **konumları sekmesini** seçin.

   ![Uygulamanın Yükleme konumları sekmesini gösteren Visual Studio Yükleyicisi.](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin.")

1. IDE **Visual Studio** varsayılanı kabul edin. Visual Studio, temel ürünü yüker ve bu sürümüne özgü dosyaları Visual Studio.

   > [!TIP]
   > Sistem sürücüniz bir katı hal sürücüsü (SSD) ise, sistem sürücüde varsayılan konumu kabul etmenizi öneririz. Bunun nedeni nedir? Yeni bir Visual Studio, birçok dosyadan okuma ve yazma ile disk I/O etkinliğini artırır. En iyisi yükü işlemek için en hızlı sürücüyü seçmektir.

1. Önbelleği **indir bölümünde,** indirme önbelleğini tutmak istediğinize karar verin ve ardından dosyalarını nerede depolamak istediğinize karar verin.

    * Yüklemeden sonra İndirme **önbelleğini tut'un işaretini kaldırın veya işaretleyin.**

       İndirme önbelleğini tutmama kararınız varsa konum yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

    * Yükleme dosyalarını ve bildirimlerini indirme önbelleğinden depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçersiniz, sistem sürücünüzde geçici olarak gereken boyut 1,58 GB'tır ve yükleme tamamlandıktan hemen sonra serbest bırak çıkar.

       > [!IMPORTANT]
       > Bu konum ilk yüklemeniz ile ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, indirme [önbelleğini taşımak için komut](use-command-line-parameters-to-install-visual-studio.md) satırı parametrelerini kullanabilirsiniz.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, "Önbelleği indir" bölümünde seçtiğiniz sürücüyü kullandığını unutmayın. \Microsoft\VisualStudio\Shared dizini, Visual Studio tarafından paylaşılan dosyaları yüklemelerde yan yana depolar Visual Studio dizindir. SDK'ler ve araçlar da bu dizinde depolanır.

::: moniker-end

::: moniker range=">=vs-2022"

1. Yükleme konumlarını Visual Studio yükleme **konumları sekmesini** seçin.

   :::image type="content" source="media/vs-2022/vs-installer-installation-locations-cplusplus-workload.png" border="false" alt-text="Uygulamanın Yükleme konumları sekmesini gösteren Visual Studio Yükleyicisi.":::

1. IDE **Visual Studio** varsayılan yolu kabul edin. Visual Studio, temel ürünü ve bu sürümüne özgü dosyaları Visual Studio.

   > [!TIP]
   > Sistem sürücüniz bir katı hal sürücüsü (SSD) ise, çekirdek ürünü sistem sürücünde tutmanızı öneririz. Bunun nedeni nedir? Yeni bir Visual Studio, birçok dosyadan okuma ve yazma ile disk I/O etkinliğini artırır. En iyisi yükü işlemek için en hızlı sürücüyü seçmektir.

   > [!IMPORTANT]
   > Farklı bir konum seçerek yalnızca yeni bir konum Visual Studio. Zaten yüklemiş ve konumu değiştirmek istiyorsanız, uygulamayı kaldırıp Visual Studio yüklemeniz gerekir.

1. Önbelleği **indir bölümünde,** indirme önbelleğini tutmak isteyip isteyip istemediklerine ve saklamak istediğinize, dosyalarını nerede depolamak istediğinize karar verin.

    * Yüklemeden sonra İndirme **önbelleğini tut'un işaretini kaldırın veya işaretleyin.**

      İndirme önbelleğini tutmama kararınız varsa, indirme önbelleği konumu yalnızca geçici olarak kullanılır. Bu eylem, önceki yüklemelerden dosyaları etkilemez veya silmez.

      Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçersiniz, indirme önbelleği konumu için geçici olarak gereken boyut 2,11 GB'tır. Yükleme tamamlandıktan hemen sonra indirilen önbellek dosyaları kaldırılır ve yalnızca paket meta verileri bırakılır.

    * Yükleme dosyalarını ve bildirimlerini indirme önbelleğinden depolamak istediğiniz sürücü de dahil olmak üzere klasör yolunu belirtin.

   > [!IMPORTANT]
   > Farklı bir konum seçerek yalnızca yeni bir konum Visual Studio. Zaten yüklemiş ve konumu değiştirmek istiyorsanız, uygulamayı kaldırıp Visual Studio yüklemeniz gerekir.

1. Paylaşılan **bileşenler, araçlar ve SDK'lar** bölümünde, yüklemelerde yan yana paylaşılan dosyaları depolamak istediğiniz Visual Studio seçin. SDK'ler ve araçlar da bu dizinde depolanır.

   > [!IMPORTANT]
   > Daha önce bilgisayarınızda Visual Studio yüklemiş olursanız Paylaşılan bileşenler, araçlar ve SDK'lar yolunu değiştiremezsiniz ve bu yol gri görünür.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
