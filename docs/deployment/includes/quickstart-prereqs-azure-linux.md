---
ms.openlocfilehash: b2f9327da5e195c50bd074a468e1f9e57ece94ea
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750783"
---
## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) , tercih ettiğiniz dilde uygun iş yükleriyle yüklendi:
  * ASP.NET: **ASP.net ve Web geliştirme**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , tercih ettiğiniz dilde uygun iş yükleriyle yüklendi:
  * ASP.NET: **ASP.net ve Web geliştirme**
::: moniker-end

* Azure aboneliği. Aboneliğiniz yoksa [ücretsiz kaydolun](https://azure.microsoft.com/free/dotnet/)ve 30 gün boyunca kredi olarak $200, popüler ücretsiz hizmet için 12 ay.

* ASP.NET Core: hızlı başlangıcı Izleyin [: ilk ASP.NET Core Web uygulamanızı oluşturmak Için Visual Studio 'Yu kullanın](../../ide/quickstart-aspnet-core.md)veya aşağıdaki adımları kullanın:
  ::: moniker range=">=vs-2019"
  Visual Studio 2019 ' de başlangıç penceresinde **Yeni proje oluştur** ' u seçin. Başlangıç penceresi açık değilse **Dosya**  >  **Başlangıç penceresi**' ni seçin. Arama kutusuna **Web uygulaması** yazın, dil olarak **C#** ' ı seçin, ardından **ASP.NET Core Web uygulaması (Model-View-Controller)** öğesini seçin ve ardından **İleri**' yi seçin. Sonraki ekranda, **Myaspapp** projesini adlandırın ve ardından **İleri**' yi seçin.

  Önerilen hedef Framework 'ü (.NET Core 3,1) veya .NET 5 ' i seçin ve ardından **Oluştur**' u seçin.
  ::: moniker-end
  ::: moniker range="vs-2017"
  Visual Studio 2017 ' de **Dosya**  >  **Yeni proje**' yi seçin, **Visual C#**  >  **.NET Core**' u seçin ve **ASP.NET Core Web uygulaması**' nı seçin İstendiğinde, **Web uygulaması (Model-View-Controller)** şablonunu seçin, **kimlik doğrulaması** olmadığından emin olun ve ardından **Tamam**' ı seçin.
  ::: moniker-end

* Dağıtım adımlarını takip etmeden önce **build > Build Solution** menü komutunu kullanarak projeyi derlediğinizden emin olun.