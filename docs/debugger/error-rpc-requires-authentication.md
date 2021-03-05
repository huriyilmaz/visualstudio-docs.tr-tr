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
ms.workload:
- multiple
ms.openlocfilehash: f22998bc1c71a242b985739b2b92ba9743535d83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146723"
---
# <a name="error-rpc-requires-authentication"></a>Hata: RPC Kimlik Doğrulaması Gerektiriyor
Visual Studio hata ayıklayıcı uzak bilgisayara bağlanamıyor. Yerel bilgisayarda uzaktan hata ayıklamayı önleyen bir RPC ilkesi etkinleştirilir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. `\` *Windir* Çalıştır`\system32\regedt32.exe`

2. Bulun ve silin `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Kayıt defteri değişikliğinin etkili olabilmesi için bilgisayarınızı yeniden başlatın.

4. Sorun devam ederse, **bilgisayar yapılandırma > Yönetim Şablonları > sistem > uzak yordam çağrısı > kimliği DOĞRULANMAMıŞ RPC istemcileri** Grup İlkesi ayarı için etki alanı yöneticinizle iletişime geçin.
