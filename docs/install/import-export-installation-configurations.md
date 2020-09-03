---
title: Yükleme yapılandırmasını içeri veya dışarı aktarma
titleSuffix: ''
description: Yükleme yapılandırmanızı başkalarıyla paylaşmak için bir. vsconfig dosyasına aktarmayı ve kopyalamak için nasıl içeri aktarılacağını öğrenin.
ms.date: 05/18/2019
ms.topic: how-to
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
ms.openlocfilehash: 4dcad21ce0a77e18bed0b077f731a509916e9e63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418827"
---
# <a name="import-or-export-installation-configurations"></a>Yükleme yapılandırmasını içeri veya dışarı aktarma

Visual Studio 'Yu, yükleme yapılandırma dosyalarıyla kuruluşunuzda yapılandırabilirsiniz. Bunu yapmak için, Visual Studio yükleyicisi 'ni kullanarak iş yükünü ve bileşen bilgilerini bir. vsconfig dosyasına dışarı aktarmanız yeterlidir. Daha sonra yapılandırmayı yeni veya var olan yüklemelere aktarabilir ve başkalarıyla de paylaşabilirsiniz.

Aşağıdaki adımları uygulayın:

::: moniker range="vs-2017"

> [!NOTE]
> Bu işlevsellik yalnızca Visual Studio 2017 sürüm 15,9 ve üzeri sürümlerde kullanılabilir.

::: moniker-end

## <a name="export-a-configuration"></a>Yapılandırmayı dışarı aktar

Bir yükleme yapılandırma dosyasını, daha önce yüklenmiş bir Visual Studio örneğinden ya da o anda yüklemekte olduğunuz bir yüklemeden dışarı aktarmayı seçebilirsiniz.

1. Visual Studio Yükleyicisi açın.

1. Ürün kartında, **daha fazla** düğmesini seçin ve ardından **yapılandırmayı dışarı aktar**' ı seçin.

   ![Visual Studio yükleyicisindeki ürün kartından yapılandırmayı dışarı aktarma](../install/media/vs-2019/vs-installer-export-config.png)

1. . Vsconfig dosyanızı kaydetmek istediğiniz konumu bulup yazın ve ardından **ayrıntıları gözden geçir**' i seçin.

   ![Visual Studio yükleyicisinden yapılandırmayı dışarı aktarma](../install/media/vs-2019/export-configuration-confirmation.png)

1. İstediğiniz iş yüklerine ve bileşenlere sahip olduğunuzdan emin olun ve **dışarı aktar**' ı seçin.

## <a name="import-a-configuration"></a>Yapılandırma içeri aktar

Bir yükleme yapılandırma dosyasını içeri aktarmaya hazırsanız, bu adımları izleyin.

1. Visual Studio Yükleyicisi açın.

1. Ürün kartında, **daha fazla** düğmesini seçin ve ardından **yapılandırmayı içeri aktar**' ı seçin.

1. İçeri aktarmak istediğiniz. vsconfig dosyasını bulun ve ardından **ayrıntıları gözden geçir**' i seçin.

1. İstediğiniz iş yüklerine ve bileşenlere sahip olduğunuzdan emin olun ve ardından **Kapat**' ı seçin.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Eksik bileşenleri otomatik olarak yükler

**Visual studio 2019 ' de yeni**: çözüm kök Dizininize bir. vsconfig dosyası kaydettiğinizde ve sonra bir çözüm açtığınızda, Visual Studio hangi bileşenlerin eksik olduğunu otomatik olarak algılar ve bunları yüklemenizi ister.

![Çözüm Gezgini ek bileşenler önerir](../install/media/vs-2019/solution-explorer-config-file.png)

Ayrıca, Çözüm Gezgini doğrudan bir. vsconfig dosyası da oluşturabilirsiniz.

1. Çözüm dosyanıza sağ tıklayın.

1. **Add** > **Yükleme yapılandırma dosyası**Ekle ' yi seçin.

1. . Vsconfig dosyasını kaydetmek istediğiniz konumu onaylayın ve sonra **ayrıntıları gözden geçir**' i seçin.

1. İstediğiniz iş yüklerine ve bileşenlere sahip olduğunuzdan emin olun ve **dışarı aktar**' ı seçin.

::: moniker-end

> [!NOTE]
> Daha fazla bilgi için bkz [. Visual Studio 'yu kuruluşunuzda yapılandırma. vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) blog gönderisi.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio 'nun ağ yüklemesi oluşturma](create-a-network-installation-of-visual-studio.md)
* [Visual Studio 'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
* [Visual Studio dağıtımlarına yönelik güncelleştirmeleri denetleme](controlling-updates-to-visual-studio-deployments.md)
* [Kurumsal dağıtımlar için Varsayılanları Ayarla](set-defaults-for-enterprise-deployments.md)
