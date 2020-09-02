---
title: Hata ayıklama nedir?
description: Bir uygulamada hata ayıklamanın ne anlama geldiğini anlayın
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01317f3b8fa92cf1bc17c3745f708e0d3f26e5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62901245"
---
# <a name="what-is-debugging"></a>Hata ayıklama nedir?

Visual Studio hata ayıklayıcı güçlü bir araçtır. Nasıl kullanacağınızı göstermemiz için *hata ayıklayıcı*, *hata ayıklama*ve *hata ayıklama modu*gibi bazı terimler hakkında konuşmak istiyoruz. Bu şekilde, daha sonra hataları bulma ve düzeltme hakkında konuştuyoruz ve aynı şey hakkında konuşacağız.

## <a name="debugger-vs-debugging"></a>Hata ayıklayıcı ile hata ayıklama

*Hata ayıklama* terimi çok sayıda farklı şeyi ifade edebilir, ancak en çok harfi, koddan hataların kaldırılması anlamına gelir. Şimdi bunu yapmak için birçok yol vardır. Örneğin, kodunuzu tarayarak veya bir kod çözümleyici kullanarak hata ayıklaması yapabilirsiniz. Bir performans profil oluşturucusu kullanarak kodda hata ayıklaması yapabilirsiniz. Ya da hata *ayıklayıcı*kullanarak hata ayıklaması yapabilirsiniz.

Hata ayıklayıcı, çalışan uygulamanıza bağlanan ve kodunuzu incelemenize olanak tanıyan özel bir geliştirici aracıdır. Visual Studio için hata ayıklama belgelerinde, genellikle "hata ayıklama" söylediğimiz anlamına gelir.

## <a name="debug-mode-vs-running-your-app"></a>Hata ayıklama modu ile uygulamanızı çalıştırma

Uygulamanızı Visual Studio 'da ilk kez çalıştırdığınızda, araç çubuğunda (veya **F5**) ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "Hata ayıklamayı Başlat") yeşil ok düğmesine basarak başlatabilirsiniz. Varsayılan olarak, **hata ayıklama** değeri sol tarafta açılır. Visual Studio 'Yu kullanmaya yeni çalışıyorsanız, bu durum, uygulamanızda hata ayıklamanın, uygulamayı çalıştırmaya yönelik bir şey olduğunu, ancak bunlar temelde iki farklı görevi olduğu izlenimi verebilir.

![Bir hata ayıklama derlemesi seçin](../debugger/media/what-is-debugging-debug-build.png)

**Hata ayıklama** değeri bir hata ayıklama yapılandırmasını gösterir. Hata ayıklama yapılandırmasındaki uygulamayı başlattığınızda (yeşil oka veya **F5**tuşuna basın), uygulamayı hata *ayıklama modunda*başlatın, bu da uygulamanızı bir hata ayıklayıcı ekli olarak çalıştırıyorsunuz demektir. Bu, uygulamanızdaki hataları bulmaya yardımcı olması için kullanabileceğiniz bir hata ayıklama özelliklerinin tam kümesini sağlar.

Açık bir projeniz varsa, **hata ayıklamayı** belirten açılan seçiciyi seçin ve bunun yerine **yayın** ' ı seçin.

![Yayın derlemesi seçin](../debugger/media/what-is-debugging-release-build.png)

Bu ayarı değiştirdiğinizde, projenizi bir hata ayıklama yapılandırmasından Sürüm yapılandırmasına değiştirirsiniz. Visual Studio projeleri, programınız için ayrı sürüm ve hata ayıklama yapılandırmalarına sahiptir. Hata ayıklama için hata ayıklama sürümü ve son sürüm dağıtımı için yayın sürümü oluşturursunuz. Bir yayın derlemesi performans için iyileştirilmiştir, ancak hata ayıklama derlemesinin hata ayıklaması için daha iyidir.

## <a name="when-to-use-a-debugger"></a>Hata ayıklayıcı ne zaman kullanılır?

Hata ayıklayıcı, uygulamalarınızda hataları bulmak ve onarmak için gerekli olan bir araçtır. Ancak, bağlam papadır ve hataları veya hataları hızla ortadan kaldırmanıza yardımcı olması için atılabilir 'deki tüm araçlardan yararlanmak önemlidir. Bazen, doğru "araç" daha iyi bir kodlama uygulaması olabilir. Hata ayıklayıcıyı ve diğer araçlardan ne zaman kullanılacağını öğrenerek, hata ayıklayıcıyı daha etkin bir şekilde kullanmayı da öğreneceksiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, birkaç genel hata ayıklama kavramı öğrendiniz. Daha sonra, Visual Studio ile hata ayıklamayı ve daha az hata ile kod yazmayı öğrenmeye başlayabilirsiniz. Aşağıdaki makalelerde C# kod örnekleri gösterilmektedir, ancak kavramlar Visual Studio tarafından desteklenen tüm diller için geçerlidir.

> [!div class="nextstepaction"]
> [Başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
