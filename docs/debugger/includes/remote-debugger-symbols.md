---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 5033580f253a5eb42cbc64656e8c4661a2e246c1
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72912860"
---
Visual Studio bilgisayarında oluşturduğunuz simgelerle kodunuzda hata ayıklaması yapabiliyor olmanız gerekir. Yerel sembolleri kullandığınızda uzaktan hata ayıklayıcının performansı çok daha iyidir.  Uzak sembolleri kullanmanız gerekiyorsa, uzak makinede sembolleri aramak için uzaktan hata ayıklama izleyicisine söylemeniz gerekir.  

Visual Studio 2013 güncelleştirme 2 ' den başlayarak, yönetilen kod için uzak sembolleri kullanmak üzere aşağıdaki msvsmon komut satırı anahtarını kullanabilirsiniz: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Daha fazla bilgi için lütfen uzaktan hata ayıklama yardımına bakın (uzaktan hata ayıklayıcı penceresinde **F1** 'e basın veya **Yardım > kullanımı**' na tıklayın). [Visual Studio 2012 ve 2013 ' de daha fazla bilgi için .NET uzak sembol yükleme değişikliklerini](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/) bulabilirsiniz
