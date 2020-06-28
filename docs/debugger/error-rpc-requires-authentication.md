---
title: Hata-RPC kimlik doğrulaması gerektiriyor | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e98daf3697c86eec7767135c9ad85d67cd6e958a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460591"
---
# <a name="error-rpc-requires-authentication"></a>Hata: RPC Kimlik Doğrulaması Gerektiriyor
Visual Studio hata ayıklayıcı uzak bilgisayara bağlanamıyor. Yerel bilgisayarda uzaktan hata ayıklamayı önleyen bir RPC ilkesi etkinleştirilir.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. `\` *Windir* Çalıştır`\system32\regedt32.exe`

2. Bulun ve silin `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .

3. Kayıt defteri değişikliğinin etkili olabilmesi için bilgisayarınızı yeniden başlatın.

4. Sorun devam ederse, **bilgisayar yapılandırma > Yönetim Şablonları > sistem > uzak yordam çağrısı > kimliği DOĞRULANMAMıŞ RPC istemcileri** Grup İlkesi ayarı için etki alanı yöneticinizle iletişime geçin.