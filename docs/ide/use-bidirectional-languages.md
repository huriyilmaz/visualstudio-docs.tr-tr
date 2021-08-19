---
title: Arapça ve Ibranice desteği
description: Arapça ve Ibranice metinleri görüntüleme ve nesne adları ve değerleri için çift yönlü metin girme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ca94c650c88cb477e99812d87e2ff42146916bcf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116831"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Visual Studio Çift yönlü diller için destek

Visual Studio, arapça ve ibranice metinleri doğru bir şekilde görüntüleyebilir ve nesne adları ve değerleri için çift yönlü metin girmenize olanak sağlar.

> [!NOTE]
> çift yönlü dilleri girip görüntülemesi için, uygun dille yapılandırılmış bir Windows sürümüyle çalışmanız gerekir. bu, uygun dil paketinin yüklü olduğu bir Windows ingilizce sürümü ya da Windows uygun şekilde yerelleştirilmiş sürümü olabilir.

## <a name="fully-supported-features"></a>Tam olarak desteklenen özellikler

tasarım zamanında Visual Studio metin girerken, nesneleri adlandırırken ve dosyaları kaydederken ve açarken çift yönlü dilleri kullanabilirsiniz.

### <a name="text-entry"></a>Metin girişi

Visual Studio Unicode destekler, bu nedenle sisteminiz uygun yerel ayara ve giriş diline ayarlandıysa, arapça veya ibranice metin girebilirsiniz. (Arapça desteği keşide ve aksanlar içerir.)

### <a name="arabic-or-hebrew-object-names"></a>Arapça veya Ibranice nesne adları

Çözümler, projeler, dosyalar, klasörler ve benzeri adları atamak için çift yönlü dilleri kullanabilirsiniz. Kodda, değişkenler, sınıflar, nesne, öznitelikler, meta veriler ve diğer öğelerin adları için çift yönlü dilleri kullanabilirsiniz. Arapça ile çalışırken, keşide ve aksanlar dahil olmak üzere herhangi bir Arapça karakter kullanabilirsiniz.

Aşağıdaki öğeler Arapça veya Ibranice kullanılarak adlandırılabilir ve Visual Studio tarafından doğru şekilde işlenir:

- Proje yoluna dahil ettiğiniz tüm klasörler dahil olmak üzere çözüm, proje ve dosya adları.

   **Çözüm Gezgini** çözüm ve öğe adlarını doğru şekilde görüntüler.

- Dosya içeriği.

   Dosyaları Unicode kodlamalı veya seçili bir kod sayfasıyla açabilir veya kaydedebilirsiniz.

- Veri öğeleri.

   **Sunucu Gezgini** , bu öğeleri doğru şekilde görüntüler ve bunları düzenleyebilirsiniz.

- Windows panosuna kopyalanmış öğeler.

- Öznitelikler ve meta veriler.

- Özellik değerleri.

   **Özellikler** penceresinde Arapça veya İbranice metin kullanabilirsiniz. pencere, standart Windows tuş vuruşlarını kullanarak sağdan sola ve soldan sağa okuma düzeni arasında geçiş yapmanıza olanak **sağlar (** +  sağdan sola ve  + soldan sağa **kaydırma** için ctrl + shıft tuşlarına basın).

- Kod ve sabit metin.

   Kod Düzenleyicisi 'nde, sınıfları, işlevleri, değişkenleri, özellikleri, dize değişmez değerlerini, özniteliklerini ve benzerlerini adlandırmak için Arapça veya Ibranice kullanabilirsiniz. Ancak, düzenleyici sağdan sola okuma düzenini desteklemez; metin her zaman sol kenar boşluğunda başlar.

   > [!TIP]
   > Dize sabit değerlerini programlarınıza sabit kodlamak yerine kaynak dosyalarına yerleştirmeniz gerekir. Daha fazla bilgi için bkz. [Masaüstü uygulamalarındaki kaynaklar (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Arapça ve Ibranice adlı nesnelere nasıl başvurabileceğiniz tutarlı olmalıdır. Örneğin, bir Arap değişkenini adlandırırken keşide kullanırsanız, bu değişkene veya hatalara başvururken her zaman keşide kullanmanız gerekir.

- Kod açıklamaları. Arapça veya Ibranice ile yorum oluşturabilirsiniz. Bu dilleri açıklama Oluşturucu aracında da kullanabilirsiniz.

### <a name="file-encoding"></a>Dosya kodlama

Dosyaları dile özgü veya Unicode kodlamalı bir şekilde kaydedebilir ve açabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: kodlamaya sahip dosyaları kaydetme ve açma](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Sağdan sola okuma düzeni

Visual Studio sağdan sola okuma düzeni için sınırlı desteğe sahiptir. varsayılan olarak Visual Studio ' deki metin girişi denetimleri soldan sağa okuma sırasını kullanır. çoğu durumda, okuma düzenini değiştirmek için standart Windows hareketlerini kullanabilirsiniz. Örneğin,  + **Özellikler** penceresini özellik değerleri için sağdan sola okuma düzenini destekleyecek şekilde değiştirmek için CTRL **+ SHIFT** tuşlarına basabilirsiniz.

Sağdan sola okuma düzeni Visual Studio aşağıdaki konumlarda desteklenmez:

- Visual Studio iletişim kutularındaki onay kutuları, açılan listeler ve diğer denetimler her zaman soldan sağa okuma düzeni kullanır.

- Kod Düzenleyicisi (ve metin düzenleyici) sağdan sola okuma düzenini desteklemez. Çift yönlü bir dilde metin girebilirsiniz, ancak okuma düzeni her zaman soldan sağa ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin](globalizing-and-localizing-applications.md)
