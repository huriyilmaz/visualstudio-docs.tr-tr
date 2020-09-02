---
title: 'Nasıl yapılır: performans kurallarını yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71593496613c75485fd30481777d0fcc1102c11c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179580"
---
# <a name="how-to-configure-performance-rules"></a>Nasıl yapılır: performans kurallarını yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'nun performans uyarıları Profil Oluşturma Araçları programın yürütülmesini yavaşlatabilecek, profili oluşturulmuş bir uygulamadaki sorunları gösterir. Uyarılar Ayrıca, daha yararlı veriler toplamak için koleksiyon yöntemlerini değiştirmeniz gerekebilecek anlamına da gelebilir. Performans uyarıları bir profil oluşturma oturumunda otomatik olarak oluşturulur ve ' de bir profil oluşturma veri dosyası açıldığında **hata listesi** penceresinde görüntülenir [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Belirli uyarılar ilgilendiğiniz senaryolar için uygulanmayabilir ve bazı uyarılar doğru şekilde oluşturulabilir. Belirli uyarıları göstermek veya gizlemek için performans uyarılarını yapılandırabilirsiniz.  
  
### <a name="to-configure-profiler-performance-warnings"></a>Profil Oluşturucu performans uyarılarını yapılandırmak için  
  
1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.  
  
2. **Performans araçları**' nı genişletin ve ardından **kurallar**' a tıklayın.  
  
3. Bir uyarıyı etkinleştirmek veya devre dışı bırakmak için, uyarı **kimliği** ve adının yanındaki onay kutusunu işaretleyin veya temizleyin.  
  
4. Bir kuralın warzil düzeyini belirtmek için kuralın yanındaki **eylem** hücresine tıklayın ve sonra uyarı düzeyine tıklayın.  
  
    - **Devre dışı** -kuralı devre dışı bırakır (kural kimliği 'nin yanındaki onay kutusunun temizlenmesiyle aynıdır).  
  
    - **Uyarı** -kuralı uyarı olarak görüntüler.  
  
    - **Hata** -yürütme profili oluşturma ve kuralı hata olarak görüntüleme.  
  
    - **Bilgi** -kuralı yalnızca bilgi olarak görüntüler.
