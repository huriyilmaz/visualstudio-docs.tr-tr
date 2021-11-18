---
title: Team Foundation Sürüm Denetimi (tfvc)
description: TFVC ve macOS hakkında sorun giderme kılavuzu.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/18/2021
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: a477ebf36d3ddb9463de60cbec603d0e39631a12
ms.sourcegitcommit: a98fa8a8362525f67824ce52b7e71757f10f1362
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2021
ms.locfileid: "132736454"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Mac için Visual Studio, Team Foundation Sürüm Denetimi’ni destekler mi?

> [!CAUTION]
> Mac için Visual Studio için preview tfvc uzantısı artık Mac için Visual Studio 2019 ' de desteklenmemektedir.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Mac için Visual Studio alternatif sürüm denetimi seçenekleri

macos üzerinde en iyi sürüm denetimi deneyimi için Team Foundation Sürüm Denetimi (tfvc) yerine **Git** kullanmanız önerilir. 

Git Mac için Visual Studio desteklenir ve Team Foundation Server (TFS)/Azure DevOps barındırılan depolar için varsayılan seçenektir. git 'i TFS/Azure DevOps kullanma hakkında daha fazla bilgi için bkz. [git deposu ayarlama](./set-up-git-repository.md) kılavuzu.

## <a name="unsupported-workarounds-for-tfvc"></a>TFVC için desteklenmeyen geçici çözümler

Mac için Visual Studio resmi olarak tfvc 'yi desteklemediğinden, bu kılavuzun geri kalanı macos 'ta tfvc ile çalışmak için bazı geçici çözümler sunar. Sürüm denetimi için TFVC 'yi bugün kullanıyorsanız, TFVC 'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler aşağıda verilmiştir:

* 1. Seçenek [grafik kullanıcı arabirimi için Visual Studio Code ve Azure Repos uzantısını kullanın](#use-visual-studio-code-and-the-azure-repos-extension)
* 2. Seçenek [Team Explorer Everywhere komut satırı istemcisini (t-CLC) kullanarak depoya Bağlan](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>1. Seçenek <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code ve Azure Repos uzantısını kullanın

sürüm denetimindeki dosyalarınızı yönetmek için bir grafik arabirimle çalışmak isterseniz, Visual Studio Code için Azure Repos uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. başlamak için [Visual Studio Code](https://code.visualstudio.com) indirin ve [Azure Repos uzantısının nasıl yapılandırılacağını](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)öğrenin.

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>2. Seçenek <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere komut satırı istemcisini kullanarak bağlanma

> [!IMPORTANT]
> Team Explorer Everywhere README uyarınca bu proje [artık korunmaz](https://github.com/microsoft/team-explorer-everywhere).

macos terminalini rahat kullanıyorsanız, Team Explorer Everywhere komut satırı istemcisi (t-CLC), tfvc 'de kaynağınıza bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantısını kurmak ve değişiklikleri kaydetmek için aşağıdaki adımları izleyebilirsiniz.

#### <a name="setting-up-the-tee-clc"></a>T-CLC ayarlanıyor

T-CLC ile kurulum almanın iki yolu vardır.

* istemciyi yüklemek için Homebrew kullanın veya
* İstemciyi indirip el ile yükleme

En kolay çözüm, macOS için bir paket yöneticisi olan **HomeBrew**' ı kullanmaktır. Bu yöntemi kullanarak yüklemek için:

1. MacOS Terminal uygulamasını başlatın.
1. Terminal ve [Homebrew giriş sayfasındaki](https://brew.sh/)yönergeleri kullanarak Homebrew 'yi yükler.
1. Homebrew yüklendikten sonra terminalinizden aşağıdaki komutu çalıştırın:`brew install tee-clc`

**T-CLC ' i el ile ayarlamak** için:

1. Team Explorer Everywhere GitHub deposunun yayınlar sayfasından [t-clc ' un en son sürümünü indirin](https://github.com/Microsoft/team-explorer-everywhere/releases) (örn. bu yazma sırasında tee-clc-14.134.0.zip).
1. .zip içeriğini diskteki bir klasöre ayıklayın.
1. MacOS Terminal uygulamasını açın ve `cd` önceki adımda kullandığınız klasöre geçmek için komutunu kullanın.
1. Klasörü içinden `./tf` komut satırı istemcisinin çalıştıracağınızı sınamak için komutunu çalıştırın, Java veya başka bağımlılıklar yüklemek isteyip istemediğiniz sorulur.

T-CLC yüklendikten sonra, `tf eula` istemcinin lisans sözleşmesini görüntülemek ve kabul etmek için komutunu çalıştırabilirsiniz.

son olarak, TFS/Azure DevOps ortamınızda kimlik doğrulamak için sunucuda bir kişisel erişim belirteci oluşturmanız gerekir. [Kişisel erişim belirteçleriyle kimlik doğrulama](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true)hakkında daha fazla bilgi edinin. TFVC ile kullanmak için bir kişisel erişim belirteci oluştururken, belirteci yapılandırırken tam erişim sağladığınızdan emin olun.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Depoya bağlanmak için t-CLC kullanma

Kaynak kodunuza bağlanmak için, önce komutunu kullanarak bir çalışma alanı oluşturmanız gerekir `tf workspace` . örneğin, aşağıdaki komutlar "myorganleştirme" adlı Azure DevOps Services bir kuruluşa bağlanır: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

`TF_AUTO_SAVE_CREDENTIALS`Ortam ayarı, kimlik bilgilerinizi birden çok kez girmeniz istenmeyecek şekilde kaydetmek için kullanılır. Bir Kullanıcı adı sorulduğunda, önceki bölümde oluşturduğunuz kişisel erişim belirtecini kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızın bir yerel klasöre eşlenmesini oluşturmak için `tf workfold` komutunu kullanırsınız. Aşağıdaki örnekte "WebApp. Services" adlı bir klasör "MyRepository" TFVC projesinden eşlenir ve yerel ~/Projects/klasörüne (yani geçerli kullanıcıların giriş klasöründeki "projeler" klasörü) kopyalanmak üzere ayarlanır.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanın:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>T-CLC kullanarak değişiklikler yürütülüyor

Mac için Visual Studio dosyalarınızda değişiklikler yaptıktan sonra, düzenlemelerinizi denetlemek için terminale geri dönebilirsiniz. `tf add`Komut, iade edilecek bekleyen değişiklikler listesine dosya eklemek için kullanılır ve `tf checkin` komut sunucuda gerçek iade işlemini gerçekleştirir. `checkin`Komut, bir yorum eklemek veya ilgili bir iş öğesini ilişkilendirmek için parametreler içerir. Aşağıdaki kod parçacığında, bir klasördeki tüm dosyalar `WebApp.Services` , iade etme için yinelemeli olarak eklenir. Ardından, kod bir yorum ile iade edilir ve "42" KIMLIĞINE sahip bir iş öğesiyle ilişkilendirilir.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada bahsedilen komutlar veya diğerleri hakkında daha fazla bilgi edinmek için terminalde aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="see-also"></a>Ayrıca bkz.

- [kodunuzu Visual Studio kullanarak tfvc 'de geliştirin ve paylaşabilirsiniz (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)
