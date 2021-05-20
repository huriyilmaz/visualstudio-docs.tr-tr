---
title: Veri kesme noktası ayarlanamıyor | Microsoft Docs
description: "\"Değer değiştiğinde kes\" kullanılırken gerçekleşen \"veri kesme noktası hataları ayarlanamıyor\" açıklamalarını, çözümlerini ve geçici çözümlerini bulun."
ms.custom: SEO-VS-2020
ms.date: 5/19/2020
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 73e7e02d90e2a89c81b5e690718c95fe7efe0fb3
ms.sourcegitcommit: 6e27b1238a8aa704b127eac34f4173e9d56690c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2021
ms.locfileid: "110231971"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Veri kesme noktası hatalarında sorun giderme
Bu sayfa, "değer değiştiğinde kes" kullanırken görülen yaygın hataları çözme konusunda size kılavuzluk eder

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>"Veri kesme noktası ayarlanamıyor" hataları tanılanıyor
> [!IMPORTANT]
> Yönetilen veri kesme noktaları .NET Core 3,0 ve üzerinde .NET 5.0.3 ve üzerinde desteklenir. En son sürümü [buradan](https://dotnet.microsoft.com/download)indirebilirsiniz.

Yönetilen veri kesme noktaları kullanılırken oluşabilecek hataların bir listesi aşağıda verilmiştir. Hatanın neden meydana geldiğinin yanı sıra hatayı çözümlemek için olası çözümleri veya geçici çözümleri içeren daha fazla açıklama içerirler.

- *"Hedef işlem tarafından kullanılan .NET sürümü veri kesme noktalarını desteklemiyor. Veri kesme noktaları, x86 veya x64 üzerinde çalışan .NET Core 3. x veya .NET 5.0.3 + gerektirir. "*

  - Yönetilen veri kesme noktaları desteği .NET Core 3,0 ' de başlamıştır. Bu, şu anda .NET Framework, .NET Core 'un sürümleri 3,0 veya 5.0.3 altında .NET sürümleri için desteklenmez. 
    
  - **Çözüm**: Bu çözüm, projenizi .net Core 3,0 sürümüne yükseltmek olacaktır.

- *"Yönetilen yığında değer bulunamıyor ve izlenemez."*
  - Yığında belirtilen değişken.
    - Bu değişken, işlev çıktıktan sonra geçersiz olacağı için yığında oluşturulan değişkenler için veri kesme noktaları ayarlamayı desteklemiyoruz.
    - **Geçici çözüm**: değişkenin kullanıldığı satırlarda kesme noktaları ayarlayın.

  - Bir açılan menüden genişletilmeyen bir değişkende "değer değiştiğinde kes".
    - Hata ayıklayıcının, izlemek istediğiniz alanı içeren nesneyi bilmesi gerekir. Çöp toplayıcı, hata ayıklayıcının izlemek istediğiniz değişkeni tutan nesneyi bilmesi için nesneyi yığında etrafında taşıyabilir. 
    - **Geçici çözüm**: bir veri kesme noktası ayarlamak istediğiniz nesne içindeki bir yöntem içindeyse, bir çerçeve yukarı gidin ve `locals/autos/watch` nesneyi genişletmek ve istediğiniz alana bir veri kesme noktası ayarlamak için pencereyi kullanın.

- *"Veri Kesme Noktaları statik alanlar veya statik özellikler için desteklenmiyor."*
    
  - Statik alanlar ve özellikler şu anda desteklenmiyor. Bu özellikle ilgileniyorsanız lütfen geri bildirim [gönderin.](#provide-feedback)

- *"Yapıların alanları ve özellikleri iz edilemez."*

  - Şu anda yapıların alanları ve özellikleri desteklenmiyor. Bu özellikle ilgileniyorsanız lütfen geri bildirim [gönderin.](#provide-feedback)

- *"Özellik değeri değişti ve artık izlenememe."*

  - Bir özellik çalışma zamanı sırasında hesaplanma biçimi değiştirebilir ve bu durumda özelliğin bağlı olduğu değişken sayısı artar ve donanım sınırlamasının aşılır. Aşağıya `"The property is dependent on more memory than can be tracked by the hardware."` bakın.

- *"Özellik, donanım tarafından iznden daha fazla belleğe bağımlıdır."*
    
  - Her mimari, destekleyene belirli sayıda bayt ve donanım veri kesme noktası içerir ve üzerinde bir veri kesme noktası ayarlamak istediğiniz özellik bu sınırı aştı. Kullanmakta olan [mimari için](#data-breakpoint-hardware-limitations) kaç donanım tarafından desteklenen veri kesme noktası ve bayt olduğunu bulmak için Veri Kesme Noktası Donanım Sınırlamaları tablosuna bakın. 
  - **Geçici** çözüm: Özelliğin içinde değişe bir değer üzerinde veri kesme noktası ayarlayın.

- *"Eski C# ifade değerlendiricisi kullanılırken Veri Kesme Noktaları desteklenmiyor."*

  - Veri kesme noktaları yalnızca eski olmayan C# ifade değerlendiricisinde de kullanılır. 
  - **Çözüm:** Eski C# ifade değerlendiricisini devre dışı bırakmak için `Debug -> Options` işaretinin altına gidip işaretini `Debugging -> General` kaldırmış `"Use the legacy C# and VB expression evaluators"` olursanız.

- *"X **sınıfı,** yalnızca buna özgü verilerde veri kesme noktaları kullanmayı engelleyen özel bir hata ayıklayıcı görünümüne sahiptir."*
  
  - Veri kesme noktaları yalnızca hedef işlem (hata ayıklama yapılan uygulama) tarafından oluşturulan bellekte de kullanılabilir. Veri kesme noktası için ayarlanmış olan bellek, [DebuggerTypeProxy](using-debuggertypeproxy-attribute.md) özniteliği veya hedef sürecin parçası olmayan başka bir nesne tarafından oluşturulmuş bir nesneye ait olabilir olarak işaretlendi.
  - **Geçici çözüm**: nesnelerin DebuggerTypeProxy görünümünü genişletmek yerine nesne (ler) ın "ham görünümünü" genişletin ve ardından veri kesme noktasını ayarlayın. Bu, veri kesme noktasının bir DebuggerTypeProxy özniteliği tarafından oluşturulan bir nesnenin sahip olduğu bellek üzerinde olmadığından emin olur.

## <a name="data-breakpoint-hardware-limitations"></a>Veri kesme noktası donanım sınırlamaları

Programınızın üzerinde çalıştığı mimari (Platform yapılandırması), kullanabileceği sınırlı sayıda donanım veri kesme noktası içerir. Aşağıdaki tablo, mimari başına kullanılacak kaç kayıt olduğunu gösterir.

| Mimari | Desteklenen donanım veri kesme noktası sayısı | En fazla bayt boyutu|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Geribildirim gönderme

Bu özellikle ilgili herhangi bir sorun veya öneri için, lütfen yardım > bir sorun bildirmek > IDE 'de veya [Geliştirici topluluğu](https://aka.ms/feedback/suggest?space=8)'Nda [bir sorun bildirmek](../ide/how-to-report-a-problem-with-visual-studio.md) için lütfen bize bilgi verin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 3,0 ' de "değer değiştiğinde kes" kullanımı](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: değer değiştiğinde kes: Visual Studio 2019 ' de .NET Core için veri kesme noktaları](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
