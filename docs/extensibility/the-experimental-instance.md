---
title: Deneysel Örnek | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699035"
---
# <a name="the-experimental-instance"></a>Deneysel Örnek
Visual Studio geliştirme ortamınızı değiştirebilecek test edilmemiş uygulamalardan korumak için VSSDK, deneme yapmak için kullanabileceğiniz deneysel bir alan sağlar. Her zamanki gibi Visual Studio kullanarak yeni uygulamalar geliştirmek, ancak bu deneysel örneği kullanarak çalıştırın.

 VSIX paketi olan her uygulama, Visual Studio deneysel örneğini hata ayıklama modunda başlatıyor.

 Visual Studio'nun deneysel örneğini belirli bir çözümün dışında başlatmak istiyorsanız, komut penceresinde aşağıdaki komutu çalıştırın:

 "*\<Visual studio kurulum yolu>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> Deney örneği, ve `<version number>Exp` `<version number>Exp_Config` düğümler altında kayıt defterine yazılır. Örneğin Visual Studio 2015 deneysel kayıt alanı
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Geliştirme sırasında uzantınızı deneme örneğinde çalıştırmanızı öneririz. Uzantıyı dağıttığınızda, geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için [vspackages kaydettirme'ye](../extensibility/internals/registering-vspackages.md)bakın.
