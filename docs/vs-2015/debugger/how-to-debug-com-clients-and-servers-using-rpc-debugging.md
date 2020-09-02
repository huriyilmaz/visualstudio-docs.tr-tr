---
title: 'Nasıl yapılır: RPC hata ayıklamasını kullanarak COM Istemcilerinde ve sunucularda hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fda2a10cd559f940ab87e5cc8c26f5b47dbec194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837307"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Nasıl Yapılır: RPC Hata Ayıklamasını Kullanarak COM İstemcilerinde ve Sunucularda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

COM istemci/sunucu uygulamalarında hata ayıklamak için uzak yordam çağrısı (RPC) hata ayıklaması kullanabilirsiniz. Bunu kullanmak için RPC hata ayıklamayı etkinleştirmeniz gerekir. RPC hata ayıklama etkinken, istemciden sunucu çağrısına adım adım hata ayıklayıcı sunucuya eklenir ve kodun hatalarını ayıklamanıza olanak tanır. Hata ayıklayıcı eklendiğinde, tüm hata ayıklayıcı özelliklerini hem istemci hem de sunucu işlemleriyle birlikte kullanabilirsiniz.  
  
### <a name="to-enable-rpc-debugging"></a>RPC hata ayıklamasını etkinleştirmek için  
  
1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.  
  
2. **Seçenekler** iletişim kutusunda, **hata ayıklama** klasörünü tıklatın.  
  
3. **Yerel** sayfasına tıklayın.  
  
4. **RPC hata ayıklama** onay kutusunu seçin.  
  
    > [!NOTE]
    > RPC çağrılarına hata ayıklamak için yönetici veya uzman kullanıcı ayrıcalıklarına sahip olmanız gerekir.  
  
    > [!NOTE]
    > Microsoft Windows Vista çalıştıran bir uzak sunucuya RPC adımlaması, yalnızca yerel bir hata ayıklayıcı uzak sunucuya bağlıysa çalışır. Aksi takdirde, RPC çağrısı hata iletisi olmadan başarısız olur. Aksi takdirde RPC çağrısı tamamlanır, ancak RPC çağrısının içine adım çalışmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [COM sunucusu ve kapsayıcı hata ayıklaması](../debugger/com-server-and-container-debugging.md)   
 [Visual Studio'da Hata Ayıklama](../debugger/debugging-in-visual-studio.md)
