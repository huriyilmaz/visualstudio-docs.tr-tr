---
description: Visual Studio hata ayıklayıcı uzak bilgisayara bağlanamıyor.
title: RPC kimlik doğrulaması gerektiriyor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a2bc92ad4686c30db46ae62f38b10ac837535fa14bf56a2c9dadc22936d13dfa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420176"
---
# <a name="error-rpc-requires-authentication"></a>Hata: RPC Kimlik Doğrulaması Gerektiriyor
Visual Studio hata ayıklayıcı uzak bilgisayara bağlanamıyor. Yerel bilgisayarda uzaktan hata ayıklamayı önleyen bir RPC ilkesi etkinleştirilir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. `\` *Windir* Çalıştır`\system32\regedt32.exe`

2. Bulun ve silin `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Kayıt defteri değişikliğinin etkili olabilmesi için bilgisayarınızı yeniden başlatın.

4. Sorun devam ederse, **bilgisayar yapılandırma > Yönetim Şablonları > sistem > uzak yordam çağrısı > kimliği DOĞRULANMAMıŞ RPC istemcileri** Grup İlkesi ayarı için etki alanı yöneticinizle iletişime geçin.
