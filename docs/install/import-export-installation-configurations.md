---
title: Yükleme yapılandırmasını içeri veya dışarı aktarma
titleSuffix: ''
description: Yükleme yapılandırmanızı başkalarıyla paylaşmak üzere .vsconfig dosyasına nasıl dışa aktarılacağınızı ve klonlamak için nasıl içe aktarılacağınızı öğrenin.
ms.date: 05/18/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 12d22334094b848350d44d245685532fed196389
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114849"
---
# <a name="import-or-export-installation-configurations"></a>Yükleme yapılandırmasını içeri veya dışarı aktarma

Visual Studio'yı yükleme yapılandırma dosyalarıyla kuruluşunuz genelinde yapılandırabilirsiniz. Bunu yapmak için, Visual Studio yükleyicisini kullanarak iş yükünü ve bileşen bilgilerini .vsconfig dosyasına aktarmanız yeterlidir. Daha sonra yapılandırmayı yeni veya varolan yüklemelere aktarabilir ve bunları başkalarıyla da paylaşabilirsiniz.

Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

> [!NOTE]
> Bu işlevsellik yalnızca Visual Studio 2017 sürüm 15.9 ve sonraki sürümlerde kullanılabilir.

::: moniker-end

## <a name="export-a-configuration"></a>Yapılandırmayı dışa aktarma

Bir yükleme yapılandırma dosyasını daha önce yüklenmiş bir Visual Studio örneğinden veya şu anda yüklediğiniz bir dosyadan dışa aktarmayı seçebilirsiniz.

1. Visual Studio Yükleyici'yi açın.

1. Ürün kartında Daha **Fazla** düğmesini seçin ve ardından **Yapılandırmayı Dışa Aktar'ı**seçin.

   ![Visual Studio yükleyicisindeki ürün kartından yapılandırmayı dışa aktarma](../install/media/vs-2019/vs-installer-export-config.png)

1. .vsconfig dosyanızı kaydetmek istediğiniz konuma göz atın veya yazın ve ardından Ayrıntı ayrıntılarını gözden **geçir'i**seçin.

   ![Visual Studio yükleyicisinden yapılandırmayı dışa aktarma](../install/media/vs-2019/export-configuration-confirmation.png)

1. İstediğiniz iş yüklerini ve bileşenlerine sahip olduğundan emin olun ve sonra **Dışa Aktar'ı**seçin.

## <a name="import-a-configuration"></a>Yapılandırma alma

Yükleme yapılandırma dosyası almaya hazır olduğunuzda aşağıdaki adımları izleyin.

1. Visual Studio Yükleyici'yi açın.

1. Ürün kartında Daha **Fazla** düğmesini seçin ve ardından **Yapılandırmayı Aktar'ı**seçin.

1. Almak istediğiniz .vsconfig dosyasını bulun ve ardından **Gözden Geçir ayrıntılarını**seçin.

1. İstediğiniz iş yüklerine ve bileşenlere sahip olduğundan emin olun ve ardından **Kapat'ı**seçin.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Eksik bileşenleri otomatik olarak yükleme

**Visual Studio 2019'da Yeni**: Bir .vsconfig dosyasını çözüm kök dizininize kaydedip bir çözüm açtığınızda Visual Studio otomatik olarak hangi bileşenlerin eksik olduğunu algılar ve bunları yüklemenizi ister.

![Çözüm Gezgini ek bileşenler önerir](../install/media/vs-2019/solution-explorer-config-file.png)

Ayrıca, Solution Explorer'dan bir .vsconfig dosyası da oluşturabilirsiniz.

1. Çözüm dosyanıza sağ tıklayın.

1. **Yükleme Yapılandırma Dosyası** **Ekle'yi** > seçin.

1. .vsconfig dosyasını kaydetmek istediğiniz konumu onaylayın ve ardından **Gözden Geçir ayrıntılarını**seçin.

1. İstediğiniz iş yüklerini ve bileşenlerine sahip olduğundan emin olun ve sonra **Dışa Aktar'ı**seçin.

::: moniker-end

> [!NOTE]
> Daha fazla bilgi için [,.vsconfig blog gönderisiyle kuruluşunuz daki Görsel Stüdyoyu Yapılandır'a](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) bakın.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nun ağ yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md)
* [Visual Studio'nun ağa dayalı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Kurumsal dağıtımlar için varsayılanları ayarlama](set-defaults-for-enterprise-deployments.md)
