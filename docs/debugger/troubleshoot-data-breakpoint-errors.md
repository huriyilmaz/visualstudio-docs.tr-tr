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
ms.openlocfilehash: deb06d9fdb084ca1a99f5fa1991c2e4d93d087574f73781979f630db973c22d5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378482"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Veri kesme noktası hatalarında sorun giderme
Bu sayfa, "değer değiştiğinde kes" kullanırken görülen yaygın hataları çözme konusunda size kılavuzluk eder

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>"Veri kesme noktası ayarlanamıyor" hataları tanılanıyor
> [!IMPORTANT]
> Yönetilen veri kesme noktaları .NET Core 3,0 ve üzerinde .NET 5.0.3 ve üzerinde desteklenir. En son sürümü [buradan](https://dotnet.microsoft.com/download)indirebilirsiniz.

Yönetilen veri kesme noktaları kullanılırken oluşabilecek hataların bir listesi aşağıda verilmiştir. Hatanın neden meydana geldiğinin yanı sıra hatayı çözümlemek için olası çözümleri veya geçici çözümleri içeren daha fazla açıklama içerirler.

- *"Hedef işlem tarafından kullanılan .NET sürümü veri kesme noktalarını desteklemiyor. Veri kesme noktaları, x86 veya x64 üzerinde çalışan .NET Core 3. x veya .NET 5.0.3 + gerektirir. "*

  - Yönetilen veri kesme noktaları desteği .NET Core 3,0 ' de başlamıştır. bu, şu anda .NET Framework, .net Core 'un sürümleri 3,0 veya 5.0.3 altında .net sürümleri için desteklenmez. 
    
  - **Çözüm**: Bu çözüm, projenizi .net Core 3,0 sürümüne yükseltmek olacaktır.

- *"Yönetilen yığında değer bulunamıyor ve izlenemez."*
  - Yığında belirtilen değişken.
    - Bu değişken, işlev çıktıktan sonra geçersiz olacağı için yığında oluşturulan değişkenler için veri kesme noktaları ayarlamayı desteklemiyoruz.
    - **Geçici çözüm**: değişkenin kullanıldığı satırlarda kesme noktaları ayarlayın.

  - Bir açılan menüden genişletilmeyen bir değişkende "değer değiştiğinde kes".
    - Hata ayıklayıcının, izlemek istediğiniz alanı içeren nesneyi bilmesi gerekir. Çöp toplayıcı, hata ayıklayıcının izlemek istediğiniz değişkeni tutan nesneyi bilmesi için nesneyi yığında etrafında taşıyabilir. 
    - **Geçici çözüm**: bir veri kesme noktası ayarlamak istediğiniz nesne içindeki bir yöntem içindeyse, bir çerçeve yukarı gidin ve `locals/autos/watch` nesneyi genişletmek ve istediğiniz alana bir veri kesme noktası ayarlamak için pencereyi kullanın.

- *"Statik alanlar veya statik özellikler için veri kesme noktaları desteklenmiyor."*
    
  - Statik alanlar ve Özellikler Şu anda desteklenmiyor. Bu özellikle ilgileniyorsanız lütfen [geri bildirim](#provide-feedback)sağlayın.

- *"Yapıların alanları ve özellikleri izlenemez."*

  - Yapıların alanları ve özellikleri şu anda desteklenmiyor. Bu özellikle ilgileniyorsanız lütfen [geri bildirim](#provide-feedback)sağlayın.

- *"Özellik değeri değişti ve artık izlenemez."*

  - Bir özellik, çalışma zamanı sırasında nasıl hesaplanacağını değiştirebilir ve bu durumda, özelliğin arttığı ve donanım sınırlamasını aşabilecek değişkenlerin sayısı artar. `"The property is dependent on more memory than can be tracked by the hardware."`Aşağıya bakın.

- *"Özelliği, donanım tarafından izlenebileceğinden daha fazla belleğe bağımlıdır."*
    
  - Her mimaride, destekleyebileceği bir dizi bayt ve donanım veri kesme noktası ve üzerinde veri kesme noktası ayarlamak istediğiniz özellik bu sınırı aştı. Kullanmakta olduğunuz mimaride kaç tane donanım tarafından desteklenen veri kesme noktası ve bayt kullanılabildiğini öğrenmek için lütfen [veri kesme noktası donanım sınırlamaları](#data-breakpoint-hardware-limitations) tablosuna bakın. 
  - **Geçici çözüm**: özellik içinde değişebilir bir değer üzerinde bir veri kesme noktası ayarlayın.

- *"Eski C# ifade değerlendiricisi kullanılırken veri kesme noktaları desteklenmez."*

  - Veri kesme noktaları yalnızca eski C# ifade değerlendiricisi üzerinde desteklenir. 
  - **Çözüm**: eski C# ifade değerlendiricisi, `Debug -> Options` işaretini kaldır ' ın altında olacak şekilde devre dışı bırakır `Debugging -> General` `"Use the legacy C# and VB expression evaluators"` .

- *"Class **X** , yalnızca kendisine özgü verilerde veri kesme noktaları kullanmayı engelleyen özel bir hata ayıklayıcı görünümüne sahiptir."*
  
  - Veri kesme noktaları yalnızca hedef işlem (hata ayıklanan uygulama) tarafından oluşturulan bellekte desteklenir. Veri kesme noktasının ayarlandığı bellek, bir [DebuggerTypeProxy özniteliği](using-debuggertypeproxy-attribute.md) tarafından oluşturulan bir nesne veya hedef işlemin bir parçası olmayan başka bir nesne tarafından sahip olunmakta olan şekilde işaretlendi.
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

Bu özellikle ilgili herhangi bir sorun veya öneri için, lütfen yardım > [bir sorun](../ide/how-to-report-a-problem-with-visual-studio.md) bildirimi GÖNDERIN > IDE 'de veya [Geliştirici Community](https://aka.ms/feedback/suggest?space=8)bildirin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 3,0 ' de "değer değiştiğinde kes" kullanımı](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [devblog: değer değiştiğinde kes: Visual Studio 2019 ' de .net Core için veri kesme noktaları](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
