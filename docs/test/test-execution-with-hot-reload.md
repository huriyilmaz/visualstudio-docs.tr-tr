---
title: Çalışırken Yeniden Yükleme ile Yürütmeyi Test Çalışırken Yeniden Yükleme
description: Visual Studio'da Test Gezgini ile sık Visual Studio. Bu konu, etkin yeniden yüklenen test yürütmeyi etkinleştirmeyi, nerede destekleniyorsa ve kullanırken neler beklemeniz gerekir? konusunu kapsar.
ms.date: 10/15/2021
ms.topic: how-to
author: vritant24
ms.author: vrbhardw
manager: manishj
ms.technology: vs-ide-test
ms.workload:
- VB
- CSharp
ms.openlocfilehash: 358f55acf7bc54059a2f21624b26c45021815c64
ms.sourcegitcommit: 0257750be796cc46e01cebd8976f637743d29417
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "130290609"
---
# <a name="test-execution-with-hot-reload"></a>Çalışırken Yeniden Yükleme ile Yürütmeyi Test Çalışırken Yeniden Yükleme

Test çalıştırmaları Visual Studio testlerinizi yürütmek için [Test](https://github.com/microsoft/vstest/) Platformunu kullanmadan önce diskte ikili dosyaları güncelleştirmek için projeyi oluşturmanızı içerir. Derlemenin içindeki Visual Studio, kodda yapılan [değişikliklerin türüne](https://github.com/dotnet/roslyn/blob/296e0fada42f241d338b169c3c6c6189101ef0b7/docs/wiki/EnC-Supported-Edits.md) bağlı olarak değişebilir. Daha büyük çözümler için derlemeler test çalıştırması için en pahalı bölüm olabilir. 2022 Visual Studio sonraki bir senaryoda, desteklenen senaryolar için derlemeleri atlayarak test yürütmeyi hızlandırmak için, etkin yeniden yükleme ile test yürütme etkinleştirilebilir.

## <a name="what-is-supported"></a>Desteklenen nedir?
- .NET 6.0 ve üstlerini hedef alan C# ve VB projeleri
- DEBUG yapılandırması için yerleşik test projeleri
- Visual Studio 2022 ve üzerinde

## <a name="enable-test-execution-with-hot-reload"></a>Çalışırken Yeniden Yükleme ile Test Yürütmeyi Etkinleştirme
  >    >  **"(Deneysel) .NET 6** ve üstlerini hedef alan C# ve VB test projeleri için Test Seçenekleri "(Deneysel) Etkin Yeniden Yüklenen Test Çalıştırmalarını Etkinleştir" seçeneklerini kullanarak bu özelliği etkinleştirin.
![Test Seçenekleri sayfasındaki Etkin Yeniden Yüklenen Test Çalıştırmalarını Etkinleştir düğmesinin Visual Studio görüntüsü. Bu seçildiğinde, testler yürütmesi desteklenen senaryolar için hot reload kullanır](./media/test-execution-hot-reload-option.png)

## <a name="why-is-it-experimental"></a>Neden Deneyseldir?
Bu, yaygın olarak kullanılan kod doğrulama yolunu değiştirerek test yürütmenin yeni bir yoludur. Ayrıca kullanıcılardan daha fazla geri bildirim aldıklarından bu özellikle ilgili kullanıcı deneyiminin değişmesini bekliyoruz. Bu iki nedenle bu özelliği şu anda "deneysel" olarak etiketlemiştik.

## <a name="how-it-works"></a>Nasıl çalışır?
Seçenek etkinleştirildikten sonra, Test Gezgini mümkün olduğunda test yürütmeyi otomatik olarak etkin yeniden yükleme ile kullanır. Sık sık yeniden yükleme yapılamayacaksa, testlerin yapılma ve çalıştırmanın normal davranışına geri döner. Testleri çalıştıran bir kullanıcı olarak iş akışınız üzerinde herhangi bir değişiklik yapmak zorunda olmazsınız (yani kodu düzenlemeye ve testleri çalıştırmaya devam edebilirsiniz).

Daha sonra, yapılan değişiklikleri [](../debugger/edit-and-continue.md) belirlemek için çalışma zamanında [C#/VB](https://devblogs.microsoft.com/dotnet/introducing-net-hot-reload/) kodunu düzenlemeye Çalışırken Yeniden Yükleme yeni yayınlanan Çalışırken Yeniden Yükleme düzenle ve Devam Edin altyapısını kullanıyoruz. Bu nedenle, yalnızca "kaba düzenlemeler" olmadan yeniden yükleme gerçekleştirebilir ve bu durumda testlerinizi yürütmeden önce yeniden oluşturmamız gerekir. Desteklenen düzenlemeler hakkında daha fazla bilgi için Düzenle ve Devam [Edin belgelerini okuyun](https://github.com/dotnet/roslyn/blob/296e0fada42f241d338b169c3c6c6189101ef0b7/docs/wiki/EnC-Supported-Edits.md)

## <a name="how-much-faster-will-the-test-execution-be"></a>Test yürütmesi ne kadar hızlı olacak?
Bu özelliğin ne kadar zaman tasarrufuna sahip olduğunu tahmin etmek için birçok değişken vardır. Örneğin:
- Proje derlemesi ne kadar sürer?
- Ne tür bir düzenleme yapıldı?
- Dosyanın düzenlemenin ne kadar büyük olduğu.
- Düzenlemenin nerede yapılmış olduğu (yaprak proje olup olmadığını).

Sonuç olarak, hız geliştirmeleri doğrudan ilgili test çalıştırması sırasında meydana gelecek derleme süresiyle ilgili olur.

### <a name="notes"></a>Notlar
- seçeneği etkinleştirdikten veya bir proje derlemesi Visual Studio ilk test çalıştırması.
- Testler çalıştırıldıklarında düzenleyicide dosyalar kaydedilemiyor olabilir. Bu sorunları çözmek ve iade etmek için tam derlemeyi (Ctrl+Shift+B) tamamlayasınız.
- Sık sık yeniden yüklenen test yürütmesi oluştuğunda diskte ikili dosyalar güncelleştirilmez.
- Sık yüklenmiş test yürütmesi, Test Gezgini'nde "**Test** Çalıştırma Tüm Testleri ", " Görünümde Tüm Testleri Çalıştır" ile çalışmıyor ve test gezgininde çözüm düğümünden Tüm Testleri  >  Çalıştır ile Çözüm Gezgini.  Özellik, şu anda çözümün tamamının üretile bir bütün olduğunu garantileyene kadar bu komutlarla birlikte çalışmaz.
- Desteklenmeyen hedef çerçeveler (.NET 6.0'dan düşük) ile testler çalıştırıldıklarında, bir proje derlemesi oluşur.
- Diskte neler olduğu ve Test Gezgini'nin neleri göreceği arasında tutarsızlıklar görüyorsanız lütfen **Ctrl+Shift+B** tuşlarını kullanarak bir çözüm/proje derlemesi düşünün ve ardından testleri çalıştırın. Herhangi bir açık derleme, sık yapılan yeniden yükleme test sonuçlarını normal tam derleme test sonuçlarıyla değiştirir.

## <a name="known-issues"></a>Bilinen sorunlar
- Sık sık yeniden yükleme ile test yürütmesi aşağıdaki senaryolarda oluşmaz:
  - Kod Kapsamı
  - Live Unit Testing
  - Profil Oluşturma
  - Hata Ayıklama
- Yığın izlemeleri okunamaz belirteçler olduğu için okunamaz olabilir. Bu sorun burada izlanıyor [ve](https://github.com/dotnet/runtime/issues/56335) .NET 7.0'da düzeltme yapılması planlanıyor
  - Bu durumda önerilen geçici çözüm, projenizi derlemek ve testi yeniden çalıştırmaktır.

## <a name="your-feedback-matters"></a>Geri bildiriminiz önemlidir
Daha önce de olduğu gibi, bu deneysel özelliğin tamamlanması için geri bildiriminize ihtiyaç vardır. Deneyimin nasıl olması gerektiğiyle ilgili bir öneriniz varsa veya herhangi bir sorunla karşılaşırsanız lütfen sorunları bize bildirebilirsiniz. Yalnızca geri bildiriminiz sayesinde kritik sorunların çözüme kavuşturulması ve gelecekteki kararların girişe göre önceliklendirmesi sağlandı.

Bize ulaşmak için lütfen geri [bildirim Visual Studio kullanın.](https://developercommunity.visualstudio.com/home)
