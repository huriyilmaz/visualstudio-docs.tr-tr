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
ms.openlocfilehash: 928dc9ae93d475cd05b663cfc7838624e52f1de24411eace0ae7ac9ba818c31f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058478"
---
Bu adımlarda IIS 'nin yalnızca temel bir yapılandırması gösterilmektedir. daha ayrıntılı bilgi veya Windows masaüstü makineye yüklemek için, bkz. [ASP.NET 3,5 ve ASP.NET 4,5 kullanarak ııs veya ııs 8,0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) ['ye yayımlama](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) .

Windows sunucusu işletim sistemleri için **Sunucu Yöneticisi** **yönet** bağlantısını veya **pano** bağlantısını kullanarak **rol ve özellik ekleme** sihirbazı ' nı kullanın. **Sunucu rolleri** adımında, **Web sunucusu (IIS)** kutusunu işaretleyin.

![Sunucu rollerini seçin adımında Web sunucusu IIS rolü seçilidir.](../media/remotedbg-server-roles-ws2012.png)

**Rol hizmetleri** adımında, istediğiniz IIS rol hizmetlerini seçin veya belirtilen varsayılan rol hizmetlerini kabul edin. Yayınlama ayarları ve Web Dağıtımı kullanarak dağıtımı etkinleştirmek istiyorsanız, **IIS Yönetim betikleri ve araçları** ' nın seçildiğinden emin olun.

Web sunucusu rolü ve hizmetlerini yüklemek için onay adımlarında ilerleyin. Web sunucusu (IIS) rolü yüklendikten sonra sunucu/IIS yeniden başlatması gerekli değildir.