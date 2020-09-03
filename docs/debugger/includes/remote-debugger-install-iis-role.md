---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324407"
---
Bu adımlarda IIS 'nin yalnızca temel bir yapılandırması gösterilmektedir. Daha ayrıntılı bilgi veya bir Windows Masaüstü makinesine yüklemek için, bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak IIS veya ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ['ye yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) .

Windows Server işletim sistemleri için **Sunucu Yöneticisi** **Yönet** bağlantısı veya **Pano** bağlantısı aracılığıyla **rol ve özellik ekleme** Sihirbazı ' nı kullanın. **Sunucu rolleri** adımında, **Web sunucusu (IIS)** kutusunu işaretleyin.

![Sunucu rollerini seçin adımında Web sunucusu IIS rolü seçilidir.](../media/remotedbg-server-roles-ws2012.png)

**Rol hizmetleri** adımında, istediğiniz IIS rol hizmetlerini seçin veya belirtilen varsayılan rol hizmetlerini kabul edin. Yayınlama ayarları ve Web Dağıtımı kullanarak dağıtımı etkinleştirmek istiyorsanız, **IIS Yönetim betikleri ve araçları** ' nın seçildiğinden emin olun.

Web sunucusu rolü ve hizmetlerini yüklemek için onay adımlarında ilerleyin. Web sunucusu (IIS) rolü yüklendikten sonra sunucu/IIS yeniden başlatması gerekli değildir.