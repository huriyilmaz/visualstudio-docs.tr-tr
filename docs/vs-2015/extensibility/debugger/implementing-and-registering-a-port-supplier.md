---
title: Bağlantı noktası sağlayıcısı uygulama ve kaydetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824678"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Bağlantı Noktası Sağlayıcısı Uygulama ve Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir bağlantı noktası tedarikçinin rolü, işlem yönetimini izleyen ve bu bağlantı noktalarını izlemek ve sağlamak için kullanılır. Bir bağlantı noktası oluşturulması gereken zamanda, bağlantı noktası sağlayıcısının GUID 'SI ile birlikte oluşturma kullanılarak bağlantı noktası tedarikçisidir (oturum hata ayıklama Yöneticisi [SDM], Kullanıcı tarafından seçilen bağlantı noktası tedarikçisine veya proje sistemi tarafından belirtilen bağlantı noktası sağlayıcısına) sahip olur. SDM daha sonra, herhangi bir bağlantı noktasının eklenip eklenediğine bakmak için [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) öğesini çağırır. Bir bağlantı noktası eklenediyse, [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) çağırarak ve bağlantı noktasını açıklayan bir [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) geçirerek yeni bir bağlantı noktası istenir. `AddPort` , bir [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) arabirimi tarafından temsil edilen yeni bir bağlantı noktasını döndürür.  
  
## <a name="discussion"></a>Tartışma  
 Bir bağlantı noktası sağlayıcısı, bir makine ya da hata ayıklama sunucusu ile ilişkili olan bağlantı noktası sağlayıcısı tarafından oluşturulur. Bir sunucu,[Trksağlayıcılar](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) yöntemi aracılığıyla bağlantı noktası tedarikçilerini numaralandırabilirler ve bir bağlantı noktası sağlayıcısı, [TRTs](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) yöntemiyle bağlantı noktalarını numaralandırabilirler.  
  
 Tipik COM kaydına ek olarak, bir bağlantı noktası tedarikçinin CLSID ve adı belirli kayıt defteri konumlarına yerleştirerek kendisini Visual Studio ile kaydetmesi gerekir. Bu adı işleyen bir hata ayıklama SDK Yardımcısı işlevi `SetMetric` : her öğe kaydedilecek şekilde çağrılır, bu nedenle:  
  
```cpp#  
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
  
```cpp#  
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
> [Hata ayıklama Için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` ve `RemoveMetric` dbgmetric. h içinde tanımlanan ve ad2de. lib içinde derlenen statik işlevlerdir. `metrictypePortSupplier`, `metricCLSID` Ve `metricName` yardımcıları dbgmetric. h içinde de tanımlanmıştır.  
  
 Bir bağlantı noktası sağlayıcısı, sırasıyla [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) ve [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)YÖNTEMLERI aracılığıyla adını ve GUID 'sini sağlayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlantı noktası sağlayıcısı uygulama](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Hata ayıklama için SDK yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Bağlantı Noktası Sağlayıcıları](../../extensibility/debugger/port-suppliers.md)
