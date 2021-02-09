---
title: Kaynak sunucu güvenlik uyarısı | Microsoft Docs
description: Visual Studio hata ayıklayıcısında kaynak sunucu güvenlik uyarısı uyarısı hakkında bilgi edinin. Kaynak sunucu kullanırken olası güvenlik tehditlerinin farkında olun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 947274f88658d44ab8e4f7de54ac001b93e270aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903517"
---
# <a name="source-server-security-alert"></a>Kaynak Sunucu Güvenlik Uyarısı
Kaynak sunucu kullanırken, yalnızca bilinen ve güvenilen bir konumdan olan sembol dosyalarını kullanın.

 Kaynak sunucu desteğini etkinleştirdiğinizde bu uyarı görüntülenir. Kaynak sunucu komutları hata ayıklama sembol dosyalarına (**\* . pdb** dosyaları) katıştırılır. PDB dosyalarınızın nereden geldiği hakkında bilgi sahibi olun.

> [!IMPORTANT]
> Kaynak sunucu kullanılırken aşağıdaki olası güvenlik tehditleri hesaba katmalıdır: rastgele komutlar uygulamanın PDB dosyasına katıştırılabildiğinden, yalnızca srcsrv.ini dosyasında yürütmek istediklerinizi yerleştirdiğinizden emin olun. srcsvr.ini dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için bkz. [güvenlik uyarısı: hata ayıklayıcı güvenilmeyen komut yürütmelidir](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, cmd.exe'ye güvendiyseniz, kötü niyetli bir kullanıcı, komutu tehlikeli duruma getirecek parametreler belirtebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Kaynak sunucu](/windows/desktop/Debug/source-server-and-source-indexing)
