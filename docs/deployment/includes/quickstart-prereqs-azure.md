---
ms.openlocfilehash: 3ffab1767817189c8bf27c699713354979425d21
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750621"
---
## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) , tercih ettiğiniz dilde uygun iş yükleriyle yüklendi:
  * ASP.NET: **ASP.net ve Web geliştirme**
  * Node.js: **Node.js geliştirme**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , tercih ettiğiniz dilde uygun iş yükleriyle yüklendi:
  * ASP.NET: **ASP.net ve Web geliştirme**
  * Node.js: **Node.js geliştirme**
::: moniker-end

* Azure aboneliği. Aboneliğiniz yoksa [ücretsiz kaydolun](https://azure.microsoft.com/free/dotnet/)ve 30 gün boyunca kredi olarak $200, popüler ücretsiz hizmet için 12 ay.

* Bir ASP.NET, ASP.NET Core, .NET Core veya Node.js projesi. Zaten bir projeniz yoksa aşağıdan bir seçenek belirleyin:
  * ASP.NET Core: hızlı başlangıcı Izleyin [: ilk ASP.NET Core Web uygulamanızı oluşturmak Için Visual Studio 'Yu kullanın](../../ide/quickstart-aspnet-core.md)veya aşağıdaki adımları kullanın:
    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de başlangıç penceresinde **Yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. Arama kutusuna **Web uygulaması** yazın, dil olarak **C#** ' ı seçin, ardından **ASP.NET Core Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **İleri**' yi seçin. Sonraki ekranda, **Myaspapp** projesini adlandırın ve ardından **İleri**' yi seçin.

    Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' de **Dosya**  >  **Yeni proje**' yi seçin, **Visual C#**  >  **.NET Core**' u seçin ve **ASP.NET Core Web uygulaması**' nı seçin İstendiğinde, **Web uygulaması (Model-View-Controller)** şablonunu seçin, **kimlik doğrulaması** olmadığından emin olun ve ardından **Tamam**' ı seçin.
    ::: moniker-end
  * Node.js: [hızlı başlangıç izleyin: Visual Studio 'yu kullanarak ilk Node.js uygulamanızı oluşturun](../../ide/quickstart-nodejs.md)veya **Dosya**  >  **Yeni proje**' yi kullanın, **JavaScript**' i seçin, sonra **boş Node.js web uygulaması**' nı seçin.

* Dağıtım adımlarını takip etmeden önce **build > Build Solution** menü komutunu kullanarak projeyi derlediğinizden emin olun.