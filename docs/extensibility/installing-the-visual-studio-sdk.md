---
title: Visual Studio SDK 'sını yükleme | Microsoft Docs
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905549"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme

Visual Studio SDK (yazılım geliştirme seti), Visual Studio kurulumunda isteğe bağlı bir özelliktir. VS SDK ' yı daha sonra da yükleyebilirsiniz.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio SDK 'sını bir Visual Studio yüklemesinin parçası olarak yükleme

Visual Studio yüklemenize VS SDK eklemek için, **Visual Studio uzantısı geliştirme** Iş yükünü **diğer araç kümeleri**altına yüklemeniz gerekir. Bu iş yükü, Visual Studio SDK 'sını ve gerekli önkoşulları yükler. **Özet** görünümünden bileşen seçerek veya seçimi kaldırarak yüklemeyi daha da ayarlayabilirsiniz.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio 'Yu yükledikten sonra Visual Studio SDK 'sını yükleme

Visual Studio yüklemesini tamamladıktan sonra Visual Studio SDK 'sını yüklemek için Visual Studio yükleyicisi 'ni yeniden çalıştırın ve **Visual Studio uzantısı geliştirme** iş yükünü seçin.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Bir çözümden Visual Studio SDK 'sını yükler

Daha önce VS SDK 'Yı yüklemeden genişletilebilirlik projesiyle bir çözüm açarsanız, **Visual Studio uzantısı geliştirme** iş yükünü yüklemek için eksik bir **özellik** iletişim kutusu istenir:

![Uzantı geliştirmeyi yükler](../extensibility/media/install-extension-development.png "Uzantı geliştirmeyi yükler")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Komut satırından Visual Studio SDK 'sını yükler

Visual Studio iş yükünde veya bileşeninde olduğu gibi, **Visual Studio uzantısı geliştirme** iş yükünü (ID: Microsoft. VisualStudio. Workload. VisualStudioExtension) komut satırından da yükleyebilirsiniz. İlgili komut satırı anahtarları ve iş yükü veya bileşen tanımlayıcılarını belirleme hakkında genel yönergeler için [Visual Studio 'yu yüklemek üzere komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) konusuna bakın.

Visual Studio 'nun yüklü sürümü ile eşleşen Visual Studio yükleyicisini kullanmanız gerektiğini unutmayın. Örneğin, bilgisayarınızda yüklü Visual Studio Enterprise yüklüyse, Visual Studio Enterprise yükleyiciyi (*vs_enterprise.exe*) çalıştırmanız gerekir.
