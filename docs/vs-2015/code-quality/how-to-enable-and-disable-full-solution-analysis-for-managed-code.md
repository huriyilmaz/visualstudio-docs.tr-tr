---
title: 'Nasıl yapılır: yönetilen kod için tam çözüm analizini etkinleştirme ve devre dışı bırakma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 72b27bf9dcc1f0ee8a222ac701f2ffae4fc68614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646285"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Nasıl yapılır: Yönetilen Kod İçin Tam Çözüm Analizini Etkinleştirme ve Devre Dışı Bırakma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTUN
> Bu konu yalnızca Visual Studio 2015 güncelleştirme 3 RC ve üzeri için geçerlidir.

 *Tam çözüm Analizi* , kod analizi sorunlarını yalnızca çözümünüzdeki açık Visual c# veya Visual Basic dosyalarında ya da çözümünüzde hem açık hem de kapalı Visual C# ya da Visual Basic dosyalarında görüp görmeyeceğinizi seçmenize olanak tanıyan bir Visual Studio özelliğidir.

 Tüm dosyalardaki tüm sorunları görebilmekle çalışırken, çözümünüz çok büyükse veya çok fazla dosya içeriyorsa, bu, dikkat dağıtıcı ve hatta bunun yavaşlamasına neden olabilir.  Gösterilen sorun sayısını sınırlandırmak ve Visual Studio performansını geliştirmek için tam çözüm analizini devre dışı bırakabilirsiniz. İsterseniz bu özelliği kolayca yeniden etkinleştirebilirsiniz.

#### <a name="to-toggle-full-solution-analysis"></a>Tam çözüm analizine geçiş yapmak için

1. Visual Studio 'daki ana menüde, **Seçenekler** iletişim kutusunu görüntülemek için **Araçlar** &#124; **Seçenekler** ' i seçin.

2. **Seçenekler** iletişim kutusunda **C#** veya **temel** &#124; **Gelişmiş**&#124; **metin düzenleyici** ' yi seçin.

3. Tam çözüm analizini etkinleştirmek için **tam çözüm analizini etkinleştir** onay kutusunu seçin veya devre dışı bırakmak için kutuyu temizleyin. İşiniz bittiğinde **Tamam** düğmesini seçin.

     ![Tam çözüm analizini etkinleştir onay kutusu.](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Tam çözüm analizini etkinleştirme ve devre dışı bırakma sonuçları
 Aşağıdaki ekran görüntüsünde, tam çözüm Analizi etkinleştirildiğinde sonuçları görebilirsiniz. Çözümdeki *Tüm* dosyalardaki tüm hatalar ve kod analizi sorunları, dosyaların açık olup olmamasına bakılmaksızın görünür.

 ![Tam çözüm Analizi etkin.](../code-quality/media/fsa-enabled.png "FSA_Enabled")

 Aşağıdaki ekran görüntüsünde, tam çözüm analizini devre dışı bıraktıktan sonra aynı çözümün sonuçları gösterilmektedir. Yalnızca açık çözüm dosyalarındaki hatalar ve kod analizi sorunları Hata Listesi görüntülenir.

 ![Tam çözüm Analizi devre dışı.](../code-quality/media/fsa-disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Tam çözüm analizini otomatik olarak devre dışı bırakma
 Visual Studio, 200 MB veya daha az sistem belleği olduğunu algılarsa, etkin olduğunda tam çözüm analizini (diğer bazı özellikler de dahil) otomatik olarak devre dışı bırakır. Böyle bir durum oluşursa, bunu size bildiren bir uyarı belirir. Bunu yapmak istiyorsanız, bir düğme tam çözüm analizini yeniden etkinleştirmenizi sağlar.

 ![Tam çözüm analizini askıya alarak uyarı metni](../code-quality/media/fsa-alert.png "FSA_Alert")

## <a name="additional-details"></a>Ek ayrıntılar
 Varsayılan olarak, tam çözüm Analizi Visual Basic için etkinleştirilmiştir ve Visual C# için devre dışı bırakılır.

 Visual Studio güncelleştirme 3 RC, tam çözüm Analizi etkin olsa bile, bellek kullanımını önemli ölçüde azaltan ve CPU süresini aşacak şekilde azaltan gelişmiş bir kod Çözümleyicisi tanılama v2 altyapısı içerir.
