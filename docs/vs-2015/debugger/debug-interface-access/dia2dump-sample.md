---
title: Dia2dump örneği | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197596"
---
# <a name="dia2dump-sample"></a>Dia2dump Örneği
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dia2dump örneği Visual Studio ile yüklenir ve Dia2dump. cpp kaynak dosyasını içerir. Derlenmiş yürütülebilir dosya, komut satırından çalışır ve bir program veritabanı (. pdb) dosyasının bir bütün içeriğini görüntüler.  
  
### <a name="to-install-the-sample"></a>Örneği yüklemek için  
  
1. Sisteminizin, Visual Studio kurulum başlangıç sayfasında açıklanan tüm kurulum gereksinimlerini karşıladığını doğrulayın.  
  
2. Visual Studio 'Yu yükledikten sonra dahil edilen örneklerle ilgili tüm kurulum ve yükleme yönergelerini izleyin.  
  
#### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1. Visual Studio 'da Dia2dump. sln dosyasını açın. (Gerekirse, Visual Studio önce Dia2dump projesini yükseltmenize yardımcı olur.)  
  
2. Proje özellik sayfalarında, **C/C++** &#124; **genel** &#124; **ek içerme dizinleri** özelliği ' nde, `..\DIA SDK\include` dizini belirtin. Bu, derleyicinin dia2. h dosyasını bulabilirler.  
  
3. **Derle** menüsünde **çözümü yeniden derle**' ye tıklayın.  
  
4. Visual Studio’yu kapatın.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. Bir komut istemi açın ve şunu yazın:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dia2dump. cpp kaynak dosyası](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Nasıl Yapılır: Başarısız Visual Studio Proje Yükseltmelerinde Sorun Giderme](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
