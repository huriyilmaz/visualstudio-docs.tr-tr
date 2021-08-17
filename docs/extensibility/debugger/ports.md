---
title: Bağlantı | Microsoft Docs
description: Bu makalede, hata ayıklayıcısı mimarisinde bir bağlantı noktasının tanımı ve rolü Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a504db1716eaad4fbf66c34985067310fada1fa1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080214"
---
# <a name="ports"></a>Bağlantı noktaları
Hata ayıklayıcısı mimarisinde bir bağlantı *noktası:*

- Bir sunucu üzerinde çalışan bir dizi işlem için kapsayıcıdır. Örneğin, bir bağlantı noktası seri kablo veya Windows CE DCOM olmayan bir makineye bağlı bir cihaza bağlantıyı temsil ediyor olabilir. Yerel bağlantı noktası olarak adlandırılan özel bağlantı noktası, yerel makinede çalışan tüm işlemleri içerir.

- Kendisini ad veya tanımlayıcıya göre tanımlayabilir.

- Bağlantı noktası üzerinde çalışan tüm işlemleri numaralandırılır ve bu işlemleri başlatarak sonlandırabilirsiniz.

- AddPort'a [bir IDebugPortRequest2](../../extensibility/debugger/reference/idebugport2.md) bağımsız değişkeni geçerek oluşturulan [bir IDebugPort2](../../extensibility/debugger/reference/idebugportrequest2.md) [arabirimiyle temsil edildi.](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hem yerel hem de yönetilen tüm Windows işlemeye sahip varsayılan bir bağlantı noktası sağlar. Özel bağlantı noktası, temel tabanlı olmayan dış cihazlarla bağlantılar için Windows ayar gerekir. Bu tür özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası sağlayıcı da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [İşlemler](../../extensibility/debugger/processes.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
