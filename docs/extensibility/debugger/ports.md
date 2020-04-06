---
title: Bağlantı Noktaları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738311"
---
# <a name="ports"></a>Bağlantı Noktaları
Hata ayıklama mimarisinde, bir *bağlantı noktası:*

- Sunucuda çalışan bir işlem kümesi için bir kapsayıcıdır. Örneğin, bağlantı noktası, Windows CE tabanlı bir aygıta seri kablo yla veya ağa bağlı olmayan bir DCOM makinesine olan bağlantıyı temsil edebilir. Yerel bağlantı noktası olarak adlandırılan özel bir bağlantı noktası, yerel makinede çalışan tüm işlemleri içerir.

- Kendini ad veya tanımlayıcıile tanımlayabilir.

- Bağlantı noktasında çalışan tüm süreçleri sayısalhale getirebilir ve bu işlemleri başlatAbilir ve sonlandırabilir.

- [AddPort'a](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) bağımsız değişkeni geçirilerek oluşturulan bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi ile temsil edilir.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hem yerel hem de yönetilen tüm Windows tabanlı işlemleri işleyen varsayılan bir bağlantı noktası sağlar. Windows tabanlı olmayan harici aygıtlarla bağlantılar için özel bir bağlantı noktası ayarlanmalıdır. Bu tür özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası tedarikçisi de ayarlamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Süreç](../../extensibility/debugger/processes.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
