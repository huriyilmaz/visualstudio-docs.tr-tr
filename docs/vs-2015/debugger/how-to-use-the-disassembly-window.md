---
title: 'Nasıl yapılır: ayrıştırma penceresini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c25c3cdeb96abacb4123b2d0a851ac3d4acb0cd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696136"
---
# <a name="how-to-use-the-disassembly-window"></a>Nasıl Yapılır: Ayrıştırılmış Kod Penceresini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu özellik yalnızca adres düzeyinde hata ayıklama etkinleştirildiğinde **Seçenekler** iletişim kutusu, **hata ayıklama** düğümü ' ne ayarlanırsa kullanılabilir. Betik veya SQL hata ayıklama için kullanılamaz.  
  
 **Ayrıştırılmış** pencere, derleyici tarafından oluşturulan yönergelere karşılık gelen derleme kodunu gösterir. Yönetilen kodda hata ayıklaması yapıyorsanız, bu derleme yönergeleri, Visual Studio derleyicisi tarafından oluşturulan Microsoft ara dili (MSIL) değil, tam zamanında (JıT) derleyicisi tarafından oluşturulan yerel koda karşılık gelir.  
  
 Bütünleştirilmiş kod yönergelerine ek olarak, **ayrıştırılmış** bir pencere aşağıdaki isteğe bağlı bilgileri gösterebilir:  
  
- Her yönergenin bulunduğu bellek adresi. Yerel uygulamalar için bu gerçek bellek adresidir. Visual Basic, C# veya yönetilen kod için, işlevin başından itibaren bir kaydırmadır.  
  
- Derleme kodunun türetildiği kaynak kodu.  
  
- Kod baytları — gerçek makinenin veya MSIL yönergelerinin bayt temsilleri.  
  
- Bellek adreslerinin sembol adları.  
  
- Kaynak koda karşılık gelen satır numaraları.  
  
  Derleme dili yönergeleri, yönerge adları için kısaltmalar ve değişkenleri, Yazmaçları ve sabitleri temsil eden semboller olan anımsatıcıları içerir. Her makine dili yönergesi, genellikle bir veya daha fazla değişken, kayıt veya sabitler tarafından izlenen bir derleme dili anımsatıcı tarafından temsil edilir.  
  
  Derleme dilini okuyaamaması ve ayrıştırma penceresi 'nden tam olarak yararlanmak istiyorsanız, derleme dili programlamada iyi bir kitaba danışın. Bütünleştirilmiş kod dili programlama, ayrıştırma penceresine bu kısa giriş yapabiliriz.  
  
  Derleme kodu yoğun bir şekilde işlemci Yazmaçları kullandığından veya yönetilen kod söz konusu olduğunda, ortak dil çalışma zamanı saklayıcıları sırasında, kayıt içeriğini incelemenize olanak tanıyan kayıtları kaydetme penceresi ile bağlantılı olarak, genellikle ayrıştırma penceresini kullanmak yararlı olacaktır.  
  
  Büyük olasılıkla, derleme dili yerine ham, sayısal biçimde makine kodu yönergelerini görüntülemeniz gerekmez. Ancak bunu yapmak istiyorsanız, bu amaçla bellek penceresini kullanabilir veya ayrıştırma penceresindeki kısayol menüsünden kod baytları ' ni seçebilirsiniz.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-disassembly-window"></a>Ayrıştırılmış pencereyi görüntüleme  
  
- **Hata Ayıkla** menüsünde **Windows**' u seçin ve **ayrıştırılmış derleme**' ye tıklayın.  
  
     Hata ayıklayıcı, veya kesme modunda çalışıyor olmalıdır.  
  
### <a name="to-turn-optional-information-on-or-off"></a>İsteğe bağlı bilgileri açmak veya kapatmak için  
  
- **Ayrıştırma** penceresini sağ tıklatın ve kısayol menüsünde istenen seçenekleri ayarlayın veya temizleyin.  
  
     Sol kenar boşluğunda sarı bir ok, geçerli yürütme noktasının konumunu işaret ediyor. Yerel kod için, bu, CPU 'nun program sayacına karşılık gelir. Bu konum, programınızda yürütülecek sonraki yönergeyi gösterir.  
  
     Daha fazla bilgi için bkz. [bellekte sayfalama veya](../debugger/how-to-page-up-or-down-in-memory.md)küçültme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)
