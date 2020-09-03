---
title: Kod Haritası Çözümleyicileri kullanarak olası sorunları bulun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc5d185640c9623a2213aaf7ad50fa68a088b15c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669624"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Kod haritası çözümleyicilerini kullanarak olası sorunları bulma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşırı karmaşık olabilecek veya geliştirme gerektirebilecek kodu tanımlamanızı sağlamak için kod haritaları üzerinde çözümleyiciler çalıştırın. Örneğin, bu Çözümleyicileri kullanabilirsiniz:

|**Olan kodu bulmak için**|**Bu alanı inceleyerek**|
|-------------------------------|--------------------------------------------|
|Döngüler veya dairesel bağımlılıklar|Bunları basitleştirebilir ve bu döngüleri bölebilir olup olmayacağını düşünebilirsiniz.|
|Çok fazla bağımlılık|Bunlar çok fazla işlev gerçekleştiriyor veya bu alanların değiştirilmesini belirlemede etkiler. İyi biçimlendirilmiş bir kod eşlemesi, en az sayıda bağımlılığı gösterecektir. Kodu korumak, değiştirmek, test etmek ve yeniden kullanmak daha kolay hale getirmek için, bu alanların daha açık bir şekilde tanımlanması veya benzer işlevleri gerçekleştiren kodu birleştirebilmeniz için yeniden düzenleme yapıp yapamayacağını göz önünde bulundurun.|
|Bağımlılık yok|Bunlar gereklidir veya bu kodu kaldırmanız gerekip gerekmediğini belirtir.|

## <a name="analyze-code-maps"></a>Kod eşlemelerini çözümle

1. Harita araç çubuğunda, çalıştırmak istediğiniz **Düzen**, **çözümleyiciler**ve ardından çözümleyici ' yi seçin:

   |**Analyzer**|**Olan düğümleri belirlemek için**|
   |------------------|--------------------------------|
   |**Döngüsel başvurular Çözümleyicisi**|Birbirini dairesel bağımlılıklardır. **Note:**  Grupları genişlettiğinizde, **Genel türler** grubundaki döngüsel bağımlılıklar haritada gösterilmez.|
   |**Hub Çözümleyicisi bulma**|Yüksek oranda bağlı düğümlerin üst %25 ' i<br /><br /> **Haritadaki tüm diğer düğümleri gizlemek için**<br /><br /> -Haritanın kısayol menüsünü açın, **Gelişmiş**' i seçin, Seç ' i **seçin**ve **seçimini gizleyin**.<br />     Harita seçilmemiş düğümleri gizler ve çözümleyici yeni düğümleri hub olarak tanımlar.|
   |**Başvurulmayan düğümler Çözümleyicisi**|Diğer düğümlerden başvuruları yoktur. **Dikkat:**  Kodun kullanılmadığını varsaymadan önce bu durumların her birini doğrulayın. XAML bağımlılıkları ve çalışma zamanı bağımlılıkları gibi belirli bağımlılıklar kodda statik olarak bulunamaz.|

   Kod Haritası Çözümleyicileri, uygulandıktan sonra çalışmaya devam edecektir. Eşlemeyi değiştirirseniz, uygulanan tüm çözümleyiciler, güncelleştirilmiş Haritayı otomatik olarak yeniden işler. Bir çözümleyici çalıştırmayı durdurmak için harita araç çubuğunda **Düzen**, **çözümleyiciler**' ı seçin. Seçili çözümleyici 'yi devre dışı bırakın.

> [!TIP]
> Çok büyük bir haritanız varsa, bir çözümleyici çalıştırmak yetersiz bellek özel durumuna neden olabilir. Bu durumda, kapsamını daraltmak için haritayı düzenleyin veya daha küçük bir tane oluşturun ve ardından çözümleyici 'yi çalıştırın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md) [, hata ayıklama sırasında çağrı yığınında uygulamalar eşleme yöntemlerinizde](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md) [hata ayıklamak için kod haritaları kullanın](../modeling/use-code-maps-to-debug-your-applications.md)
