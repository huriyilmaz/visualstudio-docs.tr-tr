---
title: 'Hata: RPC kimlik doğrulaması gerektiriyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535742"
---
# <a name="error-rpc-requires-authentication"></a>Hata: RPC Kimlik Doğrulaması Gerektiriyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı uzak bilgisayara bağlanamıyor. Yerel bilgisayarda uzaktan hata ayıklamayı önleyen bir RPC ilkesi etkinleştirilir.  
  
### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. `\` *Windir* Çalıştır`\system32\regedt32.exe`  
  
2. Bulun ve silin `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .  
  
3. Kayıt defteri değişikliğinin etkili olabilmesi için bilgisayarınızı yeniden başlatın.  
  
4. Sorun devam ederse, **bilgisayar yapılandırması->Yönetim Şablonları->sistem->uzak yordam çağrısı->kimliği DOĞRULANMAMıŞ RPC istemcileri** Grup İlkesi ayarı hakkında etki alanı yöneticinizle iletişime geçin.
