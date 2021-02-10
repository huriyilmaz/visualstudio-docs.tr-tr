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
ms.workload:
- multiple
ms.openlocfilehash: a16aa4d445878ac8d357fa551e46552a1465bfe1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971355"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Visual Studio 'da çift yönlü diller için destek

Visual Studio, Arapça ve Ibranice metinleri doğru bir şekilde görüntüleyebilir ve nesne adları ve değerleri için çift yönlü metin girmenize olanak sağlar.

> [!NOTE]
> Çift yönlü dilleri girip görüntülemesi için, uygun dille yapılandırılmış bir Windows sürümüyle çalışmanız gerekir. Bu, uygun dil paketinin yüklü olduğu bir Windows Ingilizce sürümü ya da Windows 'un uygun şekilde yerelleştirilmiş sürümü olabilir.

## <a name="fully-supported-features"></a>Tam olarak desteklenen özellikler

Visual Studio 'da tasarım zamanında, metin girerken, nesneleri adlandırırken ve dosyaları kaydederken ve açarken çift yönlü dilleri kullanabilirsiniz.

### <a name="text-entry"></a>Metin girişi

Visual Studio Unicode 'U destekler, bu nedenle sisteminiz uygun yerel ayara ve giriş diline ayarlandıysa, Arapça veya Ibranice metin girebilirsiniz. (Arapça desteği keşide ve aksanlar içerir.)

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

   **Özellikler** penceresinde Arapça veya İbranice metin kullanabilirsiniz. Pencere, standart Windows tuş vuruşlarını kullanarak sağdan sola ve soldan sağa okuma düzeni arasında geçiş yapmanıza olanak **sağlar (** +  sağdan sola ve  + soldan sağa **kaydırma** için CTRL + SHIFT tuşlarına basın).

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

Visual Studio, sağdan sola okuma düzeni için sınırlı desteğe sahiptir. Varsayılan olarak, Visual Studio 'daki metin girişi denetimleri soldan sağa okuma düzeni kullanır. Çoğu durumda, okuma düzenini değiştirmek için standart Windows hareketlerini kullanabilirsiniz. Örneğin,  + **Özellikler** penceresini özellik değerleri için sağdan sola okuma düzenini destekleyecek şekilde değiştirmek için CTRL **+ SHIFT** tuşlarına basabilirsiniz.

Aşağıdaki konumlarda, Visual Studio 'da sağdan sola okuma düzeni desteklenmez:

- Visual Studio iletişim kutularındaki onay kutuları, açılan listeler ve diğer denetimler her zaman soldan sağa okuma düzeni kullanır.

- Kod Düzenleyicisi (ve metin düzenleyici) sağdan sola okuma düzenini desteklemez. Çift yönlü bir dilde metin girebilirsiniz, ancak okuma düzeni her zaman soldan sağa ayarlanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin](globalizing-and-localizing-applications.md)
