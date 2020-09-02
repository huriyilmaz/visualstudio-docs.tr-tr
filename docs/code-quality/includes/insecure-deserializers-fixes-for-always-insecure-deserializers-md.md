---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324239"
---
- Mümkünse, bunun yerine güvenli bir serileştirici kullanın ve **bir saldırganın seri durumdan çıkarmak için rastgele bir tür belirtmesini sağlayın**. Bazı güvenli serileştiriciler şunları içerir:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Hiçbir şekilde kullanmayın <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> . Bir tür Çözümleyicisi kullanmanız gerekiyorsa, serisi kaldırılan türleri beklenen bir listeyle kısıtlayın.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-TypeNameHandling. None kullanın. TypeNameHandling için başka bir değer kullanmanız gerekiyorsa, serisi kaldırılan türleri özel bir ISerializationBinder ile beklenen bir listeyle kısıtlayın.
  - Protokol Arabellekleri
- Seri hale getirilen verileri prova yapın. Serileştirmeden sonra, serileştirilmiş verileri şifreli olarak imzalayın. Seri durumdan önce, şifreleme imzasını doğrulayın. Şifreleme anahtarını, önemli döndürmeler için açıklanmasını ve tasarıma karşı koruyun.