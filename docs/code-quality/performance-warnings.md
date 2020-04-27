---
title: Performans Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e578bedf3e6b784321ffb14628ebbe10bc45dc20
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167352"
---
# <a name="performance-warnings"></a>Performans Uyarıları
Performans uyarıları yüksek performanslı kitaplıkları ve uygulamaları destekler.

## <a name="in-this-section"></a>Bu Bölümde

| Kural | Açıklama |
| - | - |
| [CA1800: Gereksiz tür dönüştürmeler yapmayın](../code-quality/ca1800.md) | Özellikle yayınlar sıkıştırılmış yineleme deyiminde gerçekleştirildiğinde yinelenen yayınların performansını azaltır. |
| [CA1801: Kullanılmayan parametreleri gözden geçirin](../code-quality/ca1801.md) | Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. |
| [CA1802: Uygun yerlerde sabitleri kullanın](../code-quality/ca1802.md) | Bir alan statik ve salt okunur (paylaşılan ve salt okunur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) olarak tanımlanır ve derleme zamanında oluşturulabilir bir değer ile başlatılır. Hedeflenen alana atanan değer derleme zamanında oluşturulabilir olduğundan, değerin çalışma zamanı yerine derleme zamanında hesaplanabilmesi için bildirimi const (const [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) alanı olarak değiştirin. |
| [CA1804: Kullanılmayan yerelleri kaldırın](../code-quality/ca1804.md) | Kullanılmayan yerel değişkenler ve gereksiz atamaların derleme boyutunu artırır ve performansı düşürür. |
| [CA1806: Metot sonuçlarını yoksaymayın](../code-quality/ca1806.md) | Yeni bir nesne oluşturulur, ancak hiçbir zaman kullanılmaz veya yeni bir dize oluşturan ve döndüren bir yöntem çağrılır ve yeni dize hiçbir zaman kullanılmaz veya bir bileşen nesne modeli (COM) ya da P/Invoke yöntemi hiçbir zaman kullanılmayan bir HRESULT veya hata kodu döndürür. |
| [CA1809: Aşırı yerellerden kaçının](../code-quality/ca1809.md) | Bir değeri bellek yerine işlemci yazmacında tutmak yaygın bir performans iyileştirmesidir ve buna "değeri kaydetmek denir".  Tüm yerel değişkenlerin kaydedilme olasılığını artırmak için yerel değişken sayısını 64 olarak sınırlandırın. |
| [CA1810: Başvuru türü statik alanları satır içinden başlatın](../code-quality/ca1810.md) | Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik oluşturucu denetimleri performansı düşürebilir. |
| [CA1811: Çağırılmayan özel kodlardan kaçının](../code-quality/ca1811.md) | Özel veya dahili (derleme düzeyi) bir üyenin derlemede çağıranları yoktur, ortak dil çalışma zamanı tarafından çağrılmaz ve bir temsilci tarafından çağrılmaz. |
| [CA1812: Örneklenmemiş iç sınıflardan kaçının](../code-quality/ca1812.md) | Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz. |
| [CA1813: Mühürsüz özniteliklerden kaçının](../code-quality/ca1813.md) | .NET özel özniteliklerin alınması için yöntemler sağlar. Varsayılan olarak, bu yöntemleri öznitelik devralma hiyerarşisinde arar. Öznitelik mühürleme kalıtım hiyerarşisi aracılığıyla aramayı ortadan kaldırır ve performansı artırabilir. |
| [CA1814: Çok boyutlu diziler yerine basit dizileri tercih edin](../code-quality/ca1814.md) | Basit bir dizi, öğeleri dizi olan bir dizidir. Öğeleri oluşturan diziler farklı boyutlarda olabilir ve bu da bazı veri kümeleri için daha az alana yol açabilir. |
| [CA1815: Değer türlerinde eşittir ve işleç eşittiri geçersiz kılın](../code-quality/ca1815.md) | Değer türleri için, Equals'ın devralınmış uygulaması Reflection kitaplığını kullanır ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals'ı uygulamalıdır. |
| [CA1816: GC.SuppressFinalize'ı doğru çağırın](../code-quality/ca1816.md) | Dispose uygulamasının bir yöntemi GC çağrısını yapmaz. SuppressFinalize veya Dispose çağrılarının uygulanması olmayan bir yöntem GC. SuppressFinalize veya bir yöntemi GC çağırır. SuppressFinalize ve bu (benim [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) dışında bir şey geçirir. |
| [CA1819: Özellikler diziler döndürmemelidir](../code-quality/ca1819.md) | Özellik salt okunurdur olsa bile, Özellikler tarafından döndürülen diziler yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Tipik olarak, kullanıcılar bu tür bir özellik aramanın performans üzerindeki olumsuz etkilerini anlamayacaktır. |
| [CA1820: Dize uzunluğunu kullanarak boş dizeleri test edin](../code-quality/ca1820.md) | String.Length özelliği veya String.IsNullOrEmpty yöntemi, Equals kullanılmasından önemli ölçüde daha hızlıdır. |
| [CA1821: Boş sonlandırıcıları kaldırın](../code-quality/ca1821.md) | Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Boş bir Sonlandırıcı, hiçbir avantaj olmadan ek yüke neden olur. |
| [CA1822: Üyeleri static olarak işaretleyin](../code-quality/ca1822.md) | Örnek verilerine erişmeyen Üyeler veya çağrı örnekleri metotları statik (içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]paylaşılan) olarak işaretlenebilir. Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için verebilir. |
| [CA1823: Kullanılmayan özel alanlardan kaçının](../code-quality/ca1823.md) | Derlemede erişimi görülmeyen özel alanlar algılandı. |
| [CA1824: Derlemeleri NeutralResourcesLanguageAttribute ile işaretleyin](../code-quality/ca1824.md) | NeutralResourcesLanguage özniteliği bir derlemenin bağımsız kültürünün kaynağını görüntüleyen dilin Kaynak Yöneticisi'ni bilgilendirir. Bu ilk yüklediğiniz kaynak için arama performansını artırır ve çalışma kümenizi azaltabilir. |
| [CA1825: Sıfır uzunluklu dizi ayırmalarından kaçının](../code-quality/ca1825.md) | Sıfır uzunluklu bir diziyi başlatmak gereksiz bellek ayırmaya yol açar. Bunun yerine, çağırarak <xref:System.Array.Empty%2A?displayProperty=nameWithType>statik olarak ayrılan boş dizi örneğini kullanın. Bellek ayırma, bu yöntemin tüm etkinleştirmeleri genelinde paylaşılır. |
| [CA1826: LINQ sıralanabilir yöntemi yerine özelliği kullanın](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>LINQ yöntemi eşdeğer, daha verimli bir özelliği destekleyen bir tür üzerinde kullanıldı. |
| [CA1827: herhangi bir kullanılabilir olduğunda Count/LongCount kullanmayın](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A>ya <xref:System.Linq.Enumerable.LongCount%2A> da yöntemi, yöntemin <xref:System.Linq.Enumerable.Any%2A> daha verimli olacağı yerde kullanılmıştır. |
| [CA1828: AnyAsync kullanılıyorsa, CountAsync/LongCountAsync kullanmayın](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A>ya <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> da yöntemi, yöntemin <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> daha verimli olacağı yerde kullanılmıştır. |
| [CA1829: sıralanabilir. Count yöntemi yerine length/Count özelliğini kullanın](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>LINQ yöntemi eşdeğer, daha etkin `Length` veya `Count` özelliği destekleyen bir tür üzerinde kullanıldı. |
