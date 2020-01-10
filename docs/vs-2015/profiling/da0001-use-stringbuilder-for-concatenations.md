---
title: 'DA0001: birleştirmeleri için StringBuilder kullanın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: faa0cf18bfd9810d84e01028b3f787b3b2c99578
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844739"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Birleştirmeler için StringBuilder kullanın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [DA0001: birleştirmeleri Için StringBuilder kullanma](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations).  
  
|||  
|-|-|  
|Kural Kimliği|DA0001|  
|Kategori|.NET Framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme|  
|İleti|Dize birleştirmeleri için StringBuilder kullanmayı düşünün|  
|Mesaj türü|Uyarı|  
  
## <a name="cause"></a>Sebep  
 System. String. Concat çağrısı, profil oluşturma verilerinin önemli bir orandır. Birden çok kesimden dizeler oluşturmak için <xref:System.Text.StringBuilder> sınıfını kullanmayı düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 <xref:System.String> nesne sabittir. Bu nedenle, dizedeki tüm değişiklikler yeni bir dize nesnesi ve özgün bir çöp toplama oluşturur. Bu davranış, String. Concat öğesini açık bir şekilde çağırıp veya + ya da + = gibi dize birleştirme işleçlerini kullanın. Bu yöntemler sık sık çağrılırsa (örneğin, sıkı bir döngüde bir dizeye karakterler eklendiğinde) program performansı azalabilir.  
  
 StringBuilder sınıfı kesilebilir bir nesnedir ve System. String 'ten farklı olarak, bu sınıfın bir örneğini değiştiren StringBuilder üzerindeki yöntemlerin çoğu aynı örneğe bir başvuru döndürür. Bir StringBuilder örneğine karakter ekleyebilir veya metin ekleyebilir ve yeni bir örnek ayırma ve özgün örneği silme gereksinimi olmadan örnekteki karakterleri kaldırabilir veya değiştirebilirsiniz.  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 Örnekleme profili verilerinin [Işlev ayrıntıları görünümüne](../profiling/function-details-view.md) gitmek için hata Listesi penceresindeki iletiye çift tıklayın. Dize bitişinin en sık kullanımını yapan programın bölümlerini bulun. Sık kullanılan dize birleştirme işlemleri dahil olmak üzere karmaşık dize düzenlemeleri için StringBuilder sınıfını kullanın.  
  
 Dizeler ile çalışma hakkında daha fazla bilgi için, Microsoft desenleri ve uygulamalar kitaplığındaki [yönetilen kod performansını artırma başlıklı Bölüm 5](https://msdn.microsoft.com/library/ms998547.aspx) ' ın [dize işlemleri](https://msdn.microsoft.com/library/ms998547.aspx#scalenetchapt05_topic26) bölümü.
