---
title: 'CA2109: görünür olay işleyicilerini gözden geçirin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ddcab6e0f416837bcd7b01521a6d77ddce691b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520984"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Görünen olay işleyicilerini gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korunan olay işleme yöntemi algılandı.

## <a name="rule-description"></a>Kural Tanımı
 Dışarıdan görünür bir olay işleme yöntemi, gözden geçirme gerektiren bir güvenlik sorunu gösterir.

 Olay işleme yöntemleri kesinlikle gerekli olmadığı sürece maruz bırakılmamalıdır. İşleyici ve olay imzaları eşleştiği sürece, sunulan yöntemi çağıran bir temsilci türü olan bir olay işleyicisi, herhangi bir olaya eklenebilir. Olaylar büyük olasılıkla herhangi bir kod tarafından oluşturulabilir ve bir düğmeye tıklanması gibi kullanıcı eylemlerine yanıt olarak yüksek düzeyde güvenilen sistem kodu tarafından sık ortaya çıkar. Bir olay işleme yöntemine güvenlik denetimi eklemek kodun yöntemi çağıran bir olay işleyicisini kaydetmesini engellemez.

 Talep bir olay işleyicisi tarafından çağrılan bir yöntemi güvenilir bir şekilde koruyamaz. Güvenlik talepleri, Çağrı yığınındaki çağıranları inceleyerek güvenilmeyen çağıranlardan kod korumanıza yardımcı olur. Olay işleyicisinin bir olaya bir olay işleyicisi ekleyen kod, olay işleyicisinin yöntemleri çalıştırıldığında çağrı yığınında mevcut değildir. Bu nedenle, çağrı yığınında olay işleyicisi yöntemi çağrıldığında yalnızca son derece güvenilen çağıranlar olabilir. Bu, olay işleyicisi yöntemi tarafından yapılan taleplerin başarılı olmasına neden olur. Ayrıca, yöntem çağrıldığında, talep edilen izin belirtilebilir. Bu nedenlerden dolayı, bu kural ihlalini düzeltmeyen risk yalnızca olay işleme yöntemi gözden geçirildikten sonra değerlendirilebiliyor. Kodunuzu gözden geçirdikten sonra aşağıdaki sorunları göz önünde bulundurun:

- Olay işleyiciniz, izinleri tamamlamak veya yönetilmeyen kod iznini gizleme gibi tehlikeli veya açıktan yararlanmayan işlemleri gerçekleştirmesini ister misiniz?

- Yalnızca yığında son derece güvenilen çağıranlar ile herhangi bir zamanda çalıştırabildiğinden, kodunuza yönelik güvenlik tehditleri nelerdir?

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için, yöntemini gözden geçirin ve aşağıdakileri değerlendirin:

- Olay işleme yöntemini genel olmayan hale getirebilirsiniz musunuz?

- Tüm tehlikeli işlevleri olay işleyicisinden dışarı taşıyabilir miyim?

- Bir güvenlik talebi belirtilmişse, bu başka bir şekilde gerçekleştirilebilir mi?

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Kodunuzun bir güvenlik tehdidi oluşturmadığından emin olmak için dikkatli bir güvenlik incelemesinin ardından bu kuraldan bir uyarı gizleyin.

## <a name="example"></a>Örnek
 Aşağıdaki kod kötü amaçlı kod tarafından kötüye kullanılabilecek bir olay işleme yöntemi gösterir.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [Güvenlik talepleri](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
