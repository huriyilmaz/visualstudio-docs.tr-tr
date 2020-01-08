---
title: Yükleme konumlarını seçme
description: Sistem sürücünüzdeki yükleme ayak izini Visual Studio'nun konumunu indirme önbelleğini, paylaşılan bileşenler, SDK'ları ve araçları farklı sürücülere değiştirerek azaltmak öğrenin. Örneğin, bazı dosyaları C sürücüsünden D sürücüsüne taşıyın.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3ea0651ee1cfde14d5ef7b422095707d8f81cb2f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590156"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Visual Studio 'da yükleme konumlarını seçme

::: moniker range="vs-2019"

Bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio 'nun yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleğini, paylaşılan bileşenler, SDK'lar ve Araçlar dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

**Sürüm 15,7 ' de yeni**: bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio 'nun yükleme ayak izini azaltabilirsiniz. Özellikle, indirme önbelleğini, paylaşılan bileşenler, SDK'lar ve Araçlar dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

   > [!NOTE]
   > Bazı araçlar ve bunlar yüklenebileceği ile ilgili farklı kurallara sahip bir SDK'ları vardır. Başka bir konum seçin bile gibi araçları ve SDK'lar sistem sürücünüzde yüklenir.

Başlamaya hazır mısınız? İşte nasıl.

::: moniker range="vs-2017"

1. Visual Studio'yu yüklediğinizde seçin **yükleme konumlarını** sekmesi.

   ![Visual Studio 2017-yükleme konumunu seçin](media/vs-installation-locations.png "Yükleme konumunu seçin.")

1. İçinde **Visual Studio IDE** bölümünde, varsayılanı kabul edin. Visual Studio temel ürünü yükler ve Visual Studio'nun bu sürümüne özgü dosyaları içerir.

   ![Yükleme konumları sekmesinin Visual Studio IDE bölümü](media/vs-installation-locations-ide.png "Yükleme konumu sekmesinin Visual Studio IDE bölümü için varsayılanı kabul edin.")

   > [!TIP]
   > Sistem sürücünüzdeki bir katı hal sürücüsü (SSD) ise, sistem sürücünüzde varsayılan konumu kabul etmenizi öneririz. Nedeni nedir? Visual Studio ile geliştirme yaptığınızda, okuma ve disk g/ç etkinliği artıran çok sayıda dosya, için yazma. Yükü işlemek için hızlı sürücünüze seçmek idealdir.

1. İçinde **indirme önbelleğini** bölümünde, indirme önbelleğini Tut ve kendi dosyalarını depolamak istediğiniz yere karar istediğinize karar verin.

     ![Yükleme konumları sekmesinin önbellek indirme bölümü](media/vs-installation-locations-cache.png "Yükleme sonrasında indirme önbelleğinin tutulup tutulmayacağını seçin ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. İşaretleyin veya işaretini kaldırın **yüklemeden sonra indirme önbelleğini tut**.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem kalmaz etkileyebilir veya önceki yüklemelerinden dosyaları silin.

    1. Yükleme dosyaları ve indirme önbelleğini bildirimlerinden depolamak istediğiniz sürücüyü belirtin.

        "C++ ile masaüstü geliştirme" iş yükünü seçin, örneğin, geçici olarak gereken boyut 1.58 yüklemesi tamamlandıktan hemen sonra serbest bırakılır sistem sürücüsünde GB'dir.

       > [!IMPORTANT]
       > Bu konum, ilk yükleme ile ayarlanır ve yükleyicisi kullanıcı arabirimini daha sonra değiştirilemez. Bunun yerine, şunları yapmalısınız [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md) indirme önbelleğini taşınır.

1. İçinde **paylaşılan bileşenler, Araçlar ve SDK'lar** bölümünde, yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depolamak istediğiniz sürücüyü belirtin. SDK'lar ve araçlar da bu dizinde depolanır.

   ![Yükleme konumları sekmesinin paylaşılan bileşenler, Araçlar ve SDK 'lar bölümü](media/vs-installation-locations-shared.png "Paylaşılan bileşenleri, araçları ve SDK 'Ları depolamak istediğiniz konumu belirtin.")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu yüklediğinizde seçin **yükleme konumlarını** sekmesi.

   ![Visual Studio 2019-yükleme konumunu seçin](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin.")

1. İçinde **Visual Studio IDE** bölümünde, varsayılanı kabul edin. Visual Studio temel ürünü yükler ve Visual Studio'nun bu sürümüne özgü dosyaları içerir.

   > [!TIP]
   > Sistem sürücünüzdeki bir katı hal sürücüsü (SSD) ise, sistem sürücünüzde varsayılan konumu kabul etmenizi öneririz. Nedeni nedir? Visual Studio ile geliştirme yaptığınızda, okuma ve disk g/ç etkinliği artıran çok sayıda dosya, için yazma. Yükü işlemek için hızlı sürücünüze seçmek idealdir.

1. İçinde **indirme önbelleğini** bölümünde, indirme önbelleğini Tut ve kendi dosyalarını depolamak istediğiniz yere karar istediğinize karar verin.

    * İşaretleyin veya işaretini kaldırın **yüklemeden sonra indirme önbelleğini tut**.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem kalmaz etkileyebilir veya önceki yüklemelerinden dosyaları silin.

    * Yükleme dosyaları ve indirme önbelleğini bildirimlerinden depolamak istediğiniz sürücüyü belirtin.

        "C++ ile masaüstü geliştirme" iş yükünü seçin, örneğin, geçici olarak gereken boyut 1.58 yüklemesi tamamlandıktan hemen sonra serbest bırakılır sistem sürücüsünde GB'dir.

       > [!IMPORTANT]
       > Bu konum, ilk yükleme ile ayarlanır ve yükleyicisi kullanıcı arabirimini daha sonra değiştirilemez. Bunun yerine, şunları yapmalısınız [komut satırı parametrelerini](use-command-line-parameters-to-install-visual-studio.md) indirme önbelleğini taşınır.

1. **Paylaşılan bileşenler, Araçlar ve SDK** 'lar bölümünde, "önbelleği indirme" bölümünde seçtiğiniz sürücünün aynısını kullandığını unutmayın. \Microsoft\VisualStudio\Shared Directory, Visual Studio 'nun yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depoladığını gösterir. SDK'lar ve araçlar da bu dizinde depolanır.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
