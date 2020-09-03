---
title: Mağaza uygulamalarında hata ayıkla
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc2d05c6b6aae4b2f33d135c6859da7b17de963
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533165"
---
# <a name="debug-store-apps-in-visual-studio"></a>Visual Studio’da Store uygulamalarının hatalarını ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı, bir programın yürütülmesini denetlemenizi ve durumunu incelemenizi sağlar. Hata ayıklayıcıyı Windows Mağazası uygulamanızda hataların nedenini bulmak ve uygulamanızın nasıl çalıştığını tam olarak anlamak için kullanabilirsiniz. Hata ayıklayıcıda yürütmeyi askıya aldığınızda, Visual Studio yürütülen kodu içeren kaynak dosyayı görüntüler ve yürütülen deyimin vurgular. Değişkenlerin değerlerine, işlev yürütme çağrı yığınına ve program durumlarınızın diğer yönlerini görebilirsiniz. Deyimlerin programın değerlerini nasıl değiştirmediğini görmek için tek seferde program bir deyimi yürütmeye devam edebilirsiniz (adım adım). JavaScript ile yazılan uygulamalarda, sayfanın DOM 'sini inceleyebilir ve düzenleyebilirsiniz.

## <a name="in-this-section"></a>Bu bölümde

|Başlık|Açıklama|
|-|-|
|[Hata ayıklama oturumu başlatma (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|Bir hata ayıklama oturumu başlatma bir JavaScript uygulaması için hata ayıklama oturumu yapılandırmak ve başlatmak üzere farklı seçenekleri açıklar.|
|[Hata ayıklama oturumunda yürütmeyi denetleme (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|Hata ayıklayıcı gezinmesi, hata ayıklamanın nasıl başlatılacağını ve durdurulacağını, kod içinde nasıl gezindiğini ve program durumunun nasıl görüntüleneceğini gösteren basit bir uygulama için sizi yönlendirir.|
|[Hızlı başlangıç: HTML ve CSS hatalarını ayıklama](../debugger/quickstart-debug-html-and-css.md)|HTML ve CSS hata ayıklaması, HTML ve CSS 'yi görüntülemek ve değiştirmek için Live DOM İnceleme araçlarını kullanarak bir JavaScript uygulamasının nasıl etkileşimli olarak ayıklanarak nasıl yapılacağını gösterir.|
|[Hızlı Başlangıç: JavaScript hata ayıklama](../debugger/quickstart-debug-javascript-using-the-console.md)|Konsolunda hata ayıklama JavaScript, JavaScript [konsol komutları](../debugger/javascript-console-commands.md)kullanılarak bir JavaScript uygulamasının nasıl etkileşimli olarak ayıklanalınacağını gösterir.|
|[Hata ayıklama oturumu başlatma (VB, C#, C++ ve XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|Bir hata ayıklama oturumu başlatma (Visual C++, Visual c# ve Visual Basic) Visual C++, Visual c# veya Visual Basic ile yazılmış bir uygulama için hata ayıklama oturumu yapılandırmak ve başlatmak üzere farklı seçenekleri açıklar.|
|[Bir hata ayıklama oturumunda gezinme (Xaml ve C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|Hata ayıklayıcı gezinmesi, hata ayıklamayı başlatma ve durdurma, kod üzerinde gezinme ve program durumunu görüntüleme ve değiştirme işlemlerinin nasıl yapılacağını gösteren basit bir uygulamadır.|
|[Windows Mağazası için askıya alma, sürdürme ve arka plan olaylarını tetikleme)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|Hata ayıklayıcı, uygulamaları askıya alan, sürdürecek ve sonlandıran Windows Işlem ömür yönetimi (PLM) olaylarını devre dışı bırakır. Bu olayları hata ayıklayıcı araç çubuğundan tetikleyebilirsiniz.<br /><br /> Arka plan görevleri, uygulama askıya alındığında bile önemli işlemler gerçekleştirmenize olanak tanır. Hata ayıklayıcı, bu arka plan görevinin başlamasını ve hatalarını ayıklamanızı mümkün.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'da hata ayıklama (MSDN Kitaplığı 'nda)](https://msdn.microsoft.com/library/sc65sadd(VS.110).aspx)
