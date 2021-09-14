---
title: Yükleme yapılandırmasını içeri veya dışarı aktarma
titleSuffix: ''
description: Yükleme yapılandırmanızı başkalarla paylaşmak için bir .vsconfig dosyasına aktarmayı ve kopyalama için bunu içeri aktarmayı öğrenin.
ms.date: 05/18/2019
ms.topic: how-to
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda4d25c164a91614c35b6cb3f2622235bbbb02a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627068"
---
# <a name="import-or-export-installation-configurations"></a>Yükleme yapılandırmasını içeri veya dışarı aktarma

Yükleme yapılandırma Visual Studio tüm kuruluş genelinde yapılandırmayı yapılandırabilirsiniz. Bunu yapmak için, iş yükü ve bileşen bilgilerini bir .vsconfig dosyasına dışarı aktararak Visual Studio gerekir. Ardından yapılandırmayı yeni veya var olan yüklemelere aktararak başkalarını da paylaşabilirsiniz.

Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

> [!NOTE]
> Bu işlevsellik yalnızca 2017 Visual Studio 15.9 ve sonraki sürümlerde kullanılabilir.

::: moniker-end

## <a name="export-a-configuration"></a>Yapılandırmayı dışarı aktarma

Yükleme yapılandırma dosyasını daha önce yüklenmiş bir Visual Studio örneğinden veya şu anda yüklemekte olduğunu bir örnekten dışarı aktarmayı seçebilirsiniz.

1. Dosyayı Visual Studio Yükleyicisi.

1. Ürün kartında Diğer düğmesini **ve** ardından Yapılandırmayı dışarı **aktar'ı seçin.**

   ![Yapılandırmayı ürün yükleyicisinde ürün kartından Visual Studio aktarma](../install/media/vs-2019/vs-installer-export-config.png)

1. .vsconfig dosyanızı kaydetmek istediğiniz konuma gidin veya yazın ve ardından Ayrıntıları gözden **geçir'i seçin.**

   ![Yapılandırmayı Visual Studio dışarı aktarma](../install/media/vs-2019/export-configuration-confirmation.png)

1. istediğiniz iş yüklerinin ve bileşenlerin olduğundan emin olun ve dışarı aktar'ı **seçin.**

## <a name="import-a-configuration"></a>Yapılandırmayı içeri aktarma

Bir yükleme yapılandırma dosyasını içeri aktarmaya hazırsanız aşağıdaki adımları izleyin.

1. Dosyayı Visual Studio Yükleyicisi.

1. Ürün kartında Diğer düğmesini ve ardından **Yapılandırmayı** içeri **aktar'ı seçin.**

1. İçeri aktarmasını istediğiniz .vsconfig dosyasını bulun ve ardından Ayrıntıları gözden **geçir'i seçin.**

1. istediğiniz iş yüklerinin ve bileşenlerin olduğundan emin olun ve Kapat'ı **seçin.**

::: moniker range=">=vs-2019"

## <a name="automatically-install-missing-components"></a>Eksik bileşenleri otomatik olarak yükleme

**Visual Studio 2019'daki** yeni sürümü: Çözüm kök dizininize bir .vsconfig dosyası kaydedecek ve ardından bir çözüm Visual Studio hangi bileşenlerin eksik olduğunu otomatik olarak algılar ve bunları yüklemenizi istenir.

![Çözüm Gezgini ek bileşenler önerir](../install/media/vs-2019/solution-explorer-config-file.png)

Ayrıca, bir .vsconfig dosyasını dosyanın sağ tarafından Çözüm Gezgini.

1. Çözüm dosyanıza sağ tıklayın.

1. Yükleme **Yapılandırma Dosyası** > **Ekle'yi seçin.**

1. .vsconfig dosyasını kaydetmek istediğiniz konumu onaylayın ve ardından Ayrıntıları gözden **geçir'i seçin.**

1. istediğiniz iş yüklerinin ve bileşenlerin olduğundan emin olun ve dışarı aktar'ı **seçin.**

::: moniker-end

> [!NOTE]
> Daha fazla bilgi için [.vsconfig ile Visual Studio yapılandırma blog gönderisi'ne](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) bakın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Ağ yüklemesi oluşturma Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Ağ tabanlı yüklemesini güncelleştirme Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Kurumsal dağıtımlar için varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md)
