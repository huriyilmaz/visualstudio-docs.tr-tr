---
title: Bağlantı noktaları | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir bağlantı noktasının tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 368d55db8e52d2797041e420d109960c88d96cb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927190"
---
# <a name="ports"></a>Bağlantı noktaları
Hata ayıklayıcı mimarisinde, bir *bağlantı noktası*:

- , Sunucuda çalışan bir işlem kümesi için bir kapsayıcıdır. Örneğin, bir bağlantı noktası, Windows CE tabanlı bir cihaza seri kablo veya ağ bağlantılı DCOM olmayan bir makineye olan bağlantıyı temsil edebilir. Yerel makinede çalışan tüm işlemlerin bulunduğu, yerel bağlantı noktası olarak adlandırılan özel bir bağlantı noktası.

- , Kendisini ada veya tanımlayıcıya göre tanımlayabilir.

- Bağlantı noktasında çalışan tüm işlemlerin listesini oluşturabilir ve bu süreçler başlatabilir ve sonlandırabilirsiniz.

- , [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)'A bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) bağımsız değişkeni geçirerek oluşturulan bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilir.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hem yerel hem de yönetilen tüm Windows tabanlı süreçlerini işleyen varsayılan bir bağlantı noktası sağlar. Windows tabanlı olmayan dış cihazlarla bağlantılar için özel bir bağlantı noktası ayarlanmalıdır. Bu tür özel bağlantı noktalarını sağlamak için özel bir bağlantı noktası sağlayıcısı da ayarlamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Sunucular](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [İşlemler](../../extensibility/debugger/processes.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
