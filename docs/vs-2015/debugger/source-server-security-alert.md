---
title: Kaynak sunucu güvenlik uyarısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699319"
---
# <a name="source-server-security-alert"></a>Kaynak Sunucu Güvenlik Uyarısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak sunucu kullanırken, yalnızca bilinen ve güvenilen bir konumdan olan sembol dosyalarını kullanın.  
  
 Kaynak sunucu desteğini etkinleştirdiğinizde bu uyarı görüntülenir. Kaynak sunucu komutları hata ayıklama sembol dosyalarına (PDB dosyaları) katıştırılır. PDB dosyalarınızın nereden geldiği hakkında bilgi sahibi olun.  
  
> [!IMPORTANT]
> Kaynak sunucu kullanılırken aşağıdaki olası güvenlik tehditleri hesaba katmalıdır: rastgele komutlar uygulamanın PDB dosyasına katıştırılabildiğinden, yalnızca srcsrv.ini dosyasında yürütmek istediklerinizi yerleştirdiğinizden emin olun. srcsvr.ini dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için bkz. [güvenlik uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlarla dikkatli olun. Örneğin, cmd.exe'ye güvendiyseniz, kötü niyetli bir kullanıcı, komutu tehlikeli duruma getirecek parametreler belirtebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Kaynak sunucu](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
