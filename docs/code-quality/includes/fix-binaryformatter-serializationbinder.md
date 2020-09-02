---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471589"
---
- Bunun yerine güvenli bir serileştirici kullanın ve **bir saldırganın seri durumdan çıkarmak için rastgele bir tür belirtmesini sağlayın**. Daha fazla bilgi için [tercih edilen alternatifleri](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives)inceleyin.
- Seri hale getirilen verileri prova yapın. Serileştirmeden sonra, serileştirilmiş verileri şifreli olarak imzalayın. Seri durumdan önce, şifreleme imzasını doğrulayın. Şifreleme anahtarını, önemli döndürmeler için açıklanmasını ve tasarıma karşı koruyun.
- Bu seçenek, kodu hizmet saldırılarına karşı savunmasız hale getirir ve gelecekte olası uzaktan kod yürütme saldırıları sağlar. Daha fazla bilgi için, bkz. [BinaryFormatter Güvenlik Kılavuzu](/dotnet/standard/serialization/binaryformatter-security-guide). Seri durumdan çıkarılan türleri kısıtla. Özel bir uygulama uygulayın <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Seri durumdan kaldırmadan önce, `Binder` özelliği <xref:System.Runtime.Serialization.SerializationBinder> tüm kod yollarındaki özel bir örneğine ayarlayın. Geçersiz kılınan <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> yöntemde, tür beklenmiyorsa, serisini durdurmak için bir özel durum oluşturur.
