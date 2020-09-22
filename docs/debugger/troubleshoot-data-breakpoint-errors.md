---
title: Veri kesme noktası ayarlanamıyor | Microsoft Docs
ms.date: 12/3/2019
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
ms.openlocfilehash: c9f06b72673ea73e68f6c224ec9734568d70e25a
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852263"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>Veri kesme noktası hatalarında sorun giderme
Bu sayfa, "değer değiştiğinde kes" kullanırken görülen yaygın hataları çözme konusunda size kılavuzluk eder

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>"Veri kesme noktası ayarlanamıyor" hataları tanılanıyor
> [!IMPORTANT]
> Yönetilen veri kesme noktaları .NET Core 3,0 ve üzerinde desteklenir. En son sürümü [buradan](https://dotnet.microsoft.com/download)indirebilirsiniz.

Yönetilen veri kesme noktaları kullanılırken oluşabilecek hataların bir listesi aşağıda verilmiştir. Hatanın neden meydana geldiğinin yanı sıra hatayı çözümlemek için olası çözümleri veya geçici çözümleri içeren ek açıklamalar içerirler.

- *"Hedef işlem tarafından kullanılan .NET sürümü veri kesme noktalarını desteklemiyor. Veri kesme noktaları x86 veya x64 üzerinde çalışan .NET Core 3.0 + gerektirir. "*

  - Yönetilen veri kesme noktaları desteği .NET Core 3,0 ' de başlamıştır. Şu anda 3,0 altında .NET Core .NET Framework veya sürümünde desteklenmemektedir. 
    
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

## <a name="data-breakpoint-hardware-limitations"></a>Veri kesme noktası donanım sınırlamaları

Programınızın üzerinde çalıştığı mimari (Platform yapılandırması), kullanabileceği sınırlı sayıda donanım veri kesme noktası içerir. Aşağıdaki tablo, mimari başına kullanılacak kaç kayıt olduğunu gösterir.

| Mimari | Desteklenen donanım veri kesme noktası sayısı | En fazla bayt boyutu|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| x64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>Geri bildirimde bulunma

Bu özellikle ilgili herhangi bir sorun veya öneri için, lütfen yardım > bir sorun bildirmek > IDE 'de veya [Geliştirici topluluğu](https://developercommunity.visualstudio.com/)'Nda [bir sorun bildirmek](../ide/how-to-report-a-problem-with-visual-studio.md) için lütfen bize bilgi verin.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 3,0 ' de "değer değiştiğinde kes" kullanımı](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus).
- [DevBlog: değer değiştiğinde kes: Visual Studio 2019 ' de .NET Core için veri kesme noktaları](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
