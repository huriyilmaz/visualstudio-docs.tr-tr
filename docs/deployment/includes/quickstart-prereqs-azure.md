---
ms.openlocfilehash: b329eb1fc9bffd84fcb9a595b401ee0e0bcfd41f
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129638671"
---
## <a name="prerequisites"></a>Önkoşullar

::: moniker range=">=vs-2019"

* [Visual Studio 2019'un,](https://visualstudio.microsoft.com/downloads) tercih diliniz için uygun iş yükleri ile yüklü olması gerekir:
  * ASP.NET: ASP.NET **ve web geliştirme**
  * Node.js:Node.js **geliştirme**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017'ye,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) tercih diliniz için uygun iş yükleriyle birlikte yüklenmiştir:
  * ASP.NET: ASP.NET **ve web geliştirme**
  * Node.js:Node.js **geliştirme**
::: moniker-end

* Azure aboneliği. Aboneliğiniz yoksa, 30 gün boyunca 200 ABD doları kredi ve popüler ücretsiz hizmetlerden 12 ay boyunca ücretsiz olarak kaydolabilirsiniz. [](https://azure.microsoft.com/free/dotnet/)

* ASP.NET, ASP.NET Core, .NET Core veya Node.js projesi. Henüz bir projeniz yoksa aşağıdaki seçeneği belirleyin:
  * ASP.NET Core: [Hızlı Başlangıç: Visual Studio web](../../ide/quickstart-aspnet-core.md)ASP.NET Core oluşturmak için kullanın veya aşağıdaki adımları kullanın:
    ::: moniker range=">=vs-2019"
    2019 Visual Studio da başlangıç **penceresinde Yeni proje oluştur'a** tıklayın. Başlangıç penceresi açık değilse Dosya Başlangıç **Penceresi'ne**  >  **tıklayın.** Arama **kutusuna web uygulaması** yazın, dil olarak **C#** dilini seçin, ASP.NET Core Web Uygulaması **(Model-View-Controller)** seçin ve ardından Sonraki'yi **seçin.** Sonraki ekranda projeye **MyASPApp adını ve ardından** Sonraki'yi **seçin.**

    Önerilen hedef çerçeveyi veya .NET 6'yi seçin ve ardından **Oluştur'a seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    2017 Visual Studio de Dosya Yeni  >  Project'yi seçin, **Visual C#**  >  **.NET Core'ASP.NET Core** Web **Uygulaması'ASP.NET Core seçin.** İstendiğinde Web Uygulaması **(Model-View-Controller)** şablonunu seçin,  Kimlik Doğrulaması Yok seçeneğinin seçili olduğundan emin olun ve tamam'ı **seçin.**
    ::: moniker-end
  * Node.js: Hızlı [Başlangıç: İlk Visual Studio](../../ide/quickstart-nodejs.md)uygulamanızı oluşturmak için Node.js kullanın veya Dosya Yeni   >  Project'yi kullanın, **JavaScript'i** seçin ve ardından Boş Node.js **Web Uygulaması'Node.js seçin.**

* Dağıtım adımlarını uygulamadan önce Derleme Çözümü **>** komutunu kullanarak projeyi derlemeyi emin olun.