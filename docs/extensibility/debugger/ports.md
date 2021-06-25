---
title: Bağlantı | Microsoft Docs
description: Bu makalede, hata ayıklayıcı mimarisinde bir bağlantı noktasının tanımı ve rolü Visual Studio.
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
ms.workload:
- vssdk
ms.openlocfilehash: e53b2b804433f7e9450f34dac5b21e45710cd71c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900778"
---
# <a name="ports"></a>Bağlantı noktaları
Hata ayıklayıcısı mimarisinde bir bağlantı *noktası:*

- , sunucuda çalışan bir dizi işlem için kapsayıcıdır. Örneğin, bir bağlantı noktası seri kablo veya Windows CE DCOM olmayan bir makineye bağlı bir cihaza bağlantıyı temsil ediyor olabilir. Yerel bağlantı noktası olarak adlandırılan özel bağlantı noktası, yerel makinede çalışan tüm işlemleri içerir.

- Kendisini ad veya tanımlayıcıya göre tanımlayabilir.

- Bağlantı noktası üzerinde çalışan tüm işlemleri numaralandırılır ve bu işlemleri başlatarak sonlandırılır.

- AddPort'a [bir IDebugPortRequest2](../../extensibility/debugger/reference/idebugport2.md) bağımsız değişkeni geçerek oluşturulan [bir IDebugPort2](../../extensibility/debugger/reference/idebugportrequest2.md) [arabirimiyle temsil edildi.](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hem yerel hem de yönetilen tüm Windows tabanlı işlemleri ele alan varsayılan bir bağlantı noktası sağlar. Windows tabanlı olmayan dış cihazlarla bağlantılar için özel bir bağlantı noktası ayar gerekir. Bu tür özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası sağlayıcı da ayarlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [İşlemler](../../extensibility/debugger/processes.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
