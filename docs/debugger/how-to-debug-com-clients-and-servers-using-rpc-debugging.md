---
title: RPC hata ayıklamasını kullanarak COM istemcilerinde ve sunucularda hata ayıklama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83fdfa65f4efb6f0bc0b99eac27ae0e57c79e3cd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733686"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>Nasıl Yapılır: RPC Hata Ayıklamasını Kullanarak COM İstemcilerinde ve Sunucularda Hata Ayıklama
COM istemci/sunucu uygulamalarında hata ayıklamak için uzak yordam çağrısı (RPC) hata ayıklaması kullanabilirsiniz. Bunu kullanmak için RPC hata ayıklamayı etkinleştirmeniz gerekir. RPC hata ayıklama etkinken, istemciden sunucu çağrısına adım adım hata ayıklayıcı sunucuya eklenir ve kodun hatalarını ayıklamanıza olanak tanır. Hata ayıklayıcı eklendiğinde, tüm hata ayıklayıcı özelliklerini hem istemci hem de sunucu işlemleriyle birlikte kullanabilirsiniz.

### <a name="to-enable-rpc-debugging"></a>RPC hata ayıklamasını etkinleştirmek için

1. **Araçlar** menüsünde **Seçenekler**' e tıklayın.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** klasörünü tıklatın.

3. **Yerel** sayfasına tıklayın.

4. **RPC hata ayıklama** onay kutusunu seçin.

    > [!NOTE]
    > RPC çağrılarına hata ayıklamak için yönetici veya uzman kullanıcı ayrıcalıklarına sahip olmanız gerekir.

    > [!NOTE]
    > Microsoft Windows Vista çalıştıran bir uzak sunucuya RPC adımlaması, yalnızca yerel bir hata ayıklayıcı uzak sunucuya bağlıysa çalışır. Aksi takdirde, RPC çağrısı hata iletisi olmadan başarısız olur. Aksi takdirde RPC çağrısı tamamlanır, ancak RPC çağrısının içine adım çalışmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [COM Sunucusunda ve Kapsayıcısında Hata Ayıklama](../debugger/com-server-and-container-debugging.md)
- [Visual Studio’da hata ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)