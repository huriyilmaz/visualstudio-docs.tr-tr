---
title: 'DA0007: denetim akışı için özel durumlar kullanmaktan kaçının | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35a800d83e10b1c47096876fb3f9181a4db2f7a2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300977"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: Denetim akışı için özel durumlar kullanmaktan kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0007 |  
| Kategori |. NET Framework kullanımı |  
| Profil oluşturma yöntemleri | Tümü |  
| İleti | Yüksek sayıda özel durum sürekli olarak oluşturulur. Program mantığındaki özel durumların kullanımını azaltmayı göz önünde bulundurun. |  
| İleti türü | Uyarı |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Nedeni  
 Profil oluşturma verilerinde yüksek oranda .NET Framework özel durum işleyicileri çağrıldı. Oluşturulan özel durumların sayısını azaltmak için diğer denetim akışı mantığını kullanmayı göz önünde bulundurun.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Hataları ve program yürütmesini kesintiye uğratan diğer olayları yakalamak için özel durum işleyicilerinin kullanılması iyi bir uygulamadır, ancak özel durum işleyicisinin normal program yürütme mantığının bir parçası olarak kullanılması pahalı olabilir ve kaçınılmalıdır. Çoğu durumda, özel durumlar yalnızca seyrek oluşan ve beklenmediği durumlar için kullanılmalıdır. Özel durumlar, normal program akışının bir parçası olarak değer döndürmek için kullanılmamalıdır. Birçok durumda, değerleri doğrulayarak ve soruna neden olan deyimlerin yürütülmesini durdurmak için koşullu mantığı kullanarak özel durumlar oluşturmaktan kaçınabilirsiniz.  
  
 Daha fazla bilgi için, MSDN 'deki **Microsoft desenleri ve uygulamalar** kitaplığı 'Nın **.NET uygulama performansını ve ölçeklenebilirlik birimini geliştirme** bölümünde **yönetilen kod performansını artırma başlıklı Bölüm 5** ' in [özel durum yönetimi](https://go.microsoft.com/fwlink/?LinkID=177825) bölümüne bakın.  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 Işaretler görünümüne gitmek için Hata Listesi penceresindeki iletiye çift tıklayın. **.NET CLR özel durumlarını (@ProcessInstance) içeren sütunu bul\\atılan/sn ölçü sayısı** . Özel durum işlemenin diğerlerinden daha sık olduğu belirli program yürütme aşamaları olup olmadığını belirleme. Bir örnekleme profili kullanarak, throw deyimlerini tanımlamayı ve sık karşılaşılan özel durumlar oluşturan try/catch bloklarını kullanmayı deneyin. Gerekirse, en sık hangi özel durumların işlendiğini anlamanıza yardımcı olması için catch bloklarına mantık ekleyin. Mümkün olduğunda, sık yürütülen throw deyimlerini veya catch bloklarını basit akış denetim mantığı veya doğrulama kodu ile değiştirin.  
  
 Örneğin, uygulamanızın sık görülen Dividebysıfırsal özel durum özel durumlarını işleme olduğunu fark ediyorsanız, sıfır değer içeren paydaları denetlemek üzere programınıza mantık eklemek, uygulamanın performansını iyileştirir.
