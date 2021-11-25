---
title: Yükleme konumlarını seçme
description: indirme önbelleğinin, paylaşılan bileşenlerin, sdk 'ların ve araçların konumunu farklı sürücülere değiştirerek sistem sürücünüzdeki Visual Studio yükleme parmak izini nasıl azaltacağınızı öğrenin. Örneğin, bazı dosyaları C sürücüsünden D sürücüsüne taşıyın.
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
ms.openlocfilehash: e242542b62546a6a53f142ecced26edefe626fb5
ms.sourcegitcommit: 5af130d3ff64b71d415819e42f4f2efb2ae36a6a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "133117502"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Visual Studio içinde yükleme konumlarını seçin

::: moniker range=">=vs-2022"

bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio yükleme parmak izini azaltabilirsiniz. Özellikle, **indirme önbelleği** ve **paylaşılan bileşenler, Araçlar ve SDK**'lar için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2019"

bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio yükleme parmak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK 'lar ve araçlar dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

**sürüm 15,7 ' deki yenilikler**: bazı dosyalarının konumunu değiştirerek sistem sürücünüzdeki Visual Studio yükleme parmak izini azaltabilirsiniz. Özellikle, indirme önbelleği, paylaşılan bileşenler, SDK 'lar ve araçlar dosyaları için farklı bir konum kullanabilirsiniz.

::: moniker-end

::: moniker range=">=vs-2019"

   > [!NOTE]
   > Yüklenebilecekleri farklı kurallara sahip bazı araçlar ve SDK 'lar vardır. Bu tür araçlar ve SDK 'lar, başka bir konum seçseniz bile sistem sürücünüze yüklenir.

::: moniker-end

Başlamaya hazır mısınız? Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

1. Visual Studio yüklediğinizde, **yükleme konumları** sekmesini seçin.

   ![Visual Studio Yükleyicisi yükleme konumları sekmesini gösteren ekran görüntüsü.](media/vs-installation-locations.png "Yükleme konumunu seçin.")

1. **Visual Studio ıde** bölümünde, varsayılanı kabul edin. Visual Studio çekirdek ürünü yükleyerek Visual Studio bu sürümüne özgü dosyaları içerir.

   ![Visual Studio Yükleyicisi yükleme konumları sekmesinin Visual Studio ıde bölümünün ekran görüntüsü.](media/vs-installation-locations-ide.png "yükleme konumu sekmesinin Visual Studio ıde bölümü için varsayılanı kabul edin.")

   > [!TIP]
   > Sistem sürücünüz bir katı hal sürücüsü (SSD) ise, sistem sürücünüzdeki varsayılan konumu kabul etmenizi öneririz. Neden? Visual Studio ile geliştirirken, disk g/ç etkinliğini artıran çok sayıda dosyayı okur ve buradan yazarsınız. Yükü işlemek için en hızlı sürücüyü seçmeniz önerilir.

1. **Önbelleği indir** bölümünde, indirme önbelleğini tutmak istediğinize karar verin ve sonra dosyalarını nerede saklamak istediğinize karar verin.

     ![Visual Studio Yükleyicisi yükleme konumları sekmesinin indirme önbelleği bölümünün ekran görüntüsü.](media/vs-installation-locations-cache.png "Yükleme sonrasında indirme önbelleğinin tutulup tutulmayacağını seçin ve ardından dosyaları depolamak istediğiniz sürücüyü belirtin.")

    1. **Yükleme sonrasında indirme önbelleğini koru** veya işaretini kaldır.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem önceki yüklemelerin dosyalarını etkilemez veya silmez.

    1. Yükleme önbelleğinden yükleme dosyalarını ve bildirimlerini depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçerseniz, geçici olarak gereken boyut sistem sürücünüzde 1,58 GB olur ve bu, yükleme tamamlanır tamamlanmaz serbest bırakılır.

       > [!IMPORTANT]
       > Bu konum, ilk yüklemenizde ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, indirme önbelleğini taşımak için [komut satırı parametrelerini kullanmanız](use-command-line-parameters-to-install-visual-studio.md) gerekir.

1. **paylaşılan bileşenler, araçlar ve sdk** 'lar bölümünde, yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depolamak istediğiniz sürücüyü belirtin. SDK 'lar ve araçlar bu dizinde da depolanır.

   ![Visual Studio Yükleyicisi yükleme konumları sekmesindeki paylaşılan bileşenler, araçlar ve sdk 'lar bölümünün ekran görüntüsü.](media/vs-installation-locations-shared.png "Paylaşılan bileşenleri, araçları ve SDK 'Ları depolamak istediğiniz konumu belirtin.")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio yüklediğinizde, **yükleme konumları** sekmesini seçin.

   ![Visual Studio Yükleyicisi yükleme konumları sekmesini gösteren ekran görüntüsü.](media/vs-2019/vs-installer-installation-locations.png "Yükleme konumunu seçin.")

1. **Visual Studio ıde** bölümünde, varsayılanı kabul edin. Visual Studio çekirdek ürünü yükleyerek Visual Studio bu sürümüne özgü dosyaları içerir.

   > [!TIP]
   > Sistem sürücünüz bir katı hal sürücüsü (SSD) ise, sistem sürücünüzdeki varsayılan konumu kabul etmenizi öneririz. Neden? Visual Studio ile geliştirirken, disk g/ç etkinliğini artıran çok sayıda dosyayı okur ve buradan yazarsınız. Yükü işlemek için en hızlı sürücüyü seçmeniz önerilir.

1. **Önbelleği indir** bölümünde, indirme önbelleğini tutmak istediğinize karar verin ve sonra dosyalarını nerede saklamak istediğinize karar verin.

    * **Yükleme sonrasında indirme önbelleğini koru** veya işaretini kaldır.

       İndirme önbelleğini tutmamaya karar verirseniz, konum yalnızca geçici olarak kullanılır. Bu eylem önceki yüklemelerin dosyalarını etkilemez veya silmez.

    * Yükleme önbelleğinden yükleme dosyalarını ve bildirimlerini depolamak istediğiniz sürücüyü belirtin.

        Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçerseniz, geçici olarak gereken boyut sistem sürücünüzde 1,58 GB olur ve bu, yükleme tamamlanır tamamlanmaz serbest bırakılır.

       > [!IMPORTANT]
       > Bu konum, ilk yüklemenizde ayarlanır ve daha sonra yükleyici kullanıcı arabiriminden değiştirilemez. Bunun yerine, indirme önbelleğini taşımak için [komut satırı parametrelerini kullanmanız](use-command-line-parameters-to-install-visual-studio.md) gerekir.

1. **Paylaşılan bileşenler, Araçlar ve SDK** 'lar bölümünde, "önbelleği indirme" bölümünde seçtiğiniz sürücünün aynısını kullandığını unutmayın. \microsoft\visualstudio\shared directory, Visual Studio yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depoladığını gösterir. SDK 'lar ve araçlar bu dizinde da depolanır.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio yüklediğinizde, **yükleme konumları** sekmesini seçin.

   :::image type="content" source="media/vs-2022/vs-installer-installation-locations-tab.png" border="false" alt-text="Visual Studio Yükleyicisi yükleme konumları sekmesini gösteren ekran görüntüsü.":::

1. **Visual Studio ıde** bölümünde, varsayılan yolu kabul edin. Visual Studio çekirdek ürünü yüklüyor ve bu Visual Studio sürümüne özgü dosyaları içerir.

   > [!TIP]
   > Sistem sürücünüz bir katı hal sürücüsü (SSD) ise, temel ürünü sistem sürücünüzde tutmanız önerilir. Neden? Visual Studio ile geliştirirken, disk g/ç etkinliğini artıran çok sayıda dosyayı okur ve buradan yazarsınız. Yükü işlemek için en hızlı sürücüyü seçmeniz önerilir.

   > [!IMPORTANT]
   > Yalnızca Visual Studio ilk kez yüklerken farklı bir konum seçebilirsiniz. zaten yüklediyseniz ve konumu değiştirmek istiyorsanız, Visual Studio kaldırıp yeniden yüklemeniz gerekir.

1. **Önbelleği indir** bölümünde, indirme önbelleğini tutmak isteyip istemediğinize ve bu durumda dosyalarını depolamak istediğiniz yere karar verin.

    * **Yükleme sonrasında indirme önbelleğini koru** veya işaretini kaldır.

      İndirme önbelleğini tutmamaya karar verirseniz, indirme önbelleği konumu yalnızca geçici olarak kullanılır. Bu eylem önceki yüklemelerin dosyalarını etkilemez veya silmez.

      Örneğin, "C++ ile masaüstü geliştirme" iş yükünü seçerseniz, indirme önbelleği konumu için geçici olarak gereken boyut 2,11 GB olur. Yükleme tamamlandıktan hemen sonra indirilen önbellek dosyaları kaldırılır ve yalnızca paket meta verileri bırakılır.

    * Yükleme önbelleğinden yükleme dosyalarını ve bildirimleri depolamak istediğiniz sürücü dahil olmak üzere klasör yolunu belirtin.

   > [!IMPORTANT]
   > Yalnızca Visual Studio ilk kez yüklerken farklı bir konum seçebilirsiniz. zaten yüklediyseniz ve konumu değiştirmek istiyorsanız, Visual Studio kaldırıp yeniden yüklemeniz gerekir.

1. **paylaşılan bileşenler, araçlar ve sdk** 'lar bölümünde, yan yana Visual Studio yüklemeleri tarafından paylaşılan dosyaları depolamak istediğiniz klasörü seçin. SDK 'lar ve araçlar bu dizinde da depolanır.

   > [!IMPORTANT]
   > daha önce bilgisayarınıza Visual Studio yüklediyseniz, paylaşılan bileşenleri, araçları ve sdk 'lar yolunu değiştiremeyeceksiniz ve bu işlem gri renkte görünür.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio’yu güncelleştirme](update-visual-studio.md)
* [Visual Studio’yu değiştirme](update-visual-studio.md)
* [Visual Studio'yu kaldırma](uninstall-visual-studio.md)
