---
title: Visual Studio SDK 'sını yükleme | Microsoft Docs
description: Visual Studio yükleme sırasında, Visual Studio yazılım geliştirme seti 'ni yükleme seçenekleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 331a219210c990aed2f9601cd1f9b1f0bc5710ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079169"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme

Visual Studio SDK (yazılım geliştirme seti), Visual Studio kurulumunda isteğe bağlı bir özelliktir. VS SDK ' yı daha sonra da yükleyebilirsiniz.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio SDK 'sını bir Visual Studio yüklemesinin parçası olarak yükleme

Visual Studio yüklemenize VS SDK eklemek için, **Visual Studio uzantısı geliştirme** Iş yükünü **diğer araç kümeleri** altına yüklemeniz gerekir. Bu iş yükü, Visual Studio SDK 'sını ve gerekli önkoşulları yükler. **Özet** görünümünden bileşen seçerek veya seçimi kaldırarak yüklemeyi daha da ayarlayabilirsiniz.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio 'Yu yükledikten sonra Visual Studio SDK 'sını yükleme

Visual Studio yüklemesini tamamladıktan sonra Visual Studio SDK 'sını yüklemek için Visual Studio yükleyicisi 'ni yeniden çalıştırın ve **Visual Studio uzantısı geliştirme** iş yükünü seçin.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Bir çözümden Visual Studio SDK 'sını yükler

Daha önce VS SDK 'Yı yüklemeden genişletilebilirlik projesiyle bir çözüm açarsanız, **Visual Studio uzantısı geliştirme** iş yükünü yüklemek için eksik bir **özellik** iletişim kutusu istenir:

![Uzantı geliştirmeyi yükler](../extensibility/media/install-extension-development.png "Uzantı geliştirmeyi yükler")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Komut satırından Visual Studio SDK 'sını yükler

Visual Studio iş yükünde veya bileşeninde olduğu gibi, **Visual Studio uzantısı geliştirme** iş yükünü (ID: Microsoft. VisualStudio. Workload. VisualStudioExtension) komut satırından da yükleyebilirsiniz. İlgili komut satırı anahtarları ve iş yükü veya bileşen tanımlayıcılarını belirleme hakkında genel yönergeler için [Visual Studio 'yu yüklemek üzere komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) konusuna bakın.

Visual Studio 'nun yüklü sürümü ile eşleşen Visual Studio yükleyicisini kullanmanız gerektiğini unutmayın. Örneğin, bilgisayarınızda yüklü Visual Studio Enterprise yüklüyse, Visual Studio Enterprise yükleyiciyi (*vs_enterprise.exe*) çalıştırmanız gerekir.
