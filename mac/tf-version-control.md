---
title: Team Foundation Sürüm Denetimi (TFVC)
description: TFVC ve macOS hakkında sorun giderme kılavuzu.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: e56aec03aabe818731c65acb30eafcc18f170ac3
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714518"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Mac için Visual Studio Team Foundation Sürüm Denetimi destekliyor mu?

> [!CAUTION]
> Mac için Visual Studio için Preview TFVC uzantısı artık Mac için Visual Studio 2019 ' de desteklenmemektedir.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Mac için Visual Studio alternatif sürüm denetimi seçenekleri

MacOS üzerinde en iyi sürüm denetimi deneyimi için Team Foundation Sürüm Denetimi (TFVC) yerine **Git** kullanmanız önerilir. 

Git Mac için Visual Studio desteklenir ve Team Foundation Server (TFS)/Azure DevOps içinde barındırılan depolar için varsayılan seçenektir. Git 'i TFS/Azure DevOps ile kullanma hakkında daha fazla bilgi için bkz. [Git deposu ayarlama](/visualstudio/mac/set-up-git-repository) Kılavuzu.

## <a name="unsupported-workarounds-for-tfvc"></a>TFVC için desteklenmeyen geçici çözümler

Mac için Visual Studio resmi olarak TFVC 'yi desteklemediğinden, bu kılavuzun geri kalanı macOS 'ta TFVC ile çalışmak için bazı geçici çözümler sunar. Sürüm denetimi için TFVC 'yi bugün kullanıyorsanız, TFVC 'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler aşağıda verilmiştir:

* 1\. seçenek. [Grafik Kullanıcı arabirimi için Visual Studio Code ve Azure Repos uzantısını kullanın](#use-visual-studio-code-and-the-azure-repos-extension)
* Seçenek 2. [Team Explorer Everywhere komut satırı Istemcisini (t-CLC) kullanarak depoya bağlanma](#connecting-using-the-team-explorer-everywhere-command-line-client)

### 1\. seçenek. <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code ve Azure Repos uzantısını kullanın

Sürüm denetimindeki dosyalarınızı yönetmek için bir grafik arabirimle çalışmak isterseniz, Visual Studio Code için Azure Repos uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. Başlamak için [Visual Studio Code](https://code.visualstudio.com) indirin ve [Azure Repos uzantısının nasıl yapılandırılacağını](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)öğrenin.

### Seçenek 2. <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere komut satırı Istemcisini kullanarak bağlanma

> [!IMPORTANT]
> Team Explorer Everywhere README uyarınca bu proje [artık korunmaz](https://github.com/microsoft/team-explorer-everywhere).

MacOS terminalini rahat kullanıyorsanız, Team Explorer Everywhere komut satırı Istemcisi (t-CLC), TFVC 'de kaynağınıza bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantısını kurmak ve değişiklikleri kaydetmek için aşağıdaki adımları izleyebilirsiniz.

#### <a name="setting-up-the-tee-clc"></a>T-CLC ayarlanıyor

T-CLC ile kurulum almanın iki yolu vardır.

* İstemcisini yüklemek için homebrew kullanın veya
* İstemciyi indirip el ile yükleme

En kolay çözüm, macOS için bir paket yöneticisi olan **HomeBrew**' ı kullanmaktır. Bu yöntemi kullanarak yüklemek için:

1. MacOS Terminal uygulamasını başlatın.
1. Terminal ve [homebrew giriş sayfasındaki](https://brew.sh/)yönergeleri kullanarak Homebrew 'ı yükler.
1. Homebrew yüklendikten sonra Terminalinizden şu komutu çalıştırın: `brew install tee-clc`

**T-CLC ' i el ile ayarlamak**için:

1. Team Explorer Everywhere GitHub deposunun yayınlar sayfasından [t-CLC ' nin en son sürümünü indirin](https://github.com/Microsoft/team-explorer-everywhere/releases) (örneğin, tee-CLC-14.134.0. zip bu yazma sırasında).
1. . Zip içeriğini diskteki bir klasöre ayıklayın.
1. MacOS Terminal uygulamasını açın ve önceki adımda kullandığınız klasöre geçmek için `cd` komutunu kullanın.
1. Komut satırı istemcisinin çalıştıracağınızı sınamak için klasörü içinden komut `./tf` çalıştırın, Java veya başka bağımlılıklar yüklemek isteyip istemediğiniz sorulabilir.

T-CLC yüklendikten sonra, istemcinin lisans sözleşmesini görüntülemek ve kabul etmek için `tf eula` komutunu çalıştırabilirsiniz.

Son olarak, TFS/Azure DevOps ortamınızdan kimlik doğrulamak için sunucuda bir kişisel erişim belirteci oluşturmanız gerekir. [Kişisel erişim belirteçleriyle kimlik doğrulama](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)hakkında daha fazla bilgi edinin. TFVC ile kullanmak için bir kişisel erişim belirteci oluştururken, belirteci yapılandırırken tam erişim sağladığınızdan emin olun.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Depoya bağlanmak için t-CLC kullanma

Kaynak kodunuza bağlanmak için öncelikle `tf workspace` komutunu kullanarak bir çalışma alanı oluşturmanız gerekir. Örneğin, aşağıdaki komutlar "Myorganleştirme" adlı Azure DevOps Services bir kuruluşa bağlanır: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS` ortamı ayarı, kimlik bilgilerinizi birden çok kez girmeniz istenmeyecek şekilde kaydetmek için kullanılır. Bir Kullanıcı adı sorulduğunda, önceki bölümde oluşturduğunuz kişisel erişim belirtecini kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızın bir yerel klasöre eşlenmesinin oluşturulması için `tf workfold` komutunu kullanırsınız. Aşağıdaki örnekte "WebApp. Services" adlı bir klasör "MyRepository" TFVC projesinden eşlenir ve yerel ~/Projects/klasörüne (yani geçerli kullanıcıların giriş klasöründeki "projeler" klasörü) kopyalanmak üzere ayarlanır.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanın:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>T-CLC kullanarak değişiklikler yürütülüyor

Mac için Visual Studio dosyalarınızda değişiklikler yaptıktan sonra, düzenlemelerinizi denetlemek için terminale geri dönebilirsiniz. `tf add` komutu, iade edilecek bekleyen değişiklikler listesine dosya eklemek için kullanılır ve `tf checkin` komutu sunucuda gerçek iade işlemini gerçekleştirir. `checkin` komutu, bir yorum eklemek veya ilgili bir iş öğesini ilişkilendirmek için parametreler içerir. Aşağıdaki kod parçacığında, bir `WebApp.Services` klasöründeki tüm dosyalar, iade etme için yinelemeli olarak eklenir. Ardından, kod bir yorum ile iade edilir ve "42" KIMLIĞINE sahip bir iş öğesiyle ilişkilendirilir.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada bahsedilen komutlar veya diğerleri hakkında daha fazla bilgi edinmek için terminalde aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kullanarak (Windows 'da) kodunuzu TFVC 'de geliştirme ve paylaşma](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)