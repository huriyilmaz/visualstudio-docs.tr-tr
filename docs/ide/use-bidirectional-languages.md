---
title: Arapça ve İbranice desteği
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bccfccb77c5a80fd2630680564f88f08d7ca5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592002"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Visual Studio'da çift yönlü dillere destek

Visual Studio Arapça ve İbranice metni doğru görüntüleyebilir ve nesne adları ve değerleri için çift yönlü metin girmenizi sağlar.

> [!NOTE]
> Çift yönlü dilleri girmek ve görüntülemek için, uygun dille yapılandırılan bir Windows sürümüyle çalışıyor olmalısınız. Bu, uygun dil paketinin yüklü olduğu Windows'un İngilizce sürümü veya Uygun şekilde yerelleştirilmiş Windows sürümü olabilir.

## <a name="fully-supported-features"></a>Tam destekli özellikler

Visual Studio'da tasarım zamanında, metin girerken, nesneleri adlandırırken ve dosyaları kaydederken ve açarken çift yönlü dilleri kullanabilirsiniz.

### <a name="text-entry"></a>Metin girişi

Visual Studio Unicode'u destekler, böylece sisteminiz uygun yerel ve giriş diline ayarlanmışsa, arapça veya İbranice metin girebilirsiniz. (Arapça destek Kashida ve Diacritics içerir.)

### <a name="arabic-or-hebrew-object-names"></a>Arapça veya İbranice nesne adları

Çözümlere, projelere, dosyalara, klasörlere ve benzerlerine ad atamak için çift yönlü dillerk kullanabilirsiniz. Kodda, değişkenler, sınıflar, nesne, öznitelikler, meta veriler ve diğer öğelerin adları için çift yönlü dillerk kullanabilirsiniz. Arapça ile çalışırken, Kashida ve Diacritics dahil olmak üzere herhangi bir Arapça karakter kullanabilirsiniz.

Aşağıdaki öğeler Arapça veya İbranice kullanılarak adlandırılabilir ve Visual Studio tarafından doğru şekilde işlenir:

- Proje yoluna eklediğiniz klasörler de dahil olmak üzere çözüm, proje ve dosya adları.

   **Çözüm Gezgini** çözüm ve öğe adlarını doğru görüntüler.

- Dosya içeriği.

   Unicode kodlaması yla veya seçili bir kod sayfasıyla dosyaları açabilir veya kaydedebilirsiniz.

- Veri elemanları.

   **Sunucu Gezgini** bu öğeleri doğru görüntüler ve bunları ayarlayabilirsiniz.

- Öğeler Windows Panosuna kopyalanır.

- Öznitelikler ve meta veriler.

- Özellik değerleri.

   **Özellikler** penceresinde Arapça veya İbranice metin kullanabilirsiniz. Pencere, standart Windows tuş vuruşlarını (sağdan sola**ctrl**+**RightShift** ve soldan sağa) **Ctrl**+**LeftShift'i** kullanarak sağdan sola ve soldan sağa okuma sırası arasında geçiş yapmanızı sağlar.

- Kod ve gerçek metin.

   Kod düzenleyicisinde, sınıfları, işlevleri, değişkenleri, özellikleri, dize literalleri, öznitelikleri ni, vebenzeri adlarını vermek için Arapça veya İbranice'yi kullanabilirsiniz. Ancak, editör sağdan sola okuma sırasını desteklemez; metin her zaman sol kenar boşluğunda başlar.

   > [!TIP]
   > Dize literallerini programlarınıza kodlamak yerine kaynak dosyalarına yerleştirmelisiniz. Daha fazla bilgi için [masaüstü uygulamalarındaki Kaynaklar 'a (.NET Framework)](/dotnet/framework/resources/index)bakın.

   > [!NOTE]
   > Arapça ve İbranice adlı nesnelere nasıl atıfta bulunduğunuz konusunda tutarlı olmalısınız. Örneğin, Arapça bir değişkeni adlandırırken Kashida kullanıyorsanız, bu değişkene atıfta bulunduğınızda her zaman Kashida kullanmanız gerekir veya hatalar ortaya çıkacaktır.

- Kod açıklamaları. Arapça veya İbranice yorum oluşturabilirsiniz. Bu dilleri yorum oluşturucu aracında da kullanabilirsiniz.

### <a name="file-encoding"></a>Dosya kodlama

Dile özgü veya Unicode kodlaması ile dosyaları kaydedebilir ve açabilirsiniz. Daha fazla bilgi için [bkz: Kodlama ile dosyaları kaydet ve aç.](../ide/how-to-save-and-open-files-with-encoding.md)

## <a name="right-to-left-reading-order"></a>Sağdan sola okuma sırası

Visual Studio sağdan sola okuma sırası için sınırlı destek vardır. Varsayılan olarak, Visual Studio'daki metin giriş denetimleri soldan sağa okuma sırasını kullanır. Çoğu durumda, okuma sırasını değiştirmek için standart Windows hareketlerini kullanabilirsiniz. Örneğin, özellik değerleri için sağdan sola okuma sırasını desteklemek için **Özellikler** penceresini değiştirmek için **Ctrl**+**RightShift** tuşuna basabilirsiniz.

Visual Studio'da sağdan sola okuma sırası aşağıdaki yerlerde desteklenmez:

- Visual Studio iletişim kutularındaki kutuları, açılır listeleri ve diğer denetimleri onaylar, her zaman soldan sağa okuma sırasını kullanır.

- Kod düzenleyicisi (ve metin düzenleyicisi) sağdan sola okuma sırasını desteklemez. Metni çift yönlü bir dilde girebilirsiniz, ancak okuma sırası her zaman soldan sağadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Küreselleştirilmiş ve yerelleştirilmiş uygulamalar geliştirme](globalizing-and-localizing-applications.md)
