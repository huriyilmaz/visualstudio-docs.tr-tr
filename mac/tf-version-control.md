---
title: Team Foundation Sürüm Denetimi (TFVC)
description: TFVC ve macOS hakkında sorun giderme kılavuzu.
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 11/18/2021
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.topic: troubleshooting
ms.openlocfilehash: 68c72b4d564abab6f42fa0e49fc56d6a5c9861d2
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135806618"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Mac için Visual Studio, Team Foundation Sürüm Denetimi’ni destekler mi?

> [!CAUTION]
> Mac için Visual Studio için önizleme TFVC uzantısı, Mac için Visual Studio 2019'da artık desteklenmiyor.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Mac için Visual Studio'daki Alternatif Sürüm Denetimi seçenekleri

macOS'ta en iyi sürüm denetimi deneyimi için, Team Foundation Sürüm Denetimi (TFVC) yerine **Git'in** kullanılması önerilir. 

Git, Mac için Visual Studio (TFS)/Team Foundation Server'de barındırılan depolar için varsayılan Azure DevOps. Git'i TFS/Azure DevOps kullanma hakkında daha fazla bilgi edinmek [için Git Deposu ayarlama kılavuzuna](./set-up-git-repository.md) bakın.

## <a name="unsupported-workarounds-for-tfvc"></a>TFVC için desteklenmeyen geçici çözümler

Bu Mac için Visual Studio resmi olarak TFVC'yi desteklemese de, bu kılavuzun geri kalanında macOS üzerinde TFVC ile çalışmaya yönelik bazı geçici çözümler sağlanır. Bugün sürüm denetimi için TFVC kullanıyorsanız, TFVC'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler:

* 1. Seçenek [Grafik Visual Studio Code için Azure Repos uzantısını ve uzantıyı kullanma](#use-visual-studio-code-and-the-azure-repos-extension)
* 2. Seçenek [Bağlan Komut Satırı İstemcisi'Team Explorer Everywhere (TEE-CLC) kullanarak merkezinize bağlantı](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>1. Seçenek <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Code uzantısını Azure Repos kullanma

Dosyalarınızı sürüm denetiminde yönetmek için bir grafik arabirimle çalışmak için, Azure Repos için Visual Studio Code uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. Çalışmaya başlamanız için [Visual Studio Code](https://code.visualstudio.com) indirin ve sonra [uzantıyı yapılandırmayı Azure Repos öğrenin.](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>2. Seçenek <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Team Explorer Everywhere Komut Satırı İstemcisini kullanarak bağlanma

> [!IMPORTANT]
> ReadME Team Explorer Everywhere olarak, bu [proje artık bakımında değil.](https://github.com/microsoft/team-explorer-everywhere)

macOS Terminali'ni kullanamıyorsanız, Team Explorer Everywhere Komut Satırı İstemcisi (TEE-CLC) TFVC'de kaynağınıza bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantınızı ayarlamak ve değişiklikleri işlemek için aşağıdaki adımları takip edebilirsiniz.

#### <a name="setting-up-the-tee-clc"></a>TEE-CLC'i ayarlama

TEE-CLC ile kurulum yapmak için iki yol vardır.

* İstemciyi Homebrew için Homebrew kullanın veya
* İstemciyi indirme ve el ile yükleme

En kolay çözüm, macOS için paket yöneticisi olan **HomeBrew'u** kullanmaktır. Bu yöntemi kullanarak yüklemek için:

1. macOS Terminal uygulamasını başlatma.
1. Terminali Homebrew sayfasındaki yönergeleri kullanarak Homebrew [yükleyin.](https://brew.sh/)
1. Yükleme Homebrew terminalden aşağıdaki komutu çalıştırın:`brew install tee-clc`

**TEE-CLC'nin el ile kurulumunu yapmak için:**

1. Team Explorer Everywhere GitHub(örneğin, bu yazma zamanında tee-clc-14.134.0.zip) Team Explorer Everywhere GitHub [yayın sayfasından tee-clc'nin](https://github.com/Microsoft/team-explorer-everywhere/releases) en son sürümünü indirin.
1. Dosyanın içeriğini .zip diskte bir klasöre ayıklar.
1. macOS Terminal uygulamasını açın ve komutunu `cd` kullanarak önceki adımda kullanılan klasöre geçin.
1. Klasöründen komutunu çalıştırarak komut satırı istemcisinin çalıştırılana kadar Java veya diğer `./tf` bağımlılıkları yüklemeniz isteniyor olabilir.

TEE-CLC yüklendikten sonra, istemci için lisans sözleşmesini görüntülemek ve kabul `tf eula` etmek için komutunu çalıştırabilirsiniz.

Son olarak, TFS/Azure DevOps ortamınız ile kimlik doğrulaması yapmak için sunucuda bir kişisel erişim belirteci oluşturmanız gerekir. Kişisel erişim [belirteçleriyle kimlik doğrulama hakkında daha fazla bilgi alın.](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops&preserve-view=true) TFVC ile kullanmak üzere kişisel erişim belirteci oluştururken, belirteci yapılandırarak Tam Erişim sağlamayı da tercih edersiniz.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>TeE-CLC kullanarak reponıza bağlanma

Kaynak kodunuzla bağlantı oluşturmak için önce komutunu kullanarak bir çalışma alanı oluşturmanız `tf workspace` gerekir. Örneğin, aşağıdaki komutlar "MyOrganization" Azure DevOps Services bir Kuruluşa bağlanabilirsiniz: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Ortam `TF_AUTO_SAVE_CREDENTIALS` ayarı kimlik bilgilerinizi kaydetmek için kullanılır, bu nedenle bunları birden çok kez girmeniz istendiğinde bu ayar kullanılır. Kullanıcı adı istendiğinde, önceki bölümde oluşturduğunuz kişisel erişim belirteci kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızı yerel bir klasöre eşlemek için komutunu `tf workfold` kullanırsınız. Aşağıdaki örnek, "MyRepository" TFVC projesinden "WebApp.Services" adlı bir klasörü eşler ve yerel ~/Projects/ klasörüne kopyalanır (geçerli kullanıcıların giriş klasöründeki "Projeler" klasörü) olarak ayarlanır.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanırsınız:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>TEE-CLC kullanarak değişiklikleri işleme

Mac için Visual Studio dosyalarında değişiklik Mac için Visual Studio değişikliklerinizi kontrol etmek için Terminal'e geri dönebilirsiniz. komutu, iade etmek üzere bekleyen değişiklikler listesine dosya eklemek için kullanılır ve komut, sunucuya gerçek `tf add` `tf checkin` iade işlemini gerçekleştirir. Komut, `checkin` açıklama eklemek veya ilgili iş öğesini ilişkilendirmek için parametreler içerir. Aşağıdaki kod parçacığında, bir klasördeki tüm dosyalar iadeye tekrar `WebApp.Services` tekrar eklenir. Ardından kod bir açıklamayla iade edilir ve "42" kimliğine sahip bir iş öğesiyle ilişkilendirilir.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada veya başka komutlarda bahsedilen komutlar hakkında daha fazla bilgi edinmek için Terminal'den aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kullanarak TFVC'de kodunuzu geliştirin ve paylaşın (Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)
