---
ms.openlocfilehash: d73d994d4bab7aaf7ab4c596e133c83d79b28c06
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129638529"
---
## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* seçtiğiniz dilde uygun iş yükleriyle birlikte [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) yüklendi:
  * ASP.NET: **ASP.NET ve web geliştirme**
::: moniker-end
::: moniker range="vs-2017"
* seçtiğiniz dilde uygun iş yükleriyle birlikte [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) yüklendi:
  * ASP.NET: **ASP.NET ve web geliştirme**
::: moniker-end

* Azure aboneliği. Aboneliğiniz yoksa [ücretsiz kaydolun](https://azure.microsoft.com/free/dotnet/)ve 30 gün boyunca kredi olarak $200, popüler ücretsiz hizmet için 12 ay.

* ASP.NET Core: [hızlı başlangıç: ilk ASP.NET Core web uygulamanızı oluşturmak için Visual Studio kullanın](../../ide/quickstart-aspnet-core.md)veya aşağıdaki adımları kullanın:
  ::: moniker range=">=vs-2019"
  Visual Studio 2019 ' de, başlangıç penceresinde **yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. arama kutusuna **web uygulaması** yazın, dil olarak **C#** ' ı seçin, ardından **ASP.NET Core web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **ileri**' yi seçin. Sonraki ekranda, **Myaspapp** projesini adlandırın ve ardından **İleri**' yi seçin.

  Önerilen hedef Framework veya .NET 6 ' ı seçin ve ardından **Oluştur**' u seçin.
  ::: moniker-end
  ::: moniker range="vs-2017"
  Visual Studio 2017 ' de **dosya**  >  **yeni Project**' i seçin, **Visual C#**  >  **.net Core**' u seçin, sonra **ASP.NET Core Web uygulaması**' nı seçin İstendiğinde, **Web uygulaması (Model-View-Controller)** şablonunu seçin, **kimlik doğrulaması** olmadığından emin olun ve ardından **Tamam**' ı seçin.
  ::: moniker-end

* Dağıtım adımlarını takip etmeden önce **build > Build Solution** menü komutunu kullanarak projeyi derlediğinizden emin olun.