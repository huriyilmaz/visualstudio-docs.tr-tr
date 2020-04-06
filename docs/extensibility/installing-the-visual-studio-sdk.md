---
title: Visual Studio SDK kurulumu | Microsoft Dokümanlar
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710342"
---
# <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK’yı Yükleme

Visual Studio SDK (Yazılım Geliştirme Kiti) Visual Studio kurulumu isteğe bağlı bir özelliktir. VS SDK'yı daha sonra da yükleyebilirsiniz.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Visual Studio SDK'yı Visual Studio yüklemesinin bir parçası olarak yükleyin

Vs SDK'yı Visual Studio yüklemenize dahil etmek için **Visual Studio uzantısı geliştirme** iş yükünü Diğer Araç **Setleri'nin**altına yükleyin. Bu iş yükü Visual Studio SDK ve gerekli ön koşulları yükler. **Özet** görünümünden bileşenleri seçerek veya seçerek yüklemeyi daha fazla ayarlayabilirsiniz.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Visual Studio'yu yükledikten sonra Visual Studio SDK'yı yükleyin

Visual Studio yüklemenizi tamamladıktan sonra Visual Studio SDK'yı yüklemek için Visual Studio yükleyicisini yeniden çalıştırın ve **Visual Studio uzantısı geliştirme** iş yükünü seçin.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Visual Studio SDK'yı bir çözümden yükleyin

VS SDK'yı yüklemeden genişletilebilirlik projesiyle bir çözüm açarsanız, **Visual Studio uzantısı geliştirme** iş yükünü yüklemek için Eksik Özellik **Yükle** iletişim kutusu tarafından istenir:

![Uzantı geliştirmeyi yükleme](../extensibility/media/install-extension-development.png "Uzantı geliştirmeyi yükleme")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Visual Studio SDK komut satırından yükleyin

Herhangi bir Visual Studio iş yükü veya bileşeninde olduğu gibi, **Visual Studio uzantısı geliştirme** iş yükünü (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) komut satırından yükleyebilirsiniz. Bkz. [Visual Studio'yu yüklemek için](../install/use-command-line-parameters-to-install-visual-studio.md) uygun komut satırı anahtarları ve iş yükünü veya bileşen tanımlayıcılarını belirlemeye ilişkin genel yönergeler için komut satırı parametrelerini kullanın.

Visual Studio'nun yüklü sürümüyle eşleşen Visual Studio yükleyicisini kullanmanız gerektiğini unutmayın. Örneğin, bilgisayarınızda Visual Studio Enterprise yüklüyse, Visual Studio Enterprise yükleyicisini *(vs_enterprise.exe)* çalıştırmanız gerekir.
