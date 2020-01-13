---
title: 'CA1822: üyeleri statik olarak Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce4aa6aef9c70d0d628603afa7a256c309f280d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917937"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Üyeleri statik olarak işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1822: üyeleri static olarak işaretleme](/visualstudio/code-quality/ca1822-mark-members-as-static).

|||
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Bozuk olmayan-üye, yaptığınız değişiklikten bağımsız olarak, derleme dışında görünür değilse.<br /><br /> Parçalama-`this` anahtar sözcüğünü kullanarak üyeyi bir örnek üyesi olarak değiştirirseniz.<br /><br /> Parçalama-üyeyi bir örnek üyesinden statik üyeye değiştirirseniz ve derleme dışında görünür durumdaysa.|

## <a name="cause"></a>Sebep
 Örnek verilerine erişmeyen bir üye statik olarak işaretlenmez ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)]içinde paylaşılır).

## <a name="rule-description"></a>Kural Tanımı
 Örnek veri veya çağrı örnek yöntemlerinin erişmez üyeleri işaretlenebilir olarak statik (paylaşılan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Sanal olmayan çağrı sitelerini yayma, geçerli nesne işaretçisinin null olmadığından emin olan her bir çağrı için çalışma zamanında bir denetim yapılmasını engeller. Bu, performansa duyarlı kod için ölçülebilir bir performans kazancı elde edebilir. Bazı durumlarda, geçerli nesne örneğine erişim hatası, doğruluk sorununu temsil eder.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Üyeyi statik (veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]içinde paylaşılan) olarak işaretleyin ya da uygunsa Yöntem gövdesinde ' this '/' Me ' kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk edilen kodun bir uyarı olması için bu kuraldan daha önce sevkedilme bir uyarı görüntülenmesini güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1811: Çağrılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklendirilmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Kullanılmayan yerel öğeleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
