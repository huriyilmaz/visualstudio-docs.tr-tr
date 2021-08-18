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
ms.openlocfilehash: c1f51f1b5540eb3272998583a4ff7d86ce9c8e3d907f0ecabb73eff884575a84
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "122058301"
---
Kodun hata ayıklaması, kod bilgisayarda oluşturulan sembollerle Visual Studio gerekir. Yerel semboller kullanıyorken uzak hata ayıklayıcının performansı çok daha iyidir.  Uzak semboller kullanmak zorundaysanız, uzaktan hata ayıklama izleyiciye uzak makinede sembollere bakmasını söylemeniz gerekir.  

Güncelleştirme 2 Visual Studio 2013 den başlayarak, yönetilen kod için uzak sembolleri kullanmak üzere aşağıdaki msvsmon komut satırı anahtarını kullanabilirsiniz:`Msvsmon /FallbackLoadRemoteManagedPdbs`  

Daha fazla bilgi için lütfen uzaktan hata ayıklama yardımı 'ne bakın (uzaktan hata ayıklayıcı penceresinde **F1** tuşuna basın veya Kullanım için **Yardım'> tıklayın).** [2012 ve 2013'te .NET Uzak Sembol Yükleme Visual Studio daha fazla bilgi bulabilirsiniz](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
