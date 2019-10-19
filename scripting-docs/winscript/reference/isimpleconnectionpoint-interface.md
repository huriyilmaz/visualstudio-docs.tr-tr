---
title: Iımpliconnectionpoint arabirimi | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571793"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint Arabirimi
Belirli bir bağlantı noktasında tetiklenen olayları tanımlamak ve listelemek için basit bir yol sağlar. Bu arabirim Ayrıca, bu olaylara bir `IDispatch` nesnesi eklemenizi kolaylaştırır. Bu arabirim Işlem hata ayıklama Yöneticisi (PDM) tarafından uygulanır ve komut dosyası motorları tarafından kullanılır.  
  
 Bu arabirim `IDebugHelper::CreateSimpleConnectionPoint` kullanılabilir.  
  
 @No__t_0 devralınan yöntemlere ek olarak, `ISimpleConnectionPoint` arabirimi aşağıdaki yöntemleri sunar.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Basit bağlantı noktası nesnesi ile istemci havuzu arasında bir bağlantı kurar.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Belirtilen olay aralığındaki her olay için DISPID ve adı döndürür.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Bu arabirimde sunulan olay sayısını döndürür.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Daha önce `ISimpleConnectionPoint::Advise` aracılığıyla kurulan bir danışmanlık bağlantısını sonlandırır.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDebugProperty Arabirimi](../../winscript/reference/idebugproperty-interface.md)