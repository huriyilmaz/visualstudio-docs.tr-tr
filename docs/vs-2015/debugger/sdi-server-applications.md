---
title: SDI sunucu uygulamaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148154"
---
# <a name="sdi-server-applications"></a>SDI Sunucu Uygulamaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir SDI Sunucu uygulamasında hata ayıklaması yapıyorsanız, `/Embedding` `/Automation` C/C++, C# veya Visual Basic projeleri için *Proje* Özellik sayfaları iletişim kutusundaki **komut satırı bağımsız değişkenleri** özelliğini belirtmeniz gerekir.  
  
 Bu komut satırı bağımsız değişkenleriyle, hata ayıklayıcı sunucu uygulamasını bir kapsayıcıdan başlatılmış gibi başlatabilir. Kapsayıcının Program Yöneticisi 'nden veya dosya yöneticisinden başlatılması, kapsayıcının hata ayıklayıcıda başlatılan sunucu örneğini kullanmasına neden olur.  
  
## <a name="finding-the-command-line-arguments-property"></a>Komut satırı bağımsız değişkenleri özelliğini bulma  
 *Proje* Özellik sayfaları iletişim kutusuna erişmek için Çözüm Gezgini ' de projenize sağ tıklayın ve ardından kısayol menüsünden Özellikler ' i seçin. Komut satırı bağımsız değişkenleri özelliğini bulmak için yapılandırma özellikleri kategorisini genişletin ve hata ayıklama sayfasına tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM ve ActiveX hata ayıklaması](../debugger/com-and-activex-debugging.md)   
 [Nasıl yapılır: COM sunucularında hata ayıklama](../debugger/how-to-debug-com-servers.md)
