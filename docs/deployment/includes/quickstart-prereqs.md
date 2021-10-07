---
ms.openlocfilehash: 4a6afc117b2457b9be9a3aeb3703695fe2e1a230
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129638245"
---
## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* seçtiğiniz dilde uygun iş yükleriyle birlikte [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) yüklendi:
  * ASP.NET: **ASP.NET ve web geliştirme**
  * Python: **Python geliştirme**
  * Node.js: **Node.js geliştirme**
::: moniker-end
::: moniker range="vs-2017"
* seçtiğiniz dilde uygun iş yükleriyle birlikte [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) yüklendi:
  * ASP.NET: **ASP.NET ve web geliştirme**
  * Python: **Python geliştirme**
  * Node.js: **Node.js geliştirme**
::: moniker-end

* ASP.NET, ASP.NET Core, Python veya Node.js projesi. Zaten bir projeniz yoksa aşağıdan bir seçenek belirleyin:
  * ASP.NET Core: [hızlı başlangıç: ilk ASP.NET Core web uygulamanızı oluşturmak için Visual Studio kullanın](../../ide/quickstart-aspnet-core.md)veya aşağıdaki adımları kullanın:
    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de, başlangıç penceresinde **yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. arama kutusuna **web uygulaması** yazın, dil olarak **C#** ' ı seçin, ardından **ASP.NET Core web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **ileri**' yi seçin. Sonraki ekranda, **Myaspapp** projesini adlandırın ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework veya .NET 6 ' ı seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **dosya**  >  **yeni Project**' i seçin, **Visual C#**  >  **.net Core**' u seçin, sonra **ASP.NET Core Web uygulaması**' nı seçin İstendiğinde, **Web uygulaması (Model-View-Controller)** şablonunu seçin, **kimlik doğrulaması** olmadığından emin olun ve ardından **Tamam**' ı seçin.
    ::: moniker-end
  * Python: [hızlı başlangıç: Visual Studio kullanarak ilk Python web uygulamanızı oluşturun](../../ide/quickstart-python.md)veya **dosya**  >  **yeni Project** kullanın, **Python**' ı seçin, sonra **flask web Project**' yı seçin.
  * Node.js: [hızlı başlangıç: ilk Node.js uygulamanızı oluşturmak için Visual Studio kullanın](../../ide/quickstart-nodejs.md), **dosya**  >  **yeni Project** kullanın, **JavaScript**'i seçip **boş Node.js Web uygulaması**' nı seçin.

* Dağıtım adımlarını takip etmeden önce **build > Build Solution** menü komutunu kullanarak projeyi derlediğinizden emin olun.