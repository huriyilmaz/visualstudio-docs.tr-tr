---
title: Deneysel örnek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ee3c1ef0aed082a0e4e0fb519c744fda376fc8e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64791285"
---
# <a name="the-experimental-instance"></a>Deneysel Örnek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio geliştirme ortamınızı, onu değiştirebilen test edilmemiş uygulamalardan korumak için, VSSDK, denemek için kullanabileceğiniz bir deneysel alan sağlar. Visual Studio 'Yu her zamanki gibi kullanarak yeni uygulamalar geliştirirsiniz, ancak bunları bu deneysel örneği kullanarak çalıştırırsınız.  
  
 VSıX paketi olan her uygulama, hata ayıklama modunda Visual Studio Deneysel örneğini başlatır.  
  
 Visual Studio 'nun Deneysel örneğini belirli bir çözüm dışında başlatmak istiyorsanız, komut penceresinde aşağıdaki komutu çalıştırın:  
  
 " *\<Visual studio installation path>* \Common7\IDE\devenv.exe"/rootsuffix exp  
  
> [!NOTE]
> Deneysel örnek, ve düğümleri altında kayıt defterine yazılır `<version number>Exp` `<version number>Exp_Config` . Örneğin, Visual Studio 2015 Deneysel kayıt defteri alanı  
>   
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` ve `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Genişletirken, uzantınızı deneysel örnekte çalıştırmanızı öneririz. Uzantıyı dağıttığınızda, geliştirme örneğinde çalışır. Uygulamaları kaydetme hakkında daha fazla bilgi için bkz. [VSPackages kaydetme](../extensibility/internals/registering-vspackages.md).
