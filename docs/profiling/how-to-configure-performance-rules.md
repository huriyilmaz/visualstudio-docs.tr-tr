---
title: 'Nasıl yapılır: performans kurallarını yapılandırma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c9bb9b07a0ae1fa19ae48408aa34a9dfb6577b6e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779018"
---
# <a name="how-to-configure-performance-rules"></a>Nasıl yapılır: performans kurallarını yapılandırma
Visual Studio 'nun performans uyarıları Profil Oluşturma Araçları programın yürütülmesini yavaşlatabilecek, profili oluşturulmuş bir uygulamadaki sorunları gösterir. Uyarılar Ayrıca, daha yararlı veriler toplamak için koleksiyon yöntemlerini değiştirmeniz gerekebilecek anlamına da gelebilir. Performans uyarıları bir profil oluşturma oturumunda otomatik olarak oluşturulur ve profil oluşturma veri dosyası [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]açıldığında **hata listesi** penceresinde görüntülenir. Belirli uyarılar ilgilendiğiniz senaryolar için uygulanmayabilir ve bazı uyarılar doğru şekilde oluşturulabilir. Belirli uyarıları göstermek veya gizlemek için performans uyarılarını yapılandırabilirsiniz.

### <a name="to-configure-profiler-performance-warnings"></a>Profil Oluşturucu performans uyarılarını yapılandırmak için

1. **Araçlar** menüsünde **Seçenekler**' e tıklayın.

2. **Performans araçları**' nı genişletin ve ardından **kurallar**' a tıklayın.

3. Bir uyarıyı etkinleştirmek veya devre dışı bırakmak için, uyarı **kimliği** ve adının yanındaki onay kutusunu işaretleyin veya temizleyin.

4. Bir kuralın warzil düzeyini belirtmek için kuralın yanındaki **eylem** hücresine tıklayın ve sonra uyarı düzeyine tıklayın.

    - **Devre dışı** -kuralı devre dışı bırakır (kural kimliği 'nin yanındaki onay kutusunun temizlenmesiyle aynıdır).

    - **Uyarı** -kuralı uyarı olarak görüntüler.

    - **Hata** -yürütme profili oluşturma ve kuralı hata olarak görüntüleme.

    - **Bilgi** -kuralı yalnızca bilgi olarak görüntüler.
