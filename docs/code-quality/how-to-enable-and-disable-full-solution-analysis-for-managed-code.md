---
title: Yönetilen kod için tam çözüm çözümlemesini devre dışı & etkinleştirin
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
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79428273"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Nasıl yapılır: Yönetilen kod için tam çözüm çözümlemesini etkinleştirme ve devre dışı

*Tam çözüm analizi,* kod çözümlemesi halinde açık olup olmadıklarına bakılmaksızın çözümdeki tüm C# veya Visual Basic dosyalarını inceler anlamına gelir. Varsayılan olarak, Visual Basic için tam çözüm çözümlemesi *etkinleştirilir* ve C#için *devre dışı bırakılır.*

Tüm dosyalardaki tüm sorunları görmek yararlı olabilir, ancak dikkat dağıtıcı da olabilir. Çözümünüz çok büyükse veya birçok dosyanız varsa Visual Studio'yı yavaşlatıyor. Gösterilen sorun sayısını sınırlamak ve Visual Studio performansını artırmak için tam çözüm çözümlemesi devre dışı kullanabilirsiniz. Gerekirse bu özelliği kolayca yeniden etkinleştirebilirsiniz.

Aşağıdaki resimde, tam çözüm analizi etkinleştirilir. Çözümdeki tüm dosyalardaki derleyici ve kod çözümlemesi sorunları, açık olmasalar bile gösterilir.

![Tam çözüm analizi etkin.](../code-quality/media/fsa_enabled.png)

Aşağıdaki resim, tam çözüm çözümlemesi devre dışı bırakılması ndan sonra aynı çözümün sonuçlarını gösterir. Hata Listesinde yalnızca derleyici hataları ve kod çözümleme sorunları görünür.

![Tam çözüm analizi devre dışı bırakıldı.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>Tam çözüm analizini geçişe kaydırma

1. **Seçenekler** iletişim kutusunu açmak için Visual Studio'daki menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

1. **Seçenekler** iletişim kutusunda Metin **Düzenleyicisi** > **C#** veya **Temel** > **Gelişmiş'i**seçin.

1. Tam çözüm analizini etkinleştirmek için **tam çözüm çözümlemesini etkinleştir** onay kutusunu seçin veya devre dışı kakmak için kutuyu temizleyin. Bitirdiğinde **Tamam'ı** seç.

   ![Tam çözüm analizi onay kutusunu etkinleştirin.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>Tam çözüm analizini otomatik olarak devre dışı

Visual Studio 200 MB veya daha az sistem belleği kullanılabilir olduğunu algılarsa, etkinleştirilmişse tam çözüm çözümlemesi (ve diğer bazı özellikleri) otomatik olarak devre dışı kılabilir. Bu durumda, Visual Studio'nun bazı özellikleri devre dışı bırakıldığını bildiren bir uyarı görüntülenir. Bir düğme, isterseniz tam çözüm çözümlemesini yeniden etkinleştirmenizi sağlar.

![Tam çözüm çözümlemesi askıya alma metni](../code-quality/media/fsa_alert.png)
