---
title: Deneysel örnek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699035"
---
# <a name="the-experimental-instance"></a>Deneysel Örnek
Visual Studio geliştirme ortamınızı, onu değiştirebilen test edilmemiş uygulamalardan korumak için, VSSDK, denemek için kullanabileceğiniz bir deneysel alan sağlar. Visual Studio 'Yu her zamanki gibi kullanarak yeni uygulamalar geliştirirsiniz, ancak bunları bu deneysel örneği kullanarak çalıştırırsınız.

 VSıX paketi olan her uygulama, hata ayıklama modunda Visual Studio Deneysel örneğini başlatır.

 Visual Studio 'nun Deneysel örneğini belirli bir çözüm dışında başlatmak istiyorsanız, komut penceresinde aşağıdaki komutu çalıştırın:

 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/rootsuffix exp

> [!NOTE]
> Deneysel örnek, ve düğümleri altında kayıt defterine yazılır `<version number>Exp` `<version number>Exp_Config` . Örneğin, Visual Studio 2015 Deneysel kayıt defteri alanı
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Genişletirken, uzantınızı deneysel örnekte çalıştırmanızı öneririz. Uzantıyı dağıttığınızda, geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için bkz. [VSPackages kaydetme](../extensibility/internals/registering-vspackages.md).
