---
title: Iki yönlü dillerde uygulamalar oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b3d8649484178a537ed4af7bdde044a29893275
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619257"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Çift Yönlü Dillerde Uygulamalar Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arapça ve Ibranice gibi sağdan sola yazılan dillerde metni doğru şekilde görüntüleyen uygulamalar oluşturmak için Visual Studio 'Yu kullanabilirsiniz. Bazı özellikler için, yalnızca özellikleri ayarlayabilirsiniz. Diğer durumlarda, koddaki özellikleri uygulamanız gerekir.

> [!NOTE]
> Çift yönlü dilleri girip görüntülemesi için, uygun dille yapılandırılmış bir Windows sürümüyle çalışmanız gerekir. Bu, uygun dil paketinin yüklü olduğu bir Windows Ingilizce sürümü ya da Windows 'un uygun şekilde yerelleştirilmiş sürümü olabilir.

## <a name="types-of-application-that-support-bi-directional-languages"></a>Iki yönlü dilleri destekleyen uygulama türleri

1. Windows uygulamaları. Çift yönlü metin, sağdan sola okuma düzeni ve yansıtma (pencere, menü ve iletişim kutularının düzenini ters çevirme) için destek içeren tam çift yönlü uygulamalar oluşturabilirsiniz. Yansıtma haricinde, bu özellikler varsayılan olarak veya özellik ayarları olarak kullanılabilir. Yansıtma, ileti kutuları gibi bazı özellikler için kendiliğinden desteklenir. Ancak, diğer durumlarda kodda yansıtma uygulamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms uygulamalar için çift yönlü destek](https://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2).

2. Web uygulamaları. Web Hizmetleri, UTF-8 ve Unicode metin göndermeyi destekler ve alıyor ve bunları iki yönlü dilleri içeren uygulamalar için uygun hale getirir. Web istemcisi uygulamaları, Kullanıcı arabirimi için tarayıcıları kullanır, bu nedenle bir Web uygulamasındaki iki yönlü destek derecesi, kullanıcının tarayıcısının bu iki yönlü özellikleri ne kadar iyi desteklediğine bağlıdır. Visual Studio 'da Arapça veya Ibranice metin, sağdan sola okuma düzeni, dosya kodlama ve yerel kültür ayarları desteğiyle uygulamalar oluşturabilirsiniz. Daha fazla bilgi için bkz. [ASP.NET Web uygulamaları Için çift yönlü destek](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03).

3. Konsol uygulamaları. Konsol uygulamaları, iki yönlü diller için metin desteği içermez. Bu, Windows 'un konsol uygulamalarıyla nasıl çalıştığı hakkında bir sonucudur.

## <a name="visual-studio-features-that-are-fully-supported"></a>Tam olarak desteklenen Visual Studio özellikleri
 Visual Studio 'da tasarım zamanında, iki yönlü dilleri şu yollarla kullanabilirsiniz:

- **Metin girişi** Visual Studio Unicode 'U destekler, bu nedenle sisteminiz uygun yerel ayara ve giriş diline ayarlandıysa, Arapça veya Ibranice metin girebilirsiniz. (Arapça desteği keşide ve aksanlar içerir.)

- **Nesne adları** Çözümler, projeler, dosyalar, klasörler ve benzeri adlar atamak için çift yönlü dilleri kullanabilirsiniz. Kodda, değişkenlerin, sınıfların, nesnenin, özniteliklerin, meta verilerin ve diğer öğelerin adları için çift yönlü dilleri kullanabilirsiniz.

- **Dosya kodlama** Dosyaları dile özgü veya Unicode kodlamalı bir şekilde kaydedebilir ve açabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kodlamaya sahip dosyaları kaydetme ve açma](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-or-no-support"></a>Sınırlı veya desteği olmayan özellikler
 Çift yönlü dil uygulamalarıyla yaygın olarak kullanılan diğer özellikler, Visual Studio 'da veya bazı durumlarda hiç değil, tümüyle desteklenmez. Bu güncelleştirmeler şunlardır:

- **Sağdan sola okuma düzeni** Varsayılan olarak, Visual Studio 'da kullandığınız metin girişi denetimleri soldan sağa okuma düzeni kullanır. Çoğu durumda, okuma düzenini değiştirmek için standart Windows hareketlerini kullanabilirsiniz. Örneğin, özellik değerleri için sağdan sola okuma düzenini desteklemek üzere Özellikler penceresi değiştirmek için CTRL + sağ SHIFT tuşlarına basabilirsiniz.

  Ancak, sağdan sola okuma düzeni Visual Studio 'da her yerde desteklenmez. Özel durumlar şunları içerir:

  - Visual Studio iletişim kutularındaki onay kutuları, açılan listeler ve diğer denetimler her zaman soldan sağa okuma düzeni kullanır.

  - Kod Düzenleyicisi (ve metin düzenleyici) sağdan sola okuma düzenini desteklemez. Bir çift yönlü dilde metin girebilirsiniz, ancak okuma sırası her zaman soldan sağa olur.

## <a name="naming-things-using-arabic-or-hebrew-text"></a>Arapça veya Ibranice metin kullanarak şeyler adlandırma
 Klasörler, değişkenler veya diğer nesnelere ad atamak için Arapça veya Ibranice metin kullanabilirsiniz. Arapça ile çalışırken, keşide ve aksanlar dahil olmak üzere herhangi bir Arapça karakter kullanabilirsiniz.

 Aşağıdaki öğeler Arapça veya Ibranice kullanılarak adlandırılabilir ve Visual Studio 'da doğru şekilde işlenecektir:

- Proje yoluna dahil ettiğiniz tüm klasörler dahil olmak üzere çözüm, proje ve dosya adları. Çözüm Gezgini, çözüm ve öğe adlarını doğru şekilde görüntüler.

- Dosya içeriği. Dosyaları Unicode kodlamalı veya seçili bir kod sayfasıyla açabilir veya kaydedebilirsiniz.

    > [!NOTE]
    > Kod Düzenleyicisi özel bir durumdur. Ayrıntılar için aşağıya bakın.

- Veri öğeleri. **Sunucu Gezgini** , bu öğeleri doğru bir şekilde görüntüler ve bunları düzenlemenizi sağlar.

- Windows panosuna kopyalanmış öğeler.

- Öznitelikler ve meta veriler.

- Özellik değerleri. Özellikler penceresi Arapça veya Ibranice metin kullanabilirsiniz. Pencere, standart Windows tuş vuruşlarını kullanarak sağdan sola ve soldan sağa okuma düzeni arasında geçiş yapmanıza olanak sağlar (sağdan sola için CTRL + sağ SHIFT ve soldan sağa için CTRL + Leftshıft).

- Kod ve sabit metin. Kod düzenleyicisinde (aynı zamanda metin Düzenleyicisi de bulunur), sınıfları, işlevleri, değişkenleri, özellikleri, dize değişmez değerlerini, özniteliklerini ve benzerlerini adlandırmak için Arapça veya Ibranice kullanabilirsiniz. Ancak, düzenleyici sağdan sola okuma düzenini desteklemez; metin her zaman sol kenar boşluğunda başlar.

    > [!TIP]
    > Dize sabit değerlerini programlarınıza sabit kodlamak yerine kaynak dosyalarına yerleştirmeniz önerilir. Daha fazla bilgi için bkz. [Izlenecek yol: yerelleştirme Windows Forms](https://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5).

    > [!NOTE]
    > Bu dillerde adlandırılan nesnelere nasıl başvurabileceğiniz ile tutarlı olmanız gerekir. Örneğin, bir Arap değişkenini adlandırırken keşide kullanırsanız, bu değişkene başvururken her zaman keşide kullanmanız gerekir, aksi takdirde hatalar olur.

- Kod açıklamaları. Arapça veya Ibranice ile yorum oluşturabilirsiniz. Bu dilleri açıklama Oluşturucu aracında da kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [Windows Forms uygulamalar için Iki yönlü](https://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2) [destek ASP.NET Web uygulamaları Için çift yönlü destek](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03) [uygulamaları](../ide/globalizing-applications.md) [Yerelleştirme](../ide/localizing-applications.md) uygulamaları
