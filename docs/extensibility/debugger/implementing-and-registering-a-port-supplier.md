---
title: Liman TedarikçisiNin Uygulanması ve Kaydedilmesi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738527"
---
# <a name="implement-and-register-a-port-supplier"></a>Bir liman tedarikçisiuygulama ve kaydettirme
Bir liman tedarikçisinin rolü, süreçleri yöneten limanları izlemek ve tedarik etmektir. Bir bağlantı noktası oluşturulması gerektiğinde, bağlantı noktası tedarikçisi CoCreate ile bağlantı noktası tedarikçisi GUID (oturum hata ayıklama yöneticisi [SDM] kullanıcının seçtiği bağlantı noktası tedarikçisini veya proje sistemi tarafından belirtilen liman tedarikçisini kullanır) anında kullanılır. SDM daha sonra [canaddport'u](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) arayayıp eklenmeyen bağlantı noktaları olup olmadığını görmek için arar. Bir bağlantı noktası eklenebilirse, [AddPort'u](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) arayarak ve bağlantı noktasını açıklayan bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) geçirerek yeni bir bağlantı noktası istenir. `AddPort`[iDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilen yeni bir bağlantı noktası döndürür.

## <a name="discussion"></a>Tartışma
 Bağlantı noktası, bir makine veya hata ayıklama sunucusuyla ilişkili bir bağlantı noktası tedarikçisi tarafından oluşturulur. Bir sunucu[enumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) yöntemi ile liman tedarikçilerini sayısallandırır ve bir liman tedarikçisi de [enumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) yöntemi ile bağlantı noktalarını oyalar.

 Tipik COM kaydına ek olarak, bir liman tedarikçisi clsid ve adını belirli kayıt konumlarına yerleştirerek Visual Studio'ya kayıt yaptırmalıdır. Hata Ayıklama SDK yardımcı işlevi `SetMetric` bu angarya işler denir: bu nedenle, kayıtlı olması her öğe için bir kez çağrılır:

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

 Bir bağlantı noktası tedarikçisi, `RemoveMetric` kayıtlı her öğe için bir kez arayarak (başka bir Hata Ayıklama SDK yardımcı işlevi) arayarak kendisini kaydeder:

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
> [Hata ayıklama](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` için SDK yardımcıları `RemoveMetric` ve statik fonksiyonlar *dbgmetric.h* tanımlanan ve *ad2de.lib*içine derlenmiştir. , `metrictypePortSupplier` `metricCLSID`ve `metricName` yardımcıları da *dbgmetric.h*tanımlanır.

 Bir liman tedarikçisi adını ve GUID yöntemleri [getPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) ve [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), sırasıyla sağlayabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Liman tedarikçisi uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Liman tedarikçileri](../../extensibility/debugger/port-suppliers.md)
