---
title: 'Nasıl Yapılandırılır: Performans Kurallarını Yapılandırma | Microsoft Dokümanlar'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779018"
---
# <a name="how-to-configure-performance-rules"></a>Nasıl yapılır: Performans kurallarını yapılandırma
th Visual Studio Profil Oluşturma Araçları'nın performans uyarıları, profilli bir uygulamada program yürütmesini yavaşlatabilecek sorunları gösterir. Uyarılar, daha yararlı veriler toplamak için toplama yöntemlerini değiştirmeniz gerekebileceğini de gösterebilir. Performans uyarıları bir profil oluşturma oturumunda otomatik olarak oluşturulur ve bir profil oluşturma veri [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]dosyası açıldığında Hata **Listesi** penceresinde görünür. Bazı uyarılar ilgilendiğiniz senaryolar için geçerli olmayabilir ve bazı uyarılar yanlış yükseltilebilir. Belirli uyarıları göstermek veya gizlemek için performans uyarılarını yapılandırabilirsiniz.

### <a name="to-configure-profiler-performance-warnings"></a>Profil oluşturucu performans uyarılarını yapılandırmak için

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Performans Araçlarını**Genişlet ve **Ardından Kurallar'ı**tıklatın.

3. Bir uyarıyı etkinleştirmek veya devre dışı ksaymak için uyarı **kimliği** ve adının yanındaki onay kutusunu seçin veya temizleyin.

4. Bir kuralın savaşan düzeyini belirtmek için, kuralın yanındaki **Eylem** hücresini tıklatın ve ardından uyarı düzeyini tıklatın.

    - **Devre dışı -** kuralı devre dışı eder (bu, kural kimliğinin yanındaki onay kutusunu temizlemekle aynıdır).

    - **Uyarı** - bir uyarı olarak kural görüntüler.

    - **Hata** - profil oluşturma yürütme durur ve bir hata olarak kural görüntüler.

    - **Bilgi** - kuralı yalnızca bilgi olarak görüntüler.
