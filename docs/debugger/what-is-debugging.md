---
title: Hata ayıklama nedir?
description: Uygulamada hata ayıklamanın ne anlama geldiğini anlama
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4b2303480e242585801f8908f544df6409699d18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146582"
---
# <a name="what-is-debugging"></a>Hata ayıklama nedir?

Hata Visual Studio aracı güçlü bir araçtır. Bunu nasıl kullanabileceğinizi göstermeden önce hata ayıklayıcısı, hata ayıklama *ve* hata ayıklama modu gibi bazı terimler hakkında konuşmak *gerekir.* Bu şekilde, daha sonra hataları bulma ve düzeltme hakkında konuşacağız, aynı şey hakkında konuşacağız.

## <a name="debugger-vs-debugging"></a>Hata ayıklayıcısı ile hata ayıklama karşılaştırması

Hata ayıklama *terimi birçok* farklı anlama gelir ancak çoğu durumda kodundaki hataların kaldırılması anlamına gelir. Şimdi bunu yapmak için birçok yol vardır. Örneğin, yazım hataları için kodunuzu tarar veya bir kod çözümleyicisi kullanarak hata ayıkabilirsiniz. Performans profili oluşturma kullanarak kodda hata ayıkabilirsiniz. Veya hata ayıklayıcısı kullanarak hata *ayıklarsanız.*

Hata ayıklayıcı, çalışan uygulamanıza ekleyen ve kodunuzu incelemenize olanak sağlayan çok özel bir geliştirici aracıdır. Hata ayıklama belgelerinde Visual Studio, "hata ayıklama" dey irdele bu genellikle bunu ifade etmektir.

## <a name="debug-mode-vs-running-your-app"></a>Hata ayıklama modu ve uygulama çalıştırma karşılaştırması

Uygulamanızı uygulamada ilk kez Visual Studio, araç çubuğundaki (veya F5) ![](../debugger/media/dbg-tour-start-debugging.png "Hata Ayıklamayı Başlat") Hata Ayıklamayı Başlat düğmesine basarak **başlatabilirsiniz.** Varsayılan olarak, **hata** ayıklama değeri sol tarafta açılan listesinde görünür. Uygulamanıza yeni Visual Studio, bu durum uygulama hata ayıklamanın, uygulamanızı çalıştırmayla ilgili olduğu izlenimini bıraksa da temelde iki farklı görevdir.

![Hata ayıklama derlemesi seçme](../debugger/media/what-is-debugging-debug-build.png)

Hata **ayıklama değeri** bir hata ayıklama yapılandırmasını gösterir. Uygulamayı bir hata ayıklama yapılandırmasında başlatarak (yeşil ok veya **F5** tuşuna basın) uygulamayı hata ayıklama modunda başlatın. Bu, uygulamanın ekli bir hata ayıklayıcı ile çalıştırılan bir uygulama olduğu anlamına gelir.  Bu, uygulamadaki hataları bulmaya yardımcı olmak için kullanabileceğiniz tam hata ayıklama özellikleri kümesine olanak sağlar.

Açık bir projeniz varsa, Hata Ayıkla'nın bulunduğu açılır liste seçiciyi seçin ve bunun **yerine** **Yayın'ı** seçin.

![Yayın derlemesi seçme](../debugger/media/what-is-debugging-release-build.png)

Bu ayarı değiştirseniz, projenizi hata ayıklama yapılandırmasından sürüm yapılandırmasına değiştirirsiniz. Visual Studio projelerinin programınız için ayrı sürüm ve hata ayıklama yapılandırmaları vardır. Hata ayıklama için hata ayıklama sürümünü ve son sürüm dağıtımının yayın sürümünü derlemenizi sağlar. Yayın derlemesi performans için iyileştirilmiştir, ancak hata ayıklama derlemesi hata ayıklama için daha iyidir.

## <a name="when-to-use-a-debugger"></a>Hata ayıklayıcının ne zaman kullanımı gerekir?

Hata ayıklayıcı, uygulamalarınızdaki hataları bulmak ve düzeltmek için temel bir araçtır. Ancak bağlam her zaman önemlidir ve hataları veya hataları hızla ortadan kaldırmanıza yardımcı olmak için atılabilir tüm araçlardan faydalanmanız önemlidir. Bazen doğru "araç" daha iyi bir kodlama uygulaması olabilir. Hata ayıklayıcının ne zaman ve başka bir araçla ne zaman kullanılamayacaklarını öğrenerek, hata ayıklayıcıyı daha verimli kullanmayı da öğrenirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede bazı genel hata ayıklama kavramlarını öğrendinsiniz. Bundan sonra, daha az hatayla Visual Studio hata ayıklamayı ve kod yazmayı öğrenmeye başlayabilirsiniz. Aşağıdaki makalelerde C# kod örnekleri verilmiştir ancak kavramlar, C# tarafından desteklenen tüm diller için Visual Studio.

> [!div class="nextstepaction"]
> [Başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
