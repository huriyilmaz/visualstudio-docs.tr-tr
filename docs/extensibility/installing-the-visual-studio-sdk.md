---
title: Visual Studio SDK 'sını yükleme | Microsoft Docs
description: Visual Studio yükleme sırasında da dahil olmak üzere Visual Studio yazılım geliştirme seti 'ni yükleme seçenekleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1f0aeff420a5a043a6f6a9fd3dbfbf4c5975eba1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070236"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme

Visual Studio SDK (yazılım geliştirme seti), Visual Studio kurulum 'da isteğe bağlı bir özelliktir. VS SDK ' yı daha sonra da yükleyebilirsiniz.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio SDK 'sını Visual Studio yüklemesinin parçası olarak yükleme

Visual Studio yüklemenize VS SDK 'yı eklemek için, **Visual Studio uzantısı geliştirme** iş yükünü **diğer araç kümeleri** altına yüklemeniz gerekir. bu iş yükü Visual Studio SDK 'sını ve gerekli önkoşulları yükler. **Özet** görünümünden bileşen seçerek veya seçimi kaldırarak yüklemeyi daha da ayarlayabilirsiniz.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio yükledikten sonra Visual Studio SDK 'sını yükleme

Visual Studio yüklemenizi tamamladıktan sonra Visual Studio SDK 'yı yüklemek için Visual Studio yükleyicisini yeniden çalıştırın ve **Visual Studio uzantısı geliştirme** iş yükünü seçin.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>bir çözümden Visual Studio SDK 'yı yükler

daha önce VS SDK 'yı yüklemeden genişletilebilirlik projesiyle bir çözüm açarsanız, **Visual Studio uzantısı geliştirme** iş yükünü yüklemek için **eksik bir özellik** iletişim kutusu istenir:

![Uzantı geliştirmeyi yükler](../extensibility/media/install-extension-development.png "Uzantı geliştirmeyi yükler")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>komut satırından Visual Studio SDK 'sını yükler

her türlü Visual Studio iş yükünde veya bileşende olduğu gibi, komut satırından **Visual Studio uzantısı geliştirme** iş yükünü (ıd: Microsoft. VisualStudio. workload. VisualStudioExtension) da yükleyebilirsiniz. uygun komut satırı anahtarları ve iş yükü veya bileşen tanımlayıcılarını belirleme hakkında genel yönergeler için [Visual Studio yüklemek üzere komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) konusuna bakın.

Visual Studio yüklü sürümü ile eşleşen Visual Studio yükleyicisini kullanmanız gerektiğini unutmayın. örneğin, bilgisayarınızda yüklü Visual Studio Enterprise yüklüyse, Visual Studio Enterprise yükleyiciyi (*vs_enterprise.exe*) çalıştırmanız gerekir.
