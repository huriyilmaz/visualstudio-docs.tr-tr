---
title: Deneysel Örnek | Microsoft Docs
description: Visual Studio SDK'sı tarafından test edilmemiş uygulamaları hata ayıklama modunda çalıştırmak için deneysel bir alan sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 515183771fd4063b20d7ea2ade416d1b84c31cfb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137463"
---
# <a name="the-experimental-instance"></a>Deneysel Örnek
VsSDK, Visual Studio geliştirme ortamınızı değiştirmeyecek test edilmemiş uygulamalardan korumak için deneme yapmak için kullanabileceğiniz deneysel bir alan sağlar. Her zamanki gibi Visual Studio kullanarak yeni uygulamalar geliştirirsiniz, ancak bu deneysel örneği kullanarak bunları çalıştırabilirsiniz.

 VSIX paketi olan her uygulama, Visual Studio hata ayıklama modunda deneysel örneği başlatıyor.

 Belirli bir çözümün dışında Visual Studio örneğini başlatmak için komut penceresinde aşağıdaki komutu çalıştırın:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> Deneysel örnek, ve düğümleri altındaki kayıt `<version number>Exp` defterine `<version number>Exp_Config` yazılır. Örneğin 2015 Visual Studio kayıt defteri alanı şu şekildedir:
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Uzantınızı geliştirme aşamasında deneysel örnekte çalıştırmanızı öneririz. Uzantıyı dağıtınca geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için [bkz. VSPackage'ları Kaydetme.](../extensibility/internals/registering-vspackages.md)
