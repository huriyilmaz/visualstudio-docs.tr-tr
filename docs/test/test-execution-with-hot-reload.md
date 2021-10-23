---
title: Dinamik yeniden yükleme ile test yürütmesi
description: Visual Studio 'de test Gezgini ile Hot Reload 'i nasıl kullanacağınızı öğrenin. Bu konu, dinamik olarak yeniden yüklenmiş test yürütmenin nasıl etkinleştirileceğini ve nerede desteklendiğini ve ne zaman beklendiğini anlatmaktadır.
ms.date: 10/15/2021
ms.topic: how-to
author: vritant24
ms.author: vrbhardw
manager: manishj
ms.technology: vs-ide-test
ms.workload:
- VB
- CSharp
ms.openlocfilehash: 920c11d759ef73d8a9c83053120a1cbf5ca6201b
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130212817"
---
# <a name="test-execution-with-hot-reload"></a>Dinamik yeniden yükleme ile test yürütmesi

Visual Studio test çalıştırmaları, testlerinizi yürütmek için [test platformunu](https://github.com/microsoft/vstest/) kullanmadan önce diskteki ikilileri güncelleştirmek üzere projeyi oluşturmayı içerir. Visual Studio içindeki derleme süresi, kodda yapılan [değişikliklerin türüne](https://github.com/dotnet/roslyn/blob/296e0fada42f241d338b169c3c6c6189101ef0b7/docs/wiki/EnC-Supported-Edits.md) göre değişiklik gösterebilir. Daha büyük çözümler için, derlemeler Test çalıştırmasının en pahalı parçası olabilir. Visual Studio 2022 ve sonrasında, dinamik yeniden yükleme ile test yürütmesi, desteklenen senaryolar için yapıları atlayarak test yürütmeyi hızlandırmak için etkinleştirilebilir.

## <a name="what-is-supported"></a>Desteklenen nedir?
- .NET 6,0 ve üstünü hedefleyen C# ve VB projeleri
- Hata ayıklama yapılandırması için oluşturulan test projeleri
- Visual Studio 2022 ve üzeri

## <a name="enable-test-execution-with-hot-reload"></a>Dinamik yeniden yükleme ile test yürütmeyi etkinleştir
Bu özelliği   >    >  **, .net 6 ve üzeri hedeflenen C# ve vb test projeleri için test seçenekleri "(deneysel) etkin yeniden yüklenmiş test çalıştırmalarını etkinleştir ' i** seçerek etkinleştirin.
![Visul Studio test seçenekleri sayfasındaki etkin yeniden yüklenmiş test çalıştırmalarını etkinleştir düğmesinin ekran görüntüsü. Bu seçildiğinde, testlerin yürütülmesi desteklenen senaryolar için sık yeniden yükleme kullanır](./media/test-execution-hot-reload-option.png)

## <a name="why-is-it-experimental"></a>Neden deneysel?
Bu, kod doğrulama için yaygın olarak kullanılan bir yolu değiştirdiğimiz test yürütmesinin yeni bir yoludur. Ayrıca, kullanıcılardan daha fazla geri bildirim aldığımızda bu özelliğin etrafındaki Kullanıcı deneyimini de bekletireceğiz. Bu iki nedenle, şu anda bu özelliği "deneysel" olarak etiketliyoruz.

## <a name="how-it-works"></a>Nasıl çalışır?
Seçenek etkinleştirildikten sonra test Gezgini, mümkün olduğunda otomatik olarak test yürütmesi kullanır. Etkin bir yeniden yükleme mümkün değilse, testlerin oluşturulması ve çalıştırılması için normal davranışa geri döner. Testleri çalıştıran bir kullanıcı olarak, iş akışınızda herhangi bir değişiklik yapmanız gerekmez (diğer bir deyişle, kodu düzenlemeye ve testleri çalıştırmaya devam edebilirsiniz).

Bu arada, yapılan değişikliklerin belirlenmesi için [çalışma zamanında C#/vb kodunu düzenlemeye yönelik yeni kullanıma sunulan etkin yeniden yükleme deneyiminde](https://devblogs.microsoft.com/dotnet/introducing-net-hot-reload/) aynı [Düzenle ve devam et](../debugger/edit-and-continue.md) altyapısını kullanıyoruz. Bu nedenle, yalnızca bir "Rude düzenleme" olmadığında, bu durumda testlerinizi yürütmeden önce testlerinizi oluşturmaya geri dönediğimiz bir şekilde yeniden yükleme yaptık. Desteklenen düzenlemeler hakkında daha fazla ayrıntı için [Düzenle ve devam et belgelerini](https://github.com/dotnet/roslyn/blob/296e0fada42f241d338b169c3c6c6189101ef0b7/docs/wiki/EnC-Supported-Edits.md) okuyun

## <a name="how-much-faster-will-the-test-execution-be"></a>Test yürütmesi ne kadar hızlı olacaktır?
Bu özelliğin sizi ne kadar zaman kaydedebileceği tahmin edildiğinde yürütmeye gelen birçok değişken vardır. Örneğin:
- Proje derlemesi ne kadar sürer.
- Ne tür bir düzenleme yapılmıştır.
- Dosyanın, düzenlemenin yapıldığı yere ne kadar büyük olduğu.
- Düzenlemenin yapıldığı yer (bir yaprak projem ise).

Son olarak, Hız iyileştirmeleri bu belirli test çalıştırmasında gerçekleşen derleme süresi ile doğrudan ilgilidir.

### <a name="notes"></a>Notlar
- seçeneği etkinleştirdikten sonra ilk test çalıştırması veya Visual Studio açmak bir proje derlemesi olur.
- Testler çalıştırıldığında düzenleyicideki dosyalar kaydedilemez. Bunları çözümlemek ve iade etmeden önce, tam derleme yaptığınızdan emin olun (Ctrl + Shift + B).
- Etkin yeniden yüklenmiş test yürütmesi gerçekleştiğinde diskteki ikili dosyalar güncellenmez.
- Dinamik yeniden yüklenmiş test yürütmesi, test Gezgini 'nde **"test**  >  **çalıştırması tüm testler**", "**görünümdeki tüm Testleri Çalıştır**" ile çalışmaz ve Çözüm Gezgini çözüm düğümünden **Tüm Testleri Çalıştır** ile birlikte çalışır. Bu özellik, şu anda çözümün tamamını oluşturmayı garanti ettiğinden, bu komutlarla birlikte çalışmaz.
- Desteklenmeyen hedef çerçeveleri olan testler (.NET 6,0 ' den düşük) çalıştırıldığında bir proje derlemesi oluşur.
- Diskte bulunan ve test Gezgini 'nin gösterdiği herhangi bir tutarsızlık görürseniz, lütfen **CTRL + SHIFT + B** kullanarak bir çözüm/proje derlemesi değerlendirin ve ardından testleri çalıştırın. Herhangi bir açık derleme, dinamik yeniden yükleme testi sonuçlarını düzenli tam yapı testi sonuçlarıyla değiştirir.

## <a name="known-issues"></a>Bilinen sorunlar
- Dinamik yeniden yükleme ile test yürütmesi aşağıdaki senaryolarda oluşmaz:
  - Kod Kapsamı
  - Live Unit Testing
  - Profil Oluşturma
  - Hata Ayıklama
- Yığın izlemeleri okunamaz belirteçlerin varlığı ile okunabilir olmayabilir. Bu sorun [burada](https://github.com/dotnet/runtime/issues/56335) izleniyor ve .net 7,0 ' de bir düzeltilmesi planlanmaktadır
  - Bu durumda önerilen geçici çözüm, projenizi derleyip testi yeniden çalıştırmaya yönelik bir çözümdür.

## <a name="your-feedback-matters"></a>Geri bildiriminiz önemli
Daha önce belirtildiği gibi, bu deneysel özelliğin tamamlanabilmesi için geri bildiriminiz gerekir. Deneyimin nasıl olması gerektiğine yönelik bir öneriniz varsa veya herhangi bir sorunla karşılaşırsanız, lütfen bize sorun bildirmek için bir dakikanızı ayırın. Yalnızca geri bildiriminiz, kritik sorunların çözümlendiğini ve gelecekteki kararların sizin girişinizi temel alarak önceliklendirildiğini güvence altına alabilir.

bize ulaşmak için lütfen [Visual Studio geri bildirim mekanizmasını](https://developercommunity.visualstudio.com/home)kullanın.
