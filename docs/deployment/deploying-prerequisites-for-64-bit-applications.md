---
title: 64 bit Uygulamalar için Önkoşulları Dağıtma | Microsoft Docs
description: 64 bit platformlarda uygulama dağıtımının önkoşulları ClickOnce kullanabileceğiniz yeniden dağıtılabilirler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 91209a76acc754a900bfc88d5d488f0b4729703121d1125abc9f25990ca1c9c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435574"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>64 bit uygulamalar için dağıtım önkoşulları
ClickOnce dağıtımı, 64 bit platformlarda uygulama yüklemesini destekler. Hedef platformlar 32 bit platformlar için **x86,** **AMD64** ve EM64T yönerge kümelerini destekleyen makineler için x64 ve 64 bit Itanium işlemcisi için **Itanium'dır.**

## <a name="prerequisites"></a>Önkoşullar
 Aşağıdaki tabloda, 64 bit uygulama yüklemesi için önkoşul olarak kullanabileceğiniz yeniden dağıtılabilirler listelemektedir.

 64 bit bileşenleri olmayan bir önkoşul seçersiniz, seçilen paketlerin 64 bit platform için kullanılabilir olmadığını belirten bir uyarıyla karşınız olabilir.

| Redistributable | x64 desteği | IA64 desteği |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Yes | Hayır |
| Visual C++ 2010 Çalışma Zamanı Kitaplıkları (IA64) | Hayır | Yes |
| Visual C++ 2010 Çalışma Zamanı Kitaplıkları (x64) | Yes | Hayır |
| Microsoft .NET Framework 4 (x86 ve x64) | Yes | |
| Microsoft .NET Framework 4 İstemci Profili (x86 ve x64) | Yes | |

## <a name="see-also"></a>Ayrıca bkz.
- [Uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md)
- [Nasıl kurulur: Bir uygulamayla önkoşulları ClickOnce yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64 bit uygulamalar](/dotnet/framework/64-bit-apps)