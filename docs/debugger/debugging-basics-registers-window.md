---
title: Yazmazlar penceresi hakkında | Microsoft Docs
description: Visual Studio'daki Yazmazlar penceresi hakkında bilgi edinebilirsiniz. Bu pencere yalnızca Seçenekler iletişim kutusundaki Hata ayıklama düğümünde adres düzeyinde hata ayıklama etkinleştirildiğinde kullanılabilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0ae8733c30a299123e1f0d21a43be943a24a5277
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097594"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Visual Studio'daki Yazmaçlar Penceresi hakkında (C#, C++, Visual Basic, F#)

**Yazmazlar** penceresi yalnızca Seçenekler iletişim kutusundaki Hata ayıklama düğümünde adres düzeyinde **hata** ayıklama **etkinleştirildiyse** kullanılabilir.

 Yazmacalar, işlemcinin etkin olarak üzerinde çalıştığı küçük veri parçalarını depolamak için kullanılan bir işlemci (CPU) içindeki özel konumlardır. Kaynak kodu derlemek veya yorumlamak, gerektiğinde verileri bellekten yazmamalara ve yeniden geri taşımaya yönelik yönergeler üretir. Yazmaçlarda verilere erişmek bellekte verilere erişmekle karşılaştırıldığında çok hızlıdır, bu nedenle işlemcinin verileri bir yazmaçta tutmasını ve tekrar tekrar erişmesini sağlayan kod, işlemcinin yazmaçları sürekli yüklemesini ve kaldırmasını gerektiren koddan daha hızlı yürütme eğilimindedir. Derleyicinin verileri yazmacın içinde tutması ve başka iyileştirmeler gerçekleştirmesi için genel değişkenleri kullanmaktan kaçınmanız ve mümkün olduğunca yerel değişkenlere güvenmeniz gerekir. Bu şekilde yazılmış olan kodun iyi bir başvuru yerelliği olduğu ifade edildi. C/C++ gibi bazı dillerde programcı bir yazmaç değişkeni bildirene kadar derleyiciye değişkeni her zaman yazmaçta tutması için en iyi denemeyi söyler. Daha fazla bilgi için bkz. [Register Anahtar Sözcüğü.](/previous-versions/482s4fy9(v=vs.140))

 Yazmacalar iki türe ayrıl olabilir: genel amaçlı ve özel amaçlı. Genel amaçlı yazmacalar, iki sayı ekleme veya dizideki bir öğeye başvuru gibi genel işlemler için verileri tutar. Özel amaçlı yazmazların belirli amaçları ve özel anlamı vardır. İyi bir örnek, işlemcinin programın çağrı yığınını izlemek için kullandığı yığın işaretçisi yazmaçtır. Programcı olarak yığın işaretçisini doğrudan işlemeyebilirsiniz. Ancak, yığın işaretçisi olmadan işlemci bir işlev çağrısının sonunda nereye geri dönerek geri dönerek geri dönebilirsiniz çünkü program düzgün çalışması için önemlidir.

 Genel amaçlı yazmacaların çoğu yalnızca tek bir veri öğesi tutar. Örneğin, tek bir tamsayı, kayan nokta sayısı veya bir dizinin öğesi. Bazı yeni işlemciler, küçük bir veri dizisini tutan vektör yazmazları olarak adlandırılan daha büyük yazmamalara sahip olur. Çok fazla veriye sahip olduğundan, vektör kayıtları dizileri içeren işlemlerin çok hızlı bir şekilde gerçekleştir gerçekleştirilen işlemlere izin verir. Vektör yazmazları ilk olarak pahalı, yüksek performanslı süper bilgisayarlarda kullanılıyor ancak artık yoğun grafik operasyonlarında büyük avantaj elde etmek için kullanıldıkları mikro işlemcilerde kullanılmaya başlandı.

 Bir işlemci genellikle biri kayan nokta işlemleri için, diğeri de tamsayı işlemleri için iyileştirilmiş iki genel amaçlı yazmaca sahip olur. Şaşırtıcı bir şekilde, bunlar kayan nokta ve tamsayı yazmaca denir.

 Yönetilen kod, çalışma zamanında mikro işlemcinin fiziksel kayıtlarına erişen yerel koda derlenmiş. **Yazmazlar penceresinde** ortak dil çalışma zamanı veya yerel kod için bu fiziksel yazmazlar görüntülenir. **Yazmazlar** penceresi, betik ve SQL kayıt kavramını desteklemeen diller SQL betik veya uygulama için kayıt bilgilerini görüntülemez.

 Yazmanlar penceresini görüntüleme **hakkında daha fazla bilgi** için [bkz. Yazmanlar Penceresini Kullanma.](../debugger/how-to-use-the-registers-window.md)

 Yazmanlar **penceresine** bakarak gibi girişler `EAX = 003110D8` görebilirsiniz.

 Bu durumda, `=` işaretin sol tarafta yer alan simgesi yazman `EAX` adıdır. İşaretin sağı, `=` yazmaz içeriğini temsil eder.

 **Yazmazlar** penceresi, bir yazmanın içeriğini görüntülemekten daha fazlasını yapmaya olanak sağlar. Yerel kodda kesme modundayken yazmaca tıklar ve değeri düzenleyebilirsiniz. Bu, rastgele bir şekilde yapmak için bir şey değildir. Düzenlemekte olduğunuz yazmaca ve içerdiği verileri anlamadıkça, dikkatsiz düzenlemenin sonucu büyük olasılıkla bir program kilitlenmesi veya başka bir istirnak sonucudur. Ne yazık ki, çeşitli Intel ve Intel uyumlu işlemcilerin kayıt kümelerinin ayrıntılı bir açıklaması, bu kısa tanıtım kapsamının çok ötesindedir.

## <a name="register-groups"></a>Grupları kaydetme

Dağınıklığı azaltmak için **Yazmalar penceresi** kayıtları gruplar halinde düzenleyebilir. Yazmanlar penceresine **sağ** tıklarsanız, grup listesini içeren bir kısayol menüsüyle karşınıza çıktıyı gördüğünüz şekilde ekleyebilirsiniz.

## <a name="register-flags"></a>Bayrakları kaydetme

Intel x86 işlemcileri için Yazmalar penceresinde aşağıdaki **bayrakları** görebilirsiniz. Hata ayıklama oturumu sırasında bu bayrakları da düzenleyebilirsiniz.

|Bayrak|Değer ayarlama|
|-|-|
|Taşma|OV = 1|
|Yön|UP = 1|
|Kesme|EI = 1|
|İşaret|PL = 1|
|Sıfır|ZR = 1|
|Yardımcı taşıma|AC = 1|
|Parity|PE = 1|
|Sonraki basamağa geçirme|CY = 1|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Yazmaçlar Penceresini Kullanma](../debugger/how-to-use-the-registers-window.md)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)