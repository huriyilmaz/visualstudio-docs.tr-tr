---
title: Yönetilen kod için tam çözüm analizini devre dışı bırakma & etkinleştir
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587517"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Nasıl yapılır: yönetilen kod için tam çözüm analizini etkinleştirme ve devre dışı bırakma

*Tam çözüm Analizi* , kod analizinin, düzenleyicide açık C# olup olmamasından bağımsız olarak, Çözümdeki tüm veya Visual Basic dosyaları incelediği anlamına gelir. Varsayılan olarak, tam çözüm Analizi Visual Basic için *etkinleştirilmiştir* ve için C# *devre dışı bırakılır* .

Tüm dosyalardaki tüm sorunları görmek faydalı olabilir, ancak aynı zamanda dikkat dağıtıcı olabilir. Çözümünüz çok büyükse veya çok sayıda dosya içeriyorsa, Visual Studio 'Yu yavaşlatır. Gösterilen sorun sayısını sınırlandırmak ve Visual Studio performansını geliştirmek için tam çözüm analizini devre dışı bırakabilirsiniz. Gerekirse bu özelliği kolayca yeniden etkinleştirebilirsiniz.

Aşağıdaki görüntüde tam çözüm Analizi etkinleştirilmiştir. Açık olmasalar bile, Çözümdeki tüm dosyalardaki derleyici ve kod çözümleme sorunları gösterilir.

![Tam çözüm Analizi etkin.](../code-quality/media/fsa_enabled.png)

Aşağıdaki görüntüde, tam çözüm analizini devre dışı bıraktıktan sonra aynı çözümün sonuçları gösterilmektedir. Yalnızca derleyici hataları ve açık çözüm dosyalarındaki kod analizi sorunları Hata Listesi görüntülenir.

![Tam çözüm Analizi devre dışı.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Tam çözüm analizini değiştirme

1. **Seçenekler** iletişim kutusunu açmak Için, Visual Studio 'daki menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. **Seçenekler** Iletişim kutusunda **metin düzenleyici** > **C#** veya **temel** > **Gelişmiş**' i seçin.

1. Tam çözüm analizini etkinleştirmek için **tam çözüm analizini etkinleştir** onay kutusunu seçin veya devre dışı bırakmak için kutuyu temizleyin. İşiniz bittiğinde **Tamam ' ı** seçin.

   ![Tam çözüm analizini etkinleştir onay kutusu.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Tam çözüm analizini otomatik olarak devre dışı bırak

Visual Studio, 200 MB veya daha az sistem belleği olduğunu algılarsa, etkinleştirilirse tam çözüm analizini (ve diğer diğer özellikleri) otomatik olarak devre dışı bırakır. Bu gerçekleşirse, Visual Studio 'Nun bazı özellikleri devre dışı bırakıldığını bildiren bir uyarı görüntülenir. Bir düğme, isterseniz tam çözüm analizini yeniden yapılandırmanızı sağlar.

![Tam çözüm analizini askıya uyarı metni](../code-quality/media/fsa_alert.png)
