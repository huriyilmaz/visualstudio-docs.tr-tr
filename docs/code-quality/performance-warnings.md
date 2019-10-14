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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305665"
---
# <a name="performance-warnings"></a>Performans Uyarıları
Performans uyarıları yüksek performanslı kitaplıkları ve uygulamaları destekler.

## <a name="in-this-section"></a>Bu Bölümde

| Kural | Açıklama |
| - | - |
| [CA1800: Gereksiz @ no__t-0 olarak atama | Özellikle yayınlar sıkıştırılmış yineleme deyiminde gerçekleştirildiğinde yinelenen yayınların performansını azaltır. |
| [CA1801: Kullanılmayan parametreleri gözden geçir @ no__t-0 | Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir. |
| [CA1802: Uygun olan sabit değerleri kullanın @ no__t-0 | Bir alan statik ve salt okunur olarak tanımlanır ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ' da paylaşılan ve salt okunur) ve derleme zamanında oluşturulabilir bir değer ile başlatılır. Hedeflenen alana atanan değer derleme zamanında hesaplanabilir olduğundan, bildirimi hesaplanmasını değiştirme (içinde sabit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ve böylece, çalışma zamanında derleme zamanından yerine değeri hesaplanan alan. |
| [CA1804: Kullanılmayan yerelleri kaldır @ no__t-0 | Kullanılmayan yerel değişkenler ve gereksiz atamaların derleme boyutunu artırır ve performansı düşürür. |
| [CA1806: Yöntem sonuçlarını yoksayma @ no__t-0 | Yeni bir nesne oluşturulur, ancak hiçbir zaman kullanılmaz veya yeni bir dize oluşturan ve döndüren bir yöntem çağrılır ve yeni dize hiçbir zaman kullanılmaz veya bir bileşen nesne modeli (COM) ya da P/Invoke yöntemi hiçbir zaman kullanılmayan bir HRESULT veya hata kodu döndürür. |
| [CA1809: Aşırı Yerellerden kaçının @ no__t-0 | Bir değeri bellek yerine işlemci yazmacında tutmak yaygın bir performans iyileştirmesidir ve buna "değeri kaydetmek denir".  Tüm yerel değişkenlerin kaydedilme imkanına sahip olabilmesi şansını artırmak için 64 yerel değişken sayısını sınırlayın. |
| [CA1810: Başvuru türü statik alanlarını Başlat satır içi @ no__t-0 | Bir tür açık statik yapıcı bildirdiğinde, JIT derleyici her bir statik yöntemi kontrol ekler ve türün yapıcı örneği statik yapıcının daha önceden çağrıldığından emin olur. Statik oluşturucu denetimleri performansı düşürebilir. |
| [CA1811: Çağrılmadı özel koddan kaçının @ no__t-0 | Özel veya dahili (derleme düzeyi) bir üyenin derlemede çağıranları yoktur, ortak dil çalışma zamanı tarafından çağrılmaz ve bir temsilci tarafından çağrılmaz. |
| [CA1812: Örneklenmemiş iç sınıflardan kaçının @ no__t-0 | Bir derleme düzeyi türünün örneği, derleme içindeki kod tarafından oluşturulmaz. |
| [CA1813: Korumasız özniteliklerden kaçının @ no__t-0 | .NET özel özniteliklerin alınması için yöntemler sağlar. Varsayılan olarak, bu yöntemleri öznitelik devralma hiyerarşisinde arar. Öznitelik mühürleme kalıtım hiyerarşisi aracılığıyla aramayı ortadan kaldırır ve performansı artırabilir. |
| [CA1814: Çok boyutlu @ no__t-0 üzerinde pürüzlü Diziler tercih etme | Basit bir dizi, öğeleri dizi olan bir dizidir. Öğeleri oluşturan diziler farklı boyutlarda olabilir ve bu da bazı veri kümeleri için daha az alana yol açabilir. |
| [CA1815: Geçersiz kılma eşittir ve işleç eşittir değer türleri @ no__t-0 | Değer türleri için, Equals'ın devralınmış uygulaması Reflection kitaplığını kullanır ve türdeki tüm alanların içeriğini karşılaştırır. Yansıma hesaplama açısından pahalıdır ve her alan için eşitlik karşılaştırma gereksiz olabilir. Kullanıcıları karşılaştırmak veya örneklerini sıralamak ya da tablo anahtarlarını karma olarak kullanmayı bekliyorsanız, değer türünüz Equals'ı uygulamalıdır. |
| [CA1816: GC 'yi çağırın. SuppressFinalize doğru @ no__t-0 | Dispose uygulamasının bir yöntemi GC çağrısını yapmaz. SuppressFinalize veya Dispose çağrılarının uygulanması olmayan bir yöntem GC. SuppressFinalize veya bir yöntemi GC çağırır. SuppressFinalize ve bu ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) dışında bir şey geçirir. |
| [CA1819: Özellikler dizileri döndürmemelidir @ no__t-0 | Özellik salt okunurdur olsa bile, Özellikler tarafından döndürülen diziler yazma korumalı değildir. Dizi değiştirilmeye kanıt tutulacak özellik dizisinin bir kopyasını döndürmelidir. Tipik olarak, kullanıcılar bu tür bir özellik aramanın performans üzerindeki olumsuz etkilerini anlamayacaktır. |
| [CA1820: Dize uzunluğunu kullanarak boş dizeler için test edin @ no__t-0 | String.Length özelliği veya String.IsNullOrEmpty yöntemi, Equals kullanılmasından önemli ölçüde daha hızlıdır. |
| [CA1821: Boş sonlandırıcıları kaldır @ no__t-0 | Güncelleştirirken, nesne kullanım süresini izleme söz konusu olduğunda ek performans yükü nedeniyle sonlandırıcılardan kaçının. Boş bir Sonlandırıcı, hiçbir avantaj olmadan ek yüke neden olur. |
| [CA1822: Üyeleri static @ no__t-0 olarak işaretle | Örnek veri veya çağrı örnek yöntemlerinin erişmez üyeleri işaretlenebilir olarak statik (paylaşılan [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Bu, ölçülebilir kazanç performansını performans duyarlı kodunuz için verebilir. |
| [CA1823: Kullanılmayan özel alanlardan kaçının @ no__t-0 | Derlemede erişimi görülmeyen özel alanlar algılandı. |
| [CA1824: Derlemeleri NeutralResourcesLanguageAttribute @ no__t ile işaretle-0 | NeutralResourcesLanguage özniteliği bir derlemenin bağımsız kültürünün kaynağını görüntüleyen dilin Kaynak Yöneticisi'ni bilgilendirir. Bu ilk yüklediğiniz kaynak için arama performansını artırır ve çalışma kümenizi azaltabilir. |
| [CA1825: Sıfır uzunlukta dizi ayırmaktan kaçının @ no__t-0 | Sıfır uzunluklu bir diziyi başlatmak gereksiz bellek ayırmaya yol açar. Bunun yerine, <xref:System.Array.Empty%2A?displayProperty=nameWithType> ' ı çağırarak statik olarak ayrılan boş dizi örneğini kullanın. Bellek ayırma, bu yöntemin tüm etkinleştirmeleri genelinde paylaşılır. |
