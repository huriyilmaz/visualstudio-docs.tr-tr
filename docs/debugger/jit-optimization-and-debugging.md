---
title: JıT Iyileştirme ve hata ayıklama | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731616"
---
# <a name="jit-optimization-and-debugging"></a>JIT İyileştirmesi ve Hata Ayıklaması
**İyileştirmeler .net 'Te nasıl çalışır:** Kodda hata ayıklamaya çalışıyorsanız, bu kod en iyi duruma **getirilmeyen** daha kolay olur. Bunun nedeni, kodun en iyi duruma getirilmesi, derleyicinin ve çalışma zamanının, daha hızlı çalışması için, ancak özgün kaynak koda daha az doğrudan eşlenmesi için, oluşturulan CPU kodunda değişiklikler yapması. Bu, hata ayıklayıcıların genellikle yerel değişkenlerin değerini bildiremediği, kod adımlaması ve kesme noktaları istediğiniz gibi çalışmayabilir.

Normalde yayın derleme yapılandırması iyileştirilmiş kod oluşturuyor ve hata ayıklama derleme yapılandırması değil. @No__t_0 MSBuild özelliği, derleyicinin kodu iyileştirip söyetkinleştirilmeyeceğini denetler.

.NET ekosisteminde, kod iki adımlı bir işlemde kaynaktan CPU yönergelerine açıktır: ilk olarak, C# derleyici YAZDıĞıNıZ metni MSIL adlı bir ara ikili biçime dönüştürür ve bunu. dll dosyalarına yazar. Daha sonra, .NET çalışma zamanı bu MSIL 'yi CPU yönergelerine dönüştürür. Her iki adım da bir ölçüde iyileştirebilirler, ancak .NET çalışma zamanı tarafından gerçekleştirilen ikinci adım daha önemli iyileştirmeleri gerçekleştirir.

**' Modül YÜKLEMESINDE JIT iyileştirmesini bastır (yalnızca yönetilen) ' seçeneği:** Hata ayıklayıcı, hedef işlemin içinde iyileştirmeler etkinken derlenen bir DLL yüklendiğinde ne olacağını denetleyen bir seçenek sunar. Bu seçenek işaretli değilse (varsayılan durum), .NET çalışma zamanı MSIL kodunu CPU koduna derlediğinde, iyileştirmeler etkin kalır. Seçenek işaretliyse, hata ayıklayıcı iyileştirmelerin devre dışı bırakıldığını ister.

**Modül YÜKLEMESINDE JIT iyileştirmesini gösterme (yalnızca yönetilen)** seçeneğini bulmak için **Araçlar**  > **Seçenekler**' i seçin ve ardından **hata ayıklama** düğümünün altındaki **genel** sayfasını seçin.

**Bu seçeneği ne zaman denetlemeniz gerekir:** Bu seçeneği, bir NuGet paketi gibi başka bir kaynaktan dll 'Leri karşıdan yüklerken ve bu DLL 'deki kodda hata ayıklamak istediğinizde işaretleyin. Bunun çalışması için bu DLL için simge (. pdb) dosyasını da bulmanız gerekir.

Yalnızca yerel olarak oluşturmakta olduğunuz kodun hatalarını ayıklamakla ilgileniyorsanız, bazı durumlarda bu seçeneğin etkinleştirilmesi, hata ayıklamanın önemli ölçüde yavaşlamasına neden olur. Bu yavaşlamaya iki neden vardır:

* İyileştirilmiş kod daha hızlı çalışır. Birçok kod için iyileştirmeleri devre dışı bırakırsanız, performans etkisi eklenebilir.
* Yalnızca kendi kodum etkinse, hata ayıklayıcı, iyileştirilmiş dll 'Ler için sembolleri denemez ve yüklemez. Sembolleri bulma uzun zaman alabilir.

**Bu seçeneğin sınırlamaları:** Bu **seçeneğin çalışmacağı** iki durum vardır:

1. Hata ayıklayıcıyı zaten çalışan bir işleme iliştirmekte olduğunuz durumlarda, bu seçeneğin hata ayıklayıcı eklendiği sırada zaten yüklenmiş modüller üzerinde hiçbir etkisi olmayacaktır.
2. Bu seçeneğin yerel koda önceden derlenmiş (a. k. a NGen) dll 'Leri üzerinde hiçbir etkisi yoktur. Ancak, ' COMPlus_ZapDisable ' ortam değişkeniyle ' 1 ' olarak ayarlanmış işlemi başlatarak önceden derlenmiş kodun kullanımını devre dışı bırakabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Hata Ayıklayıcısı ile Kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Yönetilen Yürütme İşlemi](/dotnet/standard/managed-execution-process)
