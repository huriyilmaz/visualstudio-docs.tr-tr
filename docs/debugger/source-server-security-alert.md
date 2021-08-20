---
title: Kaynak Sunucu Güvenlik Uyarısı | Microsoft Docs
description: Hata ayıklayıcısında Kaynak Sunucu güvenlik uyarısı uyarısı Visual Studio okuyun. Kaynak Sunucu kullanırken olası güvenlik tehditlerini farkında olun.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 567440c7395982fb3894c783790eee12c9056abc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112340"
---
# <a name="source-server-security-alert"></a>Kaynak Sunucu Güvenlik Uyarısı
Kaynak Sunucu kullanırken, yalnızca bilinen ve güvenilen bir konumdaki sembol dosyalarını kullanın.

 Bu uyarı, Kaynak Sunucu desteğini etkinleştirebilirsiniz. Kaynak Sunucu komutları hata ayıklama sembol dosyalarına (**\* .pdb dosyaları) katıştırıldı.** PDB dosyalarınızın nereden geliyor olduğunu bilirsiniz.

> [!IMPORTANT]
> Kaynak Sunucu kullanılırken aşağıdaki olası güvenlik tehditleri dikkate alınmalıdır: Rastgele komutlar uygulamanın PDB dosyasına katıştırılabılanalı, bu nedenle yalnızca srcsrv.ini dosyasına yürütmek istediğiniz tehditleri koyabilirsiniz. srcsvr.ini dosyasında olmayan bir komutu yürütme girişimi, bir onay iletişim kutusunun görüntülenmesine neden olur. Daha fazla bilgi için [bkz. Güvenlik Uyarısı: Hata Ayıklayıcı Güvenilmeyen Komutu Yürütmeli.](../debugger/security-warning-debugger-must-execute-untrusted-command.md) Komut parametrelerinde bir doğrulama yapılmadı, bu nedenle güvenilir komutlara dikkat edin. Örneğin, cmd.exe'ye güvendiyseniz, kötü niyetli bir kullanıcı, komutu tehlikeli duruma getirecek parametreler belirtebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge (.pdb) ve Kaynak Dosyaları Belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Kaynak Sunucu](/windows/desktop/Debug/source-server-and-source-indexing)
