---
title: Takım Temel Sürüm Kontrolü (TFVC)
description: TFVC ve macOS hakkında bir sorun giderme kılavuzu.
author: jmatthiesen
ms.author: jomatthi
ms.date: 09/02/2019
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: e56aec03aabe818731c65acb30eafcc18f170ac3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714518"
---
# <a name="does-visual-studio-for-mac-support-team-foundation-version-control"></a>Mac için Visual Studio, Team Foundation Sürüm Denetimi’ni destekler mi?

> [!CAUTION]
> Mac için Visual Studio için önizleme TFVC uzantısı artık Visual Studio 2019'da Mac için desteklenmez.


## <a name="alternative-version-control-options-in-visual-studio-for-mac"></a>Mac için Visual Studio'da Alternatif Sürüm Kontrolü seçenekleri

macOS'taki en iyi sürüm kontrol deneyimi için, Team Foundation Version Control (TFVC) yerine **Git'i** kullanmanızı öneririz. 

Git, Mac için Visual Studio'da desteklenir ve Team Foundation Server (TFS)/Azure DevOps'te barındırılan depolar için varsayılan seçenektir. TFS/Azure DevOps ile Git'i kullanma hakkında daha fazla bilgi edinmek için [Git Deposu Oluşturma](/visualstudio/mac/set-up-git-repository) kılavuzuna bakın.

## <a name="unsupported-workarounds-for-tfvc"></a>TFVC için desteklenmeyen geçici geçici işler

Mac için Visual Studio resmi olarak TFVC'yi desteklemese de, bu kılavuzun geri kalanı macOS'ta TFVC ile çalışmak için bazı geçici çözüm sağlar. Bugün sürüm kontrolü için TFVC kullanıyorsanız, TFVC'de barındırılan kaynak kodunuza erişmek için kullanabileceğiniz bazı çözümler şunlardır:

* 1. Seçenek [Grafiksel bir bilgi edinin için Visual Studio Code ve Azure Depoları uzantısını kullanma](#use-visual-studio-code-and-the-azure-repos-extension)
* 2. Seçenek [Team Explorer Everywhere Komut Satırı İstemcisini (TEE-CLC) kullanarak repo'nuza bağlanın](#connecting-using-the-team-explorer-everywhere-command-line-client)

### <a name="option-1--use-visual-studio-code-and-the-azure-repos-extension"></a>1. Seçenek <a id="use-visual-studio-code-and-the-azure-repos-extension"></a>Visual Studio Kodu ve Azure Depoları uzantısını kullanma

Dosyalarınızı sürüm denetiminde yönetmek için grafik arabirimiyle çalışmak isterseniz, Visual Studio Code için Azure Repos uzantısı Microsoft tarafından desteklenen bir çözüm sağlar. Başlamak için [Visual Studio Code'u](https://code.visualstudio.com) indirin ve azure depo uzantısını nasıl [yapılandırıştırılacaöğrenin.](https://marketplace.visualstudio.com/items?itemName=ms-vsts.team)

### <a name="option-2--connecting-using-the-team-explorer-everywhere-command-line-client"></a>2. Seçenek <a id="connecting-using-the-team-explorer-everywhere-command-line-client"></a>Her Yerde Takım Gezgini Komut Satırı İstemcisini kullanarak bağlanma

> [!IMPORTANT]
> Team Explorer Everywhere README'a göre, bu proje [artık sürdürülmemektedir.](https://github.com/microsoft/team-explorer-everywhere)

macOS Terminali'ni kullanmaktan memnunsanız, Team Explorer Everywhere Komut Satırı İstemi (TEE-CLC) Kaynağınıza TFVC'de bağlanmak için desteklenen bir yol sağlar.

TFVC bağlantınızı kurmak ve değişiklikler gerçekleştirmek için aşağıdaki adımları izleyebilirsiniz.

#### <a name="setting-up-the-tee-clc"></a>TEE-CLC'nin kurulumu

TEE-CLC ile kurulum almanın iki yolu vardır.

* İstemciyi yüklemek için Homebrew'i kullanma veya
* İstemciyi indirin ve el ile kurun

En kolay çözüm **HomeBrew kullanıyor**, macOS için bir paket yöneticisi. Bu yöntemi kullanarak yüklemek için:

1. macOS Terminaluygulamasını başlatın.
1. Homebrew'i Terminal'i ve [Homebrew ana sayfasındaki](https://brew.sh/)talimatları kullanarak yükleyin.
1. Homebrew yüklendikten sonra Terminalinizden aşağıdaki komutu çalıştırın:`brew install tee-clc`

**TEE-CLC'yi el ile kurmak**için:

1. Team Explorer Everywhere GitHub repo'nun sürümler sayfasından [tee-clc'nin en son sürümünü indirin](https://github.com/Microsoft/team-explorer-everywhere/releases) (örn. bu yazı nın yazıldığı sırada tee-clc-14.134.0.zip).
1. .zip'in içeriğini diskteki bir klasöre ayıklayın.
1. macOS Terminali uygulamasını açın `cd` ve önceki adımda kullandığınız klasöre geçmek için komutu kullanın.
1. Klasörün içinden, komut `./tf` satırı istemcisinin çalıştırabileceğini test etmek için komutu çalıştırın, Java veya diğer bağımlılıkları yüklemeniz istenebilir.

TEE-CLC yüklendikten sonra, istemcinin lisans `tf eula` sözleşmesini görüntülemek ve kabul etmek için komutu çalıştırabilirsiniz.

Son olarak, TFS/Azure DevOps ortamınızla kimlik doğrulaması yapmak için sunucuda kişisel erişim belirteci oluşturmanız gerekir. [Kişisel erişim belirteçleri ile kimlik doğrulama](/azure/devops/integrate/get-started/authentication/pats?view=azure-devops)hakkında daha fazla bilgi edinin. TFVC ile kullanılacak kişisel erişim jetonu oluştururken, belirteci yapılandırırken Tam Erişim sağladığından emin olun.

#### <a name="using-the-tee-clc-to-connect-to-your-repo"></a>Repo'nuza bağlanmak için TEE-CLC'yi kullanma

Kaynak kodunuza bağlanmak için öncelikle komutu `tf workspace` kullanarak bir çalışma alanı oluşturmanız gerekir. Örneğin, aşağıdaki komutlar Azure DevOps Hizmetleri'ndeki "MyOrganization" adlı bir Kuruluşa bağlanır: 

```bash
export TF_AUTO_SAVE_CREDENTIALS=1
tf workspace -new MyWorkspace -collection:https://dev.azure.com/MyOrganization
```

Ortam `TF_AUTO_SAVE_CREDENTIALS` ayarı, kimlik bilgilerinizi kaydetmek için kullanılır, böylece birden çok kez girmeniz istenmez. Bir kullanıcı adı istendiğinde, önceki bölümde oluşturduğunuz kişisel erişim belirteci kullanın ve boş bir parola kullanın.

Kaynak dosyalarınızın yerel bir klasöre eşleneği oluşturmak `tf workfold` için komutu kullanırsınız. Aşağıdaki örnek, "MyRepository" TFVC projesinden "WebApp.Services" adlı bir klasörün haritasını çıkarır ve yerel ~/Projects/klasörüne (örneğin geçerli kullanıcıların ev klasöründe bir "Projeler" klasörüne) kopyalanacak şekilde ayarlar.

```bash
tf workfold -map $/MyRepository/WebApp.Services -workspace:MyWorkspace ~/Projects/
```

Son olarak, kaynak dosyaları sunucudan almak ve yerel olarak kopyalamak için aşağıdaki komutu kullanırsınız:

```bash
tf get
```

#### <a name="committing-changes-using-the-tee-clc"></a>TEE-CLC kullanarak değişiklik yapmak

Mac için Visual Studio'da dosyalarınızda değişiklik yaptıktan sonra, denetimlerinizi iade etmek için Terminal'e geri dönebilirsiniz. Komut, `tf add` iade edilecek bekleyen değişiklikler listesine dosya eklemek için kullanılır `tf checkin` ve komut sunucuya gerçek iadeyi gerçekleştirir. Komut, `checkin` yorum eklemek veya ilgili bir iş öğesini ilişkilendirmek için parametreleri içerir. Aşağıdaki kod snippet'inde, `WebApp.Services` bir klasördeki tüm dosyalar iadeye özyinelemeli olarak eklenir. Daha sonra, kod bir açıklama ile iade edilir ve kimliği "42" olan bir iş öğesi ile ilişkili.

```bash
cd WebApp.Services
tf add * /recursive
tf checkin -comment:"Replaced 'Northwand' typos with the correct word Northwind" -associate:42
```

Burada belirtilen komutlar veya diğerleri hakkında daha fazla bilgi edinmek için Terminal'den aşağıdaki komutu kullanabilirsiniz:

`tf help`

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'yı kullanarak kodunuzu TFVC'de geliştirin ve paylaşın (Windows'da)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)