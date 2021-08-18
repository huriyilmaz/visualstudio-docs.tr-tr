---
title: JIT İyileştirme ve Hata Ayıklama | Microsoft Docs
description: İyileştirilmiş kodun hata ayıklaması, hata ayıklaması olmayan koddan daha zordur. JIT iyileştirmesi ve ne zaman ve nasıl gizlenmeleri hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7e6dae429c3083188fa9d7fbc37a48dda5a98b18
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112600"
---
# <a name="jit-optimization-and-debugging"></a>JIT İyileştirmesi ve Hata Ayıklaması
Kodda hata ayıklamaya çalışıyorsanız, bu kod en iyi duruma getirilmiş DEĞIL olduğunda **daha kolaydır.** Kod en iyi duruma geldiğinde, derleyici ve çalışma zamanı daha hızlı çalıştırılıyor ancak özgün kaynak koda daha az doğrudan eşlemeye sahip olacak şekilde, yayılan CPU kodunda değişiklikler yapar. Eşleme daha az doğrudansa, hata ayıklayıcılar genellikle yerel değişkenlerin değerini size söylemez ve kod adımlama ve kesme noktaları beklediğiniz gibi çalışmayabilir.

> [!NOTE]
> JIT (Tam Zamanında) hata ayıklama hakkında daha fazla bilgi için bu [belgeleri okuyun.](../debugger/debug-using-the-just-in-time-debugger.md)

## <a name="how-optimizations-work-in-net"></a>.NET'te iyileştirmeler nasıl çalışır? 
Normalde Yayın derleme yapılandırması iyileştirilmiş kod oluşturur ve Hata ayıklama derleme yapılandırması oluşturmaz. MSBuild `Optimize` özelliği, derleyicinin kodu iyileştirmesi isnip isnip söylenip söylen olmadığını kontrol eder.

.NET ekosistemi içinde kod, iki adımlı bir işlemde kaynaktan CPU yönergelerine dönüştürülür: İlk olarak, C# derleyicisi, yazmanız gereken metni MSIL adlı bir ara ikili biçime dönüştürür ve MSIL'i .dll dosyalarına yazar. Daha sonra, .NET Çalışma Zamanı bu MSIL'i CPU yönergelerine dönüştürür. Her iki adım da bir dereceye kadar iyi duruma gelir, ancak .NET Çalışma Zamanı tarafından gerçekleştirilen ikinci adım daha önemli iyileştirmeleri gerçekleştirir.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>'Modül yükünde JIT iyileştirmeyi gizleme (yalnızca yönetilen)' seçeneği
Hata ayıklayıcısı, hedef işlem içinde iyileştirmeler etkin yüklerle derlenmiş bir DLL olduğunda ne olacağını kontrol eden bir seçeneği gösterir. Bu seçenek işaretlenmemişse (varsayılan durum), .NET Çalışma Zamanı MSIL kodunu CPU koduna derledikten sonra iyileştirmeleri etkin bırakır. Seçenek işaretli ise, hata ayıklayıcı iyileştirmelerin devre dışı bırakılacak şekilde istekte bulundur.

Modül yükünde JIT iyileştirmeyi gizleme **(yalnızca yönetilen)** seçeneğini bulmak için Araçlar Seçenekleri'ne tıklayın ve ardından Hata Ayıklama düğümü altında Genel   >   **sayfasını** seçin. 

![JIT İyileştirmeyi Gizleme](../debugger/media/suppress-jit-tool-options.png "JIT İyileştirmeyi Gizleme")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>'JIT iyileştirmeyi gizleme' seçeneğini ne zaman denetlemeniz gerekir?
DLL'leri nuget paketi gibi başka bir kaynaktan indirdiğiniz ve bu DLL'de kodda hata ayıklamak istediğinizde bu seçeneği işaretleyin. Gizlemenin çalışması için bu DLL için sembol (.pdb) dosyasını da bulmanız gerekir.

Yalnızca yerel olarak çözmekte olduğunu kodun hata ayıklamasını yapmak ilginizi çekiyorsa, bu seçeneğin işaretsiz bırakılacağından, bazı durumlarda bu seçeneğin etkinleştirilmesi hata ayıklamayı önemli ölçüde yavaşlatabilir. Bu yavaşlamanın iki nedeni vardır:

* İyileştirilmiş kod daha hızlı çalışır. Çok sayıda kod için iyileştirmeleri kapatıyorsanız performans etkisi ortaya çıkar.
* Daha önce Yalnızca kendi kodum, hata ayıklayıcı en iyi duruma getirilmiş URL'ler için sembolleri bile yüklemeye çalışmaz. Sembollerin bulunması uzun zaman alır.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>'JIT iyileştirmeyi gizleme' seçeneğinin sınırlamaları 
Bu seçeneğin açmanın çalışmay olduğu iki **durum** vardır:

1. Hata ayıklayıcıyı zaten çalışan bir işleme iliştiriyorsanız, bu seçeneğin hata ayıklayıcı ekli olduğu sırada zaten yüklenmiş olan modüller üzerinde hiçbir etkisi olmaz.
2. Bu seçeneğin yerel koda önceden derlenmiş OLAN (ngen'ed gibi) URL'ler üzerinde hiçbir etkisi yoktur. Ancak, işlemi **'0'** olarak ayarlanmış 'COMPlus_ReadyToRun' ortam değişkeniyle başlatarak önceden derlenmiş kodun kullanımını **devre dışı abilirsiniz.** Bu, .NET Core çalışma zamanının önceden derlenmiş görüntülerin kullanımını devre dışı bırakmasını söyler ve çalışma zamanının JIT derleme çerçevesi koduna zorlar. 

    > [!IMPORTANT]
    > .NET Framework veya daha eski bir .NET Core (2.x veya daha düşük) sürümünü hedeflemektedir, ayrıca 'COMPlus_ZapDisable' ortam değişkenini ekleyin ve '1' olarak ayarlayın

    **Bir .NET Core projesi için ortam değişkeni ayarlamak için Visual Studio:**
    1. Dosya **Çözüm Gezgini** proje **dosyasına sağ tıklayın** ve Özellikler'i **seçin.**
    2. Hata Ayıkla **sekmesine** gidin ve Ortam değişkenleri **altında** Ekle **düğmesine** tıklayın.
    3. Ad (Anahtar) değerini **COMPlus_ReadyToRun** ve Değer değerini **0 olarak ayarlayın.**

    ![Ortam COMPlus_ReadyToRun ayarlama](../debugger/media/environment-variables-debug-menu.png "Ortam COMPlus_ReadyToRun ayarlama")

## <a name="see-also"></a>Ayrıca bkz.
- [Dotnet Framework Kaynağında Hata Ayıklama](../debugger/how-to-debug-dotnet-framework-source.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Hata Ayıklayıcısı ile Kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Yönetilen Yürütme Süreci](/dotnet/standard/managed-execution-process)
