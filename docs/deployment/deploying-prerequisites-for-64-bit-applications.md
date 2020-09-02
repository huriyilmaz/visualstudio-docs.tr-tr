---
title: 64 bit uygulamalar için önkoşulları dağıtma | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c70b58577f8aa6e391215658afb7f8fa43c9bb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928877"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>64 bit uygulamalar için dağıtım önkoşulları
ClickOnce dağıtımı, uygulamaların 64-bit platformlarda yüklenmesini destekler. Hedef platformlar, 32 bitlik platformlar için **x86** , amd64 ve EM64T yönerge kümelerini destekleyen makineler için **x64** ve 64 bit Itanium işlemci için **Itanium** .

## <a name="prerequisites"></a>Önkoşullar
 Aşağıdaki tabloda, 64 bit uygulamanızın yüklemesi için ön koşullar olarak kullanabileceğiniz yeniden dağıtılabilir listelenmektedir.

 64 bitlik bileşenlere sahip olmayan bir önkoşul seçerseniz, seçili paketlerin 64 bit platformda kullanılamaz olduğunu belirten bir uyarı görebilirsiniz.

| Yeniden dağıtılabilir | x64 desteği | IA64 desteği |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Yes | Hayır |
| Visual C++ 2010 çalışma zamanı kitaplığı (ıA64) | Hayır | Yes |
| Visual C++ 2010 çalışma zamanı kitaplıkları (x64) | Yes | Hayır |
| Microsoft .NET Framework 4 (x86 ve x64) | Yes | |
| Microsoft .NET Framework 4 Istemci profili (x86 ve x64) | Yes | |

## <a name="see-also"></a>Ayrıca bkz.
- [Uygulamaları, hizmetleri ve bileşenleri dağıtma](../deployment/deploying-applications-services-and-components.md)
- [Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64 bitlik uygulamalar](/dotnet/framework/64-bit-apps)