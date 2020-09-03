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
ms.openlocfilehash: 2416eb24c21ef0e61bdb6db3de66c892e1eb699f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545346"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Üyeleri static olarak işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1822: üyeleri static olarak işaretleme](/visualstudio/code-quality/ca1822-mark-members-as-static).

|Öğe|Değer|
|-|-|
|TypeName|MarkMembersAsStatic|
|CheckId|CA1822|
|Kategori|Microsoft. Performance|
|Yeni Değişiklik|Bozuk olmayan-üye, yaptığınız değişiklikten bağımsız olarak, derleme dışında görünür değilse.<br /><br /> Parçalara ayırma olmayan bir üyeyi yalnızca anahtar sözcüğü olan bir örnek üye olarak değiştirirseniz `this` .<br /><br /> Parçalama-üyeyi bir örnek üyesinden statik üyeye değiştirirseniz ve derleme dışında görünür durumdaysa.|

## <a name="cause"></a>Nedeni
 Örnek verilerine erişmeyen bir üye statik olarak işaretlenmemiş (içinde paylaşılan [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Kural Tanımı
 Örnek verilerine erişmeyen Üyeler veya çağrı örnekleri metotları statik (içinde paylaşılan) olarak işaretlenebilir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Yöntemleri statik olarak işaretledikten sonra, derleyici sanal olmayan arama sitelerini bu üyelere yayar. Sanal olmayan çağrı sitelerini yayma, geçerli nesne işaretçisinin null olmadığından emin olan her bir çağrı için çalışma zamanında bir denetim yapılmasını engeller. Bu, performansa duyarlı kod için ölçülebilir bir performans kazancı elde edebilir. Bazı durumlarda, geçerli nesne örneğine erişim hatası, doğruluk sorununu temsil eder.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Üyeyi statik (veya paylaşılan) olarak işaretleyin [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ya da uygunsa Yöntem gövdesinde ' this '/' Me ' kullanın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Daha önce sevk edilen kodun bir uyarı olması için bu kuraldan daha önce sevkedilme bir uyarı görüntülenmesini güvenlidir.

## <a name="related-rules"></a>İlgili kurallar
 [CA1811: Çağırılmayan özel kodlardan kaçının](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Örneklenmemiş iç sınıflardan kaçının](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Kullanılmayan yerelleri kaldırın](../code-quality/ca1804-remove-unused-locals.md)
