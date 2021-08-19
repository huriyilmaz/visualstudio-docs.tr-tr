---
title: Bağlantı noktası sağlayıcısı uygulama ve kaydetme | Microsoft Docs
description: İşlem ve kaynakları yöneten bağlantı noktalarını izleyen ve sağlayan bağlantı noktası tedarikçilerini uygulamayı ve kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 151f14592e0987a16b3195944d3ef7ce0f972ea1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153478"
---
# <a name="implement-and-register-a-port-supplier"></a>Bir bağlantı noktası sağlayıcısı uygulama ve kaydetme
Bir bağlantı noktası tedarikçinin rolü, işlem yönetimini izleyen ve bu bağlantı noktalarını izlemek ve sağlamak için kullanılır. Bir bağlantı noktasının oluşturulması gerektiğinde, bağlantı noktası sağlayıcısının GUID 'SI ile CoCreate kullanılarak oluşturulur (oturum hata ayıklama Yöneticisi [SDM], kullanıcının seçtiği bağlantı noktası tedarikçisine veya proje sistemi tarafından belirtilen bağlantı noktası sağlayıcısına) sahip olur. SDM daha sonra herhangi bir bağlantı noktasının eklenip eklenediğine bakmak için [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) öğesini çağırır. Bir bağlantı noktası eklenediyse, [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağırarak ve bağlantı noktasını açıklayan bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) geçirerek yeni bir bağlantı noktası istenir. `AddPort` bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilen yeni bir bağlantı noktasını döndürür.

## <a name="discussion"></a>Tartışma
 Bir bağlantı noktası, bir makine ya da hata ayıklama sunucusu ile ilişkilendirilmiş bir bağlantı noktası sağlayıcısı tarafından oluşturulur. Sunucu, bağlantı noktası tedarikçilerini[Trksağlayıcılar](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) yöntemiyle numaralandırır ve bir bağlantı noktası tedarikçisi, [TRTs](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) yöntemiyle bağlantı noktalarını numaralandırır.

 tipik COM kaydına ek olarak, bir bağlantı noktası tedarikçinin clsıd ve adını belirli kayıt defteri konumlarına yerleştirerek kendisini Visual Studio kaydetmesi gerekir. Bu adı işleyen bir hata ayıklama SDK Yardımcısı işlevi `SetMetric` : her öğe kaydedilecek şekilde çağrılır, bu nedenle:

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Bir bağlantı noktası sağlayıcısı `RemoveMetric` , kayıtlı her öğe için bir kez çağırarak (başka bir hata ayıklama SDK Yardımcısı işlevi) kendisini siler, bu nedenle:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> [Hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` ve `RemoveMetric` *dbgmetric. h* içinde tanımlanan ve *ad2de. lib* içinde derlenen statik işlevlerdir. `metrictypePortSupplier`, `metricCLSID` Ve `metricName` yardımcıları *dbgmetric. h* içinde de tanımlanmıştır.

 Bir bağlantı noktası sağlayıcısı, sırasıyla [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) ve [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)YÖNTEMLERI aracılığıyla adını ve GUID 'sini sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Bağlantı noktası tedarikçileri](../../extensibility/debugger/port-suppliers.md)
